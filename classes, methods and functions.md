
# Klassen


    ## Structure of classes

    ConfigData  
        ├ Files  
        ├ Pathes  
        └ Stocks  
     
    Dictionaries
    
    Strings
        ├ TextInput
        │   └ TextEdit
        │       └ Sentences
        │           └ Words
        │               ├ Syllables
        │               │   └ Parts   
        │               └ WordsAnalyze
        ├ TextOutput
        
    Combination




## ConfigData

## Files (ConfigData)

## Pathes (ConfigData)
Geeignet zu Erfassung von Dateipfaden, auf mit denen spaeter Dateien angesteuert werden, z.B. die Woerterbuch-Dateien.

### Methoden
#### NewPathDictionary.--init-- (*self*) 
Legt ein neue Variable vom Typ Dic an, in der die Dateipfade aus der Config-Datei erfasst werden.  

##### Objekt
**NewPathDictionary**: Dictionary, in der alle Dateipfade hinterlegt werden.

##### Beschreibung
>Die Initialisierung erfolgt mit der Zuweisung von '{}'. Der erste Teil jedes neuen Eintrags umfasst immer den konkreten Pfad, der zweite Teil die Bezeichnung (nicht den Namen!) der Datei, zu der der Pfad fuehrt.  
Zurueckgegeben wird eine leere Dictionary.

#### PathDictionary.add_to (*self, ForFile, Path*)  
Fuegt einen neuen Eintrag zum bisherigen Dictionary der Dateipfade zu.

##### Objekt
**PathDictionary**: Dictionary, in das der neue Dateipfad aufgenommen werden soll.

##### Parameter  
- ***ForFile***: Bezeichnung der Datei, zu der der Pfad leitet.
- ***Path***: Dateipfad, der neu ins Dictionary aufgenommen werden soll.

##### Beschreibung
>Ans Ende der Dictionary wird neue zweiteiliger Eintrag angefuegt. Der erste Teil jedes neuen Eintrags umfasst immer den konkreten Pfad, der zweite Teil die Bezeichnung (nicht den Namen!) der Datei, zu der der Pfad fuehrt.  
Zurueckgegeben wird eine Dictionary mit dem ergaenzten Dateipfad.

## Stocks (ConfigData)  
Geeignet zur Erfassung von Buchstabengruppen, z.B. Vokale oder Konsonanten, oder Wortklassen, z.B. Artikel, in einer Menge.  
Aufbau im Modul `M_Config`.

### Methoden
#### NewStock.--init-- (***self, StockType***)  
Legt einen neue, leere Menge, String, Liste oder Dictionary an.  

##### Objekt
**NewStock**: Neuer Bestand, der angelegt werden soll.

##### Parameter
- ***StockType***: Art des neu anzulegenden Bestandes, z.B. Set (Menge), String (Zeichenkette), Dictionary (Woerterbuch) oder List (Liste). 

##### Beschreibung
>Enthaelt ***StockType*** den Wert 'String', wird ein leerer String "" angelegt; enthaelt ***StockType*** den Wert 'Set', wird eine leere Menge () angelegt; enthaelt ***StockType*** den Wert 'Dictionary', wird ein leeres Woerterbuch {} angelegt; enthaelt ***StockType*** den Wert 'List', wird eine leere Liste [] angelegt. Fallback ist ein leerer String - die Ueberpruefung auf den Uebergabewert 'String' erfolgt also am Ende der If-Abfragen mit einem einfachen else-Zweig.  
Zurueckgegeben wird ein neuer leerer Bestand.

#### Stock.add_to (***self, Component***)  
Durchsucht die Config-Datei und fuegt die passenden Buchstaben zur jeweiligen Menge zu.

##### Objekt
**Stock**: Namentlicher Bestand, in den der Buchstabe eingefuegt werden soll.

##### Parameter  
- ***Component***: Jeweiliger Buchstabe oder die Wortklasse, die eingefuegt werden soll.  

##### Beschreibung
>Mit 'type' wird zunaechst ueberprueft, zu welcher Bestandsart der entsprechende Bestand gehoert. In Abhaengigkeit von der Bestandsart wird der neue Buchstabe zum Bestand hinzugefuegt.  
Zurueckgegeben wird ein ergaenzter Bestand.

#### CheckStock.search_in (***self, CheckComponent***)  
Ueberprueft, ob der jeweilige Buchstabe in der jeweiligen Menge vorhanden ist. Liefert 'True' oder 'False' zurück.   

##### Objekt
**CheckStock**: Name des Bestandes, der ueberprueft werden soll.

##### Parameter  
- ***CheckComponent***: Buchstabe, der in diesem Bestand gesucht werden soll.  

##### Beschreibung
>Mit 'type' wird zunaechst ueberprueft, zu welcher Bestandsart der entsprechende Bestand gehoert. Wird der Buchstabe innerhalb des Bestands gefunden, wird die der Rueckgabewert *InStock* auf 'True' gesetzt. Grundeinstellung/Fallback fuer *InStock* ist 'False'. 

-----------------------

## Dictionaries  
Geeignet zur Erfassung der Woerterbuecher in einem AVL-Baum.  
Aufbau im Modul `M_Dictionaries`.

### Methoden
#### Dictionary.--init-- (***self***)
Legt ein neues Woerterbuch mit dem Namen von Dictionary an.

##### Objekt
**Dictionary**: Woerterbuch (AVL-Baum), das neu angelegt werden soll.

##### Beschreibung
>Die Methode greift auf die Toolbox **AVLTree** zu und erzeugt einen Grundeintrag für ein neues Woerterbuch, in das später die einzelnen Woerter geladen werden.   
Zurueckgegeben wird ein AVL-Baum mit einem leeren Wurzeleintrag.

#### InDictionary.load (***self, FromDictionaryFile***)  
Laedt ein Woerterbuch aus einer Datei in den Woerterbuch-Baum.  

##### Objekt
**InDictionary**: Woerterbuch (AVL-Baum), in das die Woerterbuch-Datei geladen werden soll.

##### Parameter
- ***FromDictionaryFile***: Dateiname inkl. Pfad, aus dem die Woerter fuer das Woerterbuch geladen werden sollen.

##### Beschreibung
>Die einzelnen Woerter werden aus der Woerterbuch-Datei ausgelesen und in das Woerterbuch eingefuegt, solange bis das Ende der Datei erreicht ist. Doppelte Woerter werden nicht eingefuegt. Dazu wird innerhalb der Tollbox 'AVLTree' die Methode **insert_without_double** genutzt.  
Zurueckgegeben wird ein als AVL-Baum strukturiertes gefuelltes Woerterbuch.

#### FromDictionary.save (***self, InDictionaryFile***)  
Speichert einen Woerterbuch-Baum in einer Woerterbuch-Datei ab.  

##### Objekt
**FromDictionary**: Woerterbuch (AVL-Baum), das in die Woerterbuch-Datei gespeichert werden soll.

##### Parameter
- ***InDictionaryFile***: Dateiname inkl. Pfad, in den die Woerter fuer das Woerterbuch gespeichert werden sollen.

##### Beschreibung
>Zunaechst wird ueberprueft, ob eine Woerterbuch-Datei mit gleichem Namen schon existiert, in diesem Fall wird daraus das Backup gemacht - mit dem Namen 'Dateiname_Entstehungsdatum'. Anschließend wird die Woerterbuch-Datei mit der aktuellen Fassung ueberschrieben. Dazu wird das Woerterbuch (AVL-Baum) ausgelesen und jedes Wort in eine einzelne Zeile geschrieben. Vorher wird ueberprueft, ob bereits eine bestehende Woerterbuch-Datei mitn gleichem namen besteht. In diesem Fall wird der Dateiname der alten Fassung um den Anhang '-old' im Dateinamen ergaenzt. Existiert bereits ein solcher Dateiname, wird die alte Datei ueberschrieben.  
Zurueckgegeben wird eine neue Woerterbuch-Datei.

#### InDictionary.check_word (*self, SearchWord*)
Ueberprüft, ob das eingegebene Wort im Woerterbuch vorhanden ist  

##### Objekt
**InDictionary**: Woerterbuch, in dem das Wort gesucht werden soll.

##### Parameter  
- ***SearchWord***: Wort, das in dem Woerterbuch gesucht werden soll.

##### Beschreibung
>Mit der Methode **search** der **Toolbox AVLTree** wird das Wort im Woerterbuch-Baum gesucht.  
Rueckgabewert ist 'True', wenn das Wort im Woerterbuch gefunden wurde oder 'Fals', falls nicht.  
Ist es nicht enthalten, wird der Nutzer gefragt, ob das Wort richtig geschrieben ist und ist das Fremdwoerterbuch aufgenommen werden soll.

#### InDictionary.add_word (*self, AddWord*)
Fuegt ein Wort in das Woertrebuch ein.

##### Objekt
**InDictionary*: Woerterbuch, in das das Wort ergaenzt werden soll.

##### Parameter
- ***AddWord***: Wort, das in das Woerterbuch eingefuegt werden soll.

##### Beschreibung
>Mithilfe der Methode **insert** der Toolbox **AVLTree** wird das Wort in das jewelige Woerterbuch an der richtigen Stelle eingefuegt. Anschließend wird die Methode **save** aufgerufen, um das ergaenzte Woerterbuch abzuspeichern.  
Zurueckgegeben wird das ergaenzte Woerterbuch.

#### DictionaryFile.check_size (*self*)  
Ermittelt die Groesse (= Anzahl der Eintraege) einer Woerterbuch-Datei.  

##### Objekt
**DictionaryFile**: Name der Datei inkl. Pfad, dessen Groesse bestimmt werden soll.

##### Beschreibung
>Fuer die Ermittlung der Groesse wird die Anzahl der Zeilen in der Woerterbuch-Datei auslesen. Fuer jede Zeile wird der Wert '1' zur Gesamtzahl (*DictionarySizes*) dazuaddiert. Der Startwert von *DictionarySize* betraegt '0'. Leerzeilen werden nicht mitgezaehlt. Ist das Dateiende erreicht, wird die Gesamtzahl (*DictionarySize*) zurueckgegeben.

#### Dictionary.check_status (*self, DictionarySize, NumberLine*)  
Ermittelt, wie viel Prozent der Woerterbuch-Datei bereits in den Woerterbuch-Baum übertragen wurden.

##### Objekt
**Dictionary**: Woerterbuch, dessen Ladestatus ermittelt werden soll.

##### Parameter
- ***DictionarySize***: Groesse (= Anzahl der Eintraege) einer Woerterbuch-Datei, die vorher ermittelt wurde.
- ***NumberLine***: Nummer der aktuell einzulesenden Zeile.

##### Beschreibung
>Zur Ermittlung des aktuellen Status wird die Nummer des aktuell einzulesenden Eintrags ins Verhaeltnis zur Gesamtzahl gesetzt.   Zurueckgegeben wird dann das Verhaeltnis als Prozentzahl.

-----------------------

## Strings  
Geeignet zur Erfassung von Texten, Saetzen, Satzbestandteilen und Wortstandteilen  
Aufbau im Modul `M_Input`

### Attribute
- *String*: Enthaelt eine Zeichenkette.

## TextInput (Strings)
Aufbau im Modul `M_Input`


-----------------------

### Structure of TextTree (TextEdit)

    ┌───────┐           ┌───────┐
    │Content│     ┌────►│Content│     ┌──── =None
    │ =Text1│     │     │ =Text2│     │
    └───────┘     │     └───────┘     │
    │Node   └─────┘     │Node   └─────┘
    │Down   NodeRight   │Down   NodeRight
    │                   │=None
    │
    ▼
    ┌───────┐           ┌───────┐           ┌───────┐
    │Content│     ┌────►│Content│     ┌────►│Content│     ┌──── =None   
    │ =Satz1│     │     │ =Satz2│     │     │ =Satz3│     │
    └───────┘     │     └───────┘     │     └───────┘     │
    │Node   └─────┘     │Node   └─────┘     │Node   └─────┘
    │Down   NodeRight   │Down   NodeRight   │Down   NodeRight
    │                   │=None              │=None
    │
    ▼                   
    ┌───────┐           ┌───────┐           ┌───────┐           ┌───────┐
    │Content│     ┌────►│Content│     ┌────►│Content│     ┌────►│Content│     ┌──── =None
    │ =Wort1│     │     │ =Wort2│     │     │ =Wort3│     │     │ =Wort4│     │
    └───────┘     │     └───────┘     │     └───────┘     │     └───────┘     │
    │Node   └─────┘     │Node   └─────┘     │Node   └─────┘     │Node   └─────┘
    │Down   NodeRight   │Down   NodeRight   │Down   NodeRight   │Down   NodeRight
    │                   │=None              │=None              │=None
    │
    ▼                   
    ┌───────┐           ┌───────┐           ┌───────┐           ┌───────┐           ┌───────┐
    │Content│     ┌────►│Content│     ┌────►│Content│     ┌────►│Content│     ┌────►│Content│     ┌──── =None
    │ =Silb1│     │     │ =Silb2│     │     │ =Silb3│     │     │ =Silb4│     │     │ =Silb5│     │
    └───────┘     │     └───────┘     │     └───────┘     │     └───────┘     │     └───────┘     │
    │Node   └─────┘     │Node   └─────┘     │Node   └─────┘     │Node   └─────┘     │Node   └─────┘
    │Down   NodeRight   │Down   NodeRight   │Down   NodeRight   │Down   NodeRight   │Down   NodeRight
    │                   │=None              │=None              │=None              │=None 
    │
    ▼                   
    ┌───────┐           ┌───────┐           ┌───────┐           ┌───────┐           ┌───────┐
    │Content│     ┌────►│Content│     ┌────►│Content│     ┌────►│Content│     ┌────►│Content│     ┌──── =None
    │ =Teil1│     │     │ =Teil2│     │     │ =Teil3│     │     │ =Teil4│     │     │ =Teil5│     │
    └───────┘     │     └───────┘     │     └───────┘     │     └───────┘     │     └───────┘     │
    │Node   └─────┘     │Node   └─────┘     │Node   └─────┘     │Node   └─────┘     │Node   └─────┘
    │Down   NodeRight   │Down   NodeRight   │Down   NodeRight   │Down   NodeRight   │Down   NodeRight
    │=None              │=None              │=None              │=None              │=None 

-----------------------

## TextEdit (TextInput)
Enthaelt den zu bearbeitenden Text.  
Aufbau im Modul `M_Edit`

### Attribute
- *NodeContent*: Inhalt des Knotens / Grundeinstellung ist '' / Typ str
- *NodeDown*: Zeiger zu tiefer gelegenen Ebene / Grundeinstellung: 'None' 
- *NodeRight*: Zeiger auf den naechten Inhalt in der gleichen Ebene / Grundeinstellung: 'None'
- *NumberText*: Nummer des Textes, der in den Baum gehangen wird. / Grundeinstellung: '0' / Typ int
- *WhoSaid*: Person, der der Text zugordnet wird. Wichtig z.B. bei Dialogen. / Grundeinstellung ist '' / Typ str

### Methoden
#### TextNode.--init-- (*self*)
Erzeugt einen Knoten fuer den Baum.

##### Objekt
**TextNode**: Knoten fuer den Text, der erzeugt werden soll.

##### Beschreibung
>Fuer den Inhalt des Knotens wird mit *NodeContent* = '' ein leerer String angelegt, die Zeiger werden auf 'None' gesetzt: *NodeDown* = None und *NodeRight* = None. *NumberText* wird auf '0' gesetzt, *WhoSaid* wird mit einem leeren String gefülltt. Die Attribute koennen spaeter mit dem jeweiligen Inhalt ueberschrieben werden.  
Zurueckgegeben wird ein Knoten mit den drei Attributen *NodeContent*, *NodeDown* und *NodeRight*.

#### InsertText.insert_string (*self, InTree, NumberText, WhoSaid*)
Fuegt den eingegebenen Text als Wurzel in den Baum ein.

##### Objekt
**InsertText**: Text, der als Wurzel in den Baum gehangen wird. (Typ: Str)

##### Parameter
- ***InTree***: Baum, in den der Text gehangen wird.
- ***NumberText***: Nummer des Textes, der in den Baum gehangen wird. (Typ: Int)
- ***WhoSaid***: Person, der der Text zugordnet wird. Wichtig z.B. bei Dialogen. (Typ: Str)

##### Beschreibung
>Zunaechst wird ein neuer Baum generiert. Anschließend wird der Text als Wurzel eingefuegt: *InTree.NodeContent* = **InsertText**.  
Zurueckgegeben wird ein Baum, dessen Wurzel mit Inhalt gefuellt ist.

#### TextToSplit.split_string (*self*)  
Teilt den Gesamtext in mehrere Saetze auf.  

##### Objekt
**TextToSplit**: Text, der aufgeteilt werden soll.

##### Beschreibung
>Es werden zwei Marker benötigt, einer für den Satzanfang und einer für das Satzende. Der Text wird Buchstabe für Buchstabe überprüft.  Wird eines der Satzzeichen '.', '!' oder '?' gefunden, wird der String bis zu dieser Stelle in einen neuen Satz kopiert. Dabei werden überflüssige Leerzeichen am Satzanfang und Satzende abgeschnitten. Der neue Satz wird als String in einen Baum gehangen. Der Marker für den Satzanfang wird auf die neue Textstelle (Satzzeichen + 1) verschoben. Anschließend geht die Überpruefung an der Stelle weiter.
Die Marker für Satzanfang (*SentenceStart*) und Satzende (*SentenceEnd*) sind Variablen, die nur in der Funktion benötigt werden. Es wird eine interne Variable *NumberSentence* (Typ: Int) eingesetzt, die die laufende Nummer des Satzes abspeichert und mit in den Baum überträgt -> Methode: **insert_string**. Damit können später die einzelnen Sätze gezielt angesteuert werden.  
Zurueckgegeben wird der in Saetze aufgesplittete Text.

## Sentences (TextEdit)
Aufbau im Modul `M_Edit`

### Attribute
- *NodeContent*: Inhalt des Knotens
- *NodeDown*: Zeiger zu tiefer gelegenen Ebene
- *NodeRight*: Zeiger auf den naechten Inhalt in der gleichen Ebene
- *NumberSentence*: Nummer der Reihenfolge des Satzes im Text. (Typ: Int)
- *WhoSaid*: Person, der der Satz zugeordnet wird. (Typ: Str)

### Methoden

#### SentenceNode.--init-- (*self*)
Erzeugt einen Knoten fuer den Baum.

##### Objekt
**SentenceNode**: Knoten fuer den Satz, der erzeugt werden soll.

##### Beschreibung
>Fuer den Inhalt des Knotens wird mit *NodeContent* = '' ein leerer String angelegt, die Zeiger werden auf 'None' gesetzt: *NodeDown* = None und *NodeRight* = None. *NumberSentence* wird auf '0' gesetzt, WhoSaid wird mit einem leeren String gefülltt. Die Attribute koennen spaeter mit dem jeweiligen Inhalt ueberschrieben werden.  
Zurueckgegeben wird ein leerer Knoten fuer einen Satz.
 

#### InsertSentence.insert_string (*self, InTree, NumberSentence, WhoSaid*)
Fuegt einen einzelnen Satz mit einer laufenden Nummer in den Baum ein.

##### Objekt
**InsertSentence**: Satz, der eingefuegt werden soll.

##### Parameter
- ***InTree***: Baum, in den der Satz gehangen wird.
- ***NumberSentence***: Nummer des Satzes, der in den Baum gehangen wird.
- ***WhoSaid***: Person, der der Satz zugordnet wird. Wichtig z.B. bei Dialogen.

##### Beschreibung
>Der einzufuegende Satz wird mit den Attributen in den Baum auf der zweiten Ebene eingefuegt. Handelt es sich um den ersten Satz, wird *NodeContent* mit den einzufuegenden Satz, *NumberSentence* mit '1' und *WhoSaid* mit dem Namen der Person ueberschrieben, der der Satz zugeordnet wird. Ab den folgenden Saetzen muss zuerst ein neuer Knoten initiiert werden und anschließend der Zeiger des vorherigen Satzes auf den neuen Knoten gestellt werden: SentencePredecessor.NodeRight = NodeNeu.  
Zurueckgegeben wird der um den neuen Satz ergaenzte Baum.


#### SentenceToSplit.split_string (*self*)  
Teilt den jeweiligen Satz in Satzbestandteile (Woerter, Satzzeichen etc.) auf.

#### Objekt
**SentenceToSplit**: Satz, der aufgeteilt werden soll.

#### Beschreibung
>Vor jedes Satzzeichen wird ein Leerzeichen gesetzt. Dann wird der Saz überprüft: Sind mehr als zwei Leerzeichen nacheinander vorhanden, wird das erste davon geloescht. Anschließend wird der Satz bei jedem Leerzeichen getrennt und die einzelnen Satzbestandteile als String in einen Baum gehangen, versehen mit der Nummer der Position, an der es gestanden hat. Zudem wird als Attribut (*SwitchPermit*) mitgegeben, ob es sich um einen Satzbestandteil handelt, bei dem die Wortbestandteile getauscht werden duerfen ('True') oder nicht ('False'). Nicht getauscht werden duerfen zum Beispiel Artikel oder Satzzeichen.  
Zurueckgegeben wird ein in Woertern aufgeteilter Satz.



## Words (Sentences)
Zu der in der Klasse 'Words' erfassten Zeichenketten zaehlen nicht nur Woerter, sondern auch beispielweise Satzzeichen.  
Aufbau im Modul `M_Edit`.

### Attribute
- *NodeContent*: Inhalt des Knotens
- *NodeDown*: Zeiger zu tiefer gelegenen Ebene
- *NodeRight*: Zeiger auf den naechsten Inhalt in der gleichen Ebene
- *NumberWord*:Nummer der Reihenfolge des Wortes im jeweiligen Satz. (Typ int)
- *NumberOfSyllables*: Anzahl der einzelnen Teile, in der Regel Silben, des Wortes. (Typ int)
- *SwitchPermit*: Gibt an, ob das Wort zum Tauschen freigegeben ist oder nicht, z.B. bei Artikeln / Grundeinstellung: 'False' (Typ bool)
- *ConnectedWith*: Nummer des anderen Wortes, das mit dem aktuellene Wort ueber eine Kooplung verbunden ist (NumberWord). / Grundeinstellung: 'None' (Typ int)
- *Capital*: Gibt an, ob das Wort mit einem Großbuchstaben anfängt / Grundeinstellung: 'False' (Typ bool)
- *LetterClassInitial*: Typ der Wortbestandteile, zu dem der Anfang des Wortes gehört, z.B. Vokale oder Konsonanten_Stark / Grundeinstellung: 'None' (Typ str)
- *Equal*: Gibt an, ob innerhalb der Spanne ein geeigneter Tauschpartner vorliegt, der mit der gleichen Buchstabenart beginnt / Grundeinstellung: 'False' (Typ bool)
- *SwitchPartnerList*: Liste mit moeglichen Tauschpartnern als verschachtelte Liste mit *NumberWord*, *NumberSyllable*, *NumberPart* / Grundeinstellung: [] (Typ list)


- *NumberSwitchPartner*: Liste mit Nummern der Woerter im Satz, mit denen innerhalb einer Spanne getauscht werden darf / Grundeinstellung: [] (Typ list) 

### Methoden

#### WordNode.--init-- (***self***)
Erzeugt einen Knoten fuer den Baum

##### Objekt
**WordNode**: Knoten fuer das Wort, der erzeugt werden soll.

##### Beschreibung
>Fuer den Inhalt des Knotens wird mit *NodeContent* = '' ein leerer String angelegt, die Zeiger werden auf 'None' gesetzt: *NodeDown* = None und *NodeRight* = None. Die Attribute werden wie folgt gesetzt: *NumberWord* = 0; *NumberOfSyllables* = 0; SwitchPermit* = False; *ConnectedWith* = 0; Capital = False; *Equal* = False; *SwitchPartnerList* = []; *Initial* = None. Die Attribute koennen spaeter mit dem jeweiligen Inhalt ueberschrieben werden.  
Zurueckgegen wird ein leerer Knoten mit den gesetzten Attributen.

#### InsertWord.insert_string (***self, InTree, NumberWord***)
Fuegt ein einzelnes Wort mit einer laufenden Nummer in den Baum ein.

##### Objekt
**InsertWord**: Wort, das in den Baum eingefuegt werden soll.

##### Parameter
- ***InTree***: Baum, in den der Satz gehangen wird.
- ***NumberWord***: Nummer des Worts im Satz, der in den Baum gehangen wird.

##### Beschreibung
>Das einzufuegende Wort wird mit den Attributen in den Baum auf der dritten Ebene eingefuegt. Handelt es sich um das erste Wort, wird *NodeContent* mit dem einzufuegenden Wort und *NumberWord* mit '1' ueberschrieben. Ab den folgenden Worten muss zuerst ein neuer Knoten initiiert werden und anschließend der Zeiger des vorherigen Wortes auf den neuen Knoten gestellt werden: *WordPredecessor.NodeRight* = NodeNeu.  
Zurueckgegeben wird ein gefuellter Knoten fuer ein Wort.

#### WordToSplit.split_string (***self***)  
Teilt das jeweilige Wort in seine Silben auf. 

##### Objekt
**WordToSplit**: Wort, das aufgeteilt werden soll.

##### Beschreibung
>Das Wort wird mit dem Woerterbuch und der entsprechenden Sibentrennung abgeglichen. Jede Silbe wird abgetrennt und in den Baum gehangen.  
Zurueckgegeben wird ein Wort, das in seine Silben auftrennt wurde.

## Syllables (Words)
Die Klasse enthaelt die Silben der einzelnen Woerter.
Aufbau im Model `M_Edit`.

### Attribute
- *NodeContent*: Inhalt des Knotens
- *NodeDown*: Zeiger zu tiefer gelegenen Ebene
- *NodeRight*: Zeiger auf den naechsten Inhalt in der gleichen Ebene
- *NumberSyllable*:Nummer der Reihenfolge des Wortes im jeweiligen Satz. (Typ int)
- *NumberOfParts*: Anzahl der einzelnen Teile, in der Regel Silben, des Wortes. (Typ int)

### Methoden

#### SyllableNode.--init-- (***self***)
Erzeugt einen Knoten fuer den Baum

##### Objekt
**SyllableNode**: Knoten fuer das Wort, der erzeugt werden soll.

##### Beschreibung
>Fuer den Inhalt des Knotens wird mit *NodeContent* = '' ein leerer String angelegt, die Zeiger werden auf 'None' gesetzt: *NodeDown* = None und *NodeRight* = None. Die Attribute werden wie folgt gesetzt: *NumberSyllable* = 0; *NumberOfParts* = 0. Die Attribute koennen spaeter mit dem jeweiligen Inhalt ueberschrieben werden.  
Zurueckgegen wird ein leerer Knoten mit den gesetzten Attributen.

#### InsertSyllable.insert_string (***self, InTree, NumberSyllable***)
Fuegt eine einzelne Silbe mit einer laufenden Nummer in den Baum ein.

##### Objekt
**InsertSyllable**: Silbe, das in den Baum eingefuegt werden soll.

##### Parameter
- ***InTree***: Baum, in den der Satz gehangen wird.
- ***NumberSyllable***: Nummer des Worts im Satz, der in den Baum gehangen wird.

##### Beschreibung
>Die einzufuegende Silbe wird mit den Attributen in den Baum auf der viertem Ebene eingefuegt. Handelt es sich um die erste Silbe, wird *NodeContent* mit dem einzufuegenden Wort und *NumberSyllable* mit '1' ueberschrieben. Ab den folgenden Silben muss zuerst ein neuer Knoten initiiert werden und anschließend der Zeiger der vorherigen Silbe auf den neuen Knoten gestellt werden: *SyllablePredecessor.NodeRight* = NodeNeu.  
Zurueckgegeben wird ein gefuellter Knoten fuer eine Silbe.


#### SyllableToSplit.split_string (***self***)  
Teilt die jeweilige Silbe in mehrere Wortbestandteile auf. 

##### Objekt
**SyllableToSplit**: Silbe, das aufgeteilt werden soll.

##### Beschreibung
>Es werden zwei Marker benötigt, einer für den Silbenbestandteilanfang und einer für das Silbenbestandteilende. Wechselt der aktuelle Buchstabe von Vokal zu Konsonant oder Satzzeichen oder Sonstige - oder umgekehrt -, wird der aktuelle Silbenbestandteil abgeschnitten und als String in einen Baum gehangen. Der Marker für den Silbenbestandteilanfang wird auf die neue Textstelle (Silbenbestandteilende + 1) verschoben. Anschließend geht die Überprüfung an der Stelle weiter. Die Marker für Silbenbestandteilanfang (*SyllableElementStart*) und Satzende (*SyllabeElementEnd*) sind Variablen, die nur in der Funktion benötigt werden. Es wird eine interne Variable *NumberElement* (Typ: Int) eingesetzt, die die laufende Nummer des Wortbestandteils abspeichert und mit in den Baum überträgt . Damit können später die einzelnen Wortbestandteile gezielt angesteuert werden.  
Zurueckgegeben wird ein in ihre Bestamdteile zerlegte Silbe.


## Parts (Words)
Enthaelt die einzelnen Bestandteile der Silbe, z.B. St|e-(|f|a|n)
Aufbau im Modul `M_Edit`.

### Attribute
- *NodeContent*: Inhalt des Knotens
- *NodeDown*: Zeiger zu tiefer gelegenen Ebene
- *NodeRight*: Zeiger auf den naechten Inhalt in der gleichen Ebene
- *InTree*: Baum, in den der Satz gehangen wird.
- *NumberPart*: Nummer des Teil im Wort, der in den Baum gehangen wird.

### Methoden

#### PartNode.--init-- (***self***)
Erzeugt einen Knoten fuer den Baum.

##### Objekt
**PartNode**: Knoten fuer den Wortbestandteil, der erzeugt werden soll.

##### Beschreibung
>Fuer den Inhalt des Knotens wird mit *NodeContent* = '' ein leerer String angelegt, die Zeiger werden auf 'None' gesetzt: *NodeDown* = None und *NodeRight* = None. Die Attribute koennen spaeter mit dem jeweiligen Inhalt ueberschrieben werden.  
Zurueckgegeben wird ein leerer Knoten fuer ein Wortteil.

#### InsertPart.insert_string (***self, InTree, NumberPart***)
Fuegt einen einzelnes Wort mit einer laufenden Nummer in den Baum ein.

##### Objekt
**InsertPart**: Wortbestandteil, der in den Baum gehangen werden soll.

##### Parameter
- ***InTree***: Baum, in den der Satz gehangen wird.
- ***NumberPart***: Nummer des Worts im Satz, der in den Baum gehangen wird.

##### Beschreibung
>Der einzufuegende Teil wird mit den Attributen in den Baum auf der vierten Ebene eingefuegt. Handelt es sich um den ersten Teil, wird *NodeContent* mit dem einzufuegenden Teil und *NumberPart* mit '1' ueberschrieben. Ab den folgenden Teilen muss zuerst ein neuer Knoten initiiert werden und anschließend der Zeiger des vorherigen Wortes auf den neuen Knoten gestellt werden: *WordPredecessor.NodeRight* = NodeNeu.  
Zurueckgegeben wird ein mit den Inhalten gefuellter Knoten.

-----------------------

## WordsAnalyze (Words)
Bildet die Klasse ab, mit der die Analyseprozesse auf Satzbestandteilebene durchgeführt werden.
Aufbau im Modul `M_Analyze`.


### Methoden
#### WordToBeAnalyzed.check (***self***)  
Steuert die gesamten Ueberpruefungsprozess, z.B. Grossschreibung am Wortanfang, beim jeweiligen Wort:

##### Objekt
**WordToBeAnalyzed**: Wort, fuer das die Checks durchgefuehrt werden sollen.

##### Beschreibung
>Die Methode ruft nach und nach die durchzufuehrenden Einzelchecks auf. Anschließend werden in Abhaengigkeit der Check-Ergebnisse die Attribute des jeweiligen Wortes gefuellt  
    - falls **check_switch_permit** 'True' zurueckliefert, wird *SwitchPermit* = True gesetzt, sonst bleibt es bei der Grundeinstellung 'False'  
    - falls **check_capital** 'True' zurueckliefert, wird *Capital* = True gesetzt, sonst bleibt es bei der Grundeinstellung 'False'  
    - in Abhaengigkeit des Rueckgabewertes von **checl_class_part** wird *LetterClassInitial* gesetzt.  
    
    Es werden auf jeden Fall alle moeglichen Checks fuer ein Wort durchgefuehrt, damit zukuenftige Erweiterungen einfacher umgesetzt werden koennen.  
Zurueckgegeben wird ein mit allen Checks versehenes Wort.

#### WordToBeAnalyzed.check_switch_permit (***self***)
Ueberprueft, ob das jeweilige Wort ueberhaupt zum Tausch herangezogen werden darf.

##### Objekt
**WordToBeAnalyzed**: Wort, fuer das die Ueberpruefung, ob es zum Tausch herangezogen werden darf, durchgefuehrt werden soll.

##### Beschreibung
>Fuer das Wort erfolgt ein Abgleich, ob es in einer der Wort-Mengen, z.B. Artikel, ist, die nicht zum Tausch herangezogen werden duerfen. Falls getauscht werden darf, wird **check_switch_permit** mit 'True' zurueckgeliefert, sonst mit 'False'.

#### WordToBeAnalyzed.check_capital (***self***)
Ueberprueft, ob das jeweilige Wort mit einem Grossbhuchstaben anfaengt.

##### Objekt
**WordToBeAnalyzed**: Wort, fuer das die Ueberpruefung auf einen Grossbuchstaben durchgefuehrt werden soll.

##### Beschreibung
>Fuer das Wort erfolgt ein Abgleich, ob es mit einem Grossbuchstaben (Funktion **capital**) beginnt. Falls das der Fall ist, wird **check_capital** mit 'True' zurueckgeliefert, sonst mit 'False'.

#### WordToBeAnalyzed.check_class_part (***self, NumerCheckSyllable = 1, NumberCheckPart = 1***)
Ueberprueft, mit mit welcher Buchstabenklasse das Wort beginnt, z.B. Vokale.

##### Ojekt
**WordToBeAnalyzed**: Wort, fuer das ueberprueft werden soll, mit welcher Buchstabengruppe der erste Buchstabe beginnt.

##### Parameter
- ***NumberCheckSyllable***: Silbe des Wortes, der ueberprueft werden soll, standardmaessig die erste Silbe
- ***NumberCheckPart***: Teil der Silbe, der ueberprueft werden soll, standardmaessig der erste Teil

##### Beschreibung
>Zur Ueberpruefung wird der angegebene Wortbestandteil herangezogen und mit den entsprechenden Mengen, die ueber die Config-Datei eingelesen wurden, abgeglichen. Die Methode liefert dann als Ergebnis die Buchstabenklasse zurueck. Diese wird ueber die Methode **check** in das Attribut des Worts *LetterClassInitial* ueberspielt.

#### WordToBeAnalyzed.check_equal (***self, LetterClass, Range***)
Ueberprueft, ob fuer das jeweilige Wort ein Tauschpartner innerhalb der Spanne vorliegt.

##### Objekt
*WordToBeAnalyzed*: Wort, fuer das die Ueberpruefung, ob ein anderes passendes Wort innerhalb der Spanne vorliegt, durchgefuehrt werden soll.

##### Parameter
- ***LetterClass***: Buchstabengruppe, nach der Woerter in der Nachbarschaft ueberprueft werden sollen.
- ***Range***: Spanne innerhalb der gesucht werden soll.

##### Beschreibung
>Fuer das Wort erfolgt ein Abgleich, ob sich innerhalb der vorgegebenen Spanne ein Wort, das mit der gleichen Buchstabenart beginnt, vorliegt. Falls ja, wird die Nummer des Wortes im Attribut *NumberSwitchPartner* festgehalten und das Attribut *SwitchPartForeign* auf '1' gesetzt, da der erste Teil des anderen Wortes getauscht wird. Die Ueberpruefung findet ab dem direkten Wortnachbarn rechts statt und endet bei dem Wort, dessen Nummer gleich der Nummer des aktuellen Wortes + der Spanne ist.   
Zurueckgegeben werden die Nummer der in der Spanne gefundenen passenden Tauschpartner.

#### WordToBeAnalyzed.check_inner (***self***)
Ueberprueft, ob ein Buchstabentausch innerhalb des gleichen Wortes moeglich ist.

##### Objekt
**WordToBeAnalyzed**: Wort, bei dem ueberprueft werden soll, ob ein Tausch von Bestandteilen innerhalb des Wortes moeglich ist.

##### Beschreibung
>Innerhalb des Wortes werden die einzelnen Teile nacheinander durchgegangen. Fuer jeden Teil wird ueberprueft, zu welcher Buchstabengruppe er gehoert. Dazu wird die Methode **check_class_part** aufgerufen. Ist seine Gruppe gleich mit der des Wortanfangs, wird das Attribut *SwitchForeignPart* auf die Nummer des Teils im Wort gesetzt. Der Rueckgabewert der Methode ist 'True', wenn ein Wortteil der gleichen Buchstabengruppe gefunden wird, sonst 'False'.

-----------------------

## WordsCombine (Words)

### Attribute
- *SumPoints*: Gesamtpunktzahl der Kombination für das Ranking. Grundeinstellung ist '0' / Typ Int
- *Part1*: Liste aus Nummer Wort 1, Position in Wort 1
- *Part2*: Liste aus Nummer Wort 2, Position in Wort 2

### Methoden

#### AllWords.fill_switches (***self***)
Erstellt fuer das aktuelle Wort eine Liste mit moeglichen Tauschpartnern.

##### Objekt
**AllWords**: Alle Woerter eines Satzes.

##### Beschreibung
>Der aktuelle Satz wird Wort fuer Wort durchgegangen. Dabei wird bei jedem Wort ueberprueft, ob es zum Tausch herangezogen werden darf, d.h. das Attribut *SwitchPermit* auf 'True' gesetzt wurde. In diesem Fall wird das Attribut *SwitchPartnerList* um eine verschachtelte Liste mit den Werten *NumberWord*, *NummerSyllable* = 1 und *NumberPart* = 1 gefuellt. Anschließend wird das naechster Wort aus der Liste von *NumerSwitchPartner* angesteuert. Auch von diesem Wort werden die Werte von *NumberWord*, *NumberSyllable* = 1 und *NumberPart* = 1 als verschachtelte Liste dort reingeschrieben.
# Wie steuert das Routine eine Tauschoperation innerhalb eines Wortes an?

#### CurrentWord.combine (self)

CurrentCombination: Aktuell 

*Steuert das Kombinieren von Wortbestandteilen.*


- **combine_connected**: Tauscht die beiden Anfangswortbestandteile eines gekoppelten Wortes

- **rate**: Steuert, welche Ratings der Wortkombinationen durchgefuehrt werden sollen.
- **rate_in_dictionary**: Ueberprueft, ob eines oder die beiden Woerter in einem der Woerterbuecher auftauchen. Falls ja, werden die Punkte von RateInDictionary mit dem jweiligen Faktor zur Gesamtpunktzahl (SumPoints) dazuaddiert.
- **rate_in_user**: Ueberprueft, ob eines oder die beiden Woerter im Woerterbuch der User als beliebtes Wort auftauchen. Falls ja, werden die Punkte von RateInUser mit dem jeweiligen Faktor zur Gesamtpunktzahl (SumPoints) dazuaddiert.
- **rate_number_letters**: Ueberprueft, wie viele Buchstaben insgesamt in der Kombination der beiden Worte getauscht wurden und addiert pro Buchstaben die Punkte fuer RateNumberLetters mit dem jeweiligen Faktor zur Gesamtpunktzahl.
- **rate_words_linked**: Ueberprueft, ob die Kombination aus zwei miteinander gekoppelten Worten besteht und addiert fuer diesen Fall die Punkte von RateWordsLinked mit dem Faktor zur Gesamtpunktzahl hinzu.





### CombinationList
#### Methoden
- **insert**: Fuegt eine neue Wortkombination mit der Gesamtpunktzahl in die Liste ein.
- **delete**: Loescht eine Wortkombination aus der Liste.
- **sort**: Sortiert die Liste nach der Gesamtpunktzahl. Algorithmus: Bubble-Sort.
- **rank_list (Word1:Part1, Word2:Part2, Points)**: Sortiert die Liste aus Kombinationen in die richtige Reihenfolge, gemessen an der Gesamtpunktzahl pro Kombination. Anschließend gibt die Funktion die Daten der am höchsten bewerteten Kombination zurück: Word1:Part1, Word2:Part2 / Regeln: An die Funktion rank_list werden die entsprechenden Daten zu den Kombinationen uebergeben und in eine Liste geschrieben. Sollten keine weiteren Kombinationen zur Verfügung stehen, wird die Funktion noch einmal aufgerufen, aber mit den Argumenten 'None:None', 'None:None', '0'. Die Funktion uberprueft zuerst ob diese Werte uebergeben wurden. Falls nein, werden die Werte in eine Liste geschrieben. Falls ja, startet die Sortierung der Liste und die Daten der Kombination mit der hoechsten Punktezahl wird zurueckgegeben.



- *SwitchPartOwn*: Gibt an, welcher Bestandteil des eigenen Wortes getauscht werden soll / Grundeinstellung: 'None' (Typ int)
- *SwitchPartForeign*: Teil welches fremden Wortes, der getauscht werden soll. (NumberWord:NumberPart) / Grundeinstellung: 'None' : 'None' (Typ dic)




-----------------------

### TextOutput (Strings)
Aufbau im Modul M_Output

#### Attribute

#### Methoden

-----------------------------

## Funktionen



### rank_list (Word1:Part1, Word2:Part2, Points)
Sortiert die Liste aus Kombinationen in die richtige Reihenfolge, gemessen an der Gesamtpunktzahl pro Kombination. Anschließend gibt die Funktion die Daten der am höchsten bewerteten Kombination zurück: Word1:Part1, Word2:Part2 
#### Regeln
An die Funktion rank_list werden die entsprechenden Daten zu den Kombinationen uebergeben und in eine Liste geschrieben. Sollten keine weiteren Kombinationen zur Verfügung stehen, wird die Funktion noch einmal aufgerufen, aber mit den Argumenten 'None:None', 'None:None', '0'. Die Funktion uberprueft zuerst ob diese Werte uebergeben wurden. Falls nein, werden die Werte in eine Liste geschrieben. Falls ja, startet die Sortierung der Liste und die Daten der Kombination mit der hoechsten Punktezahl wird zurueckgegeben.


------------------------

### AvlTree (aus Toolbox AVLTree)

#### Methoden
- **insert**: Fuegt einen neuen Knoten für ein neues Wort in den Baum ein.
- **insert_without_double**: Fuegt einen neuen Knoten in den Baum ein, aber nur wenn das keyword nicht bereits existiert.
- **rebalance**: Richtet den Baum neu aus.
- **update_heights**: Ermittelt die aktuelle Höhe des Baums.
- **update_balances**: Ermittelt, ob der Baum ausbalanciert ist.
- **rotate_right**: Fuehrt eine Rechtsrotation im Knoten durch.
- **rotate_left**: Fuehrt eine Linksrotation im Knoten durch.
- **delete**: Loescht einen Knoten aus dem Baum.
- **search**: Sucht ein keyword in dem Baum.
- **inorder_traverse**: Liest den Baum nach der Regel Links-Wurzel-Rechts aus.
- **preorder_traverse**: Liest den Baum nach der Regel Wurzel_Links-Rechts aus.
- **postorder_traverse**: Liest den Baum nach der Regel Links-Rechts-Wurzel aus.
- **levelorder_traverse**: Liest den Baum etagenweise aus.

----------------------

# Variablen

### Global

Text = Trees
InputText = TextInput
OutputText = TextOutput

### kurzzeitig einsetzbar
- Counter: benoetigt für Zaehloperationen in Schleifen



 
 #### *Attributes*
 - SwapAllowed: True/False
 - ConnectedWith: Number
 - Capital: True/False
 - SwitchPartOwn: Number
 - SwitchPartForeign: Number
 - Initial: Stock
 
 
 # Dateien



