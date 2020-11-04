# Geheimsprache mit Kryptographie
## ~avatar avatar @unplugged
Verschicke geheime Nachrichten welche du mit dem Calliope verschlüsseln und wieder entschlüsseln kannst.


## ~ @unplugged
Lerne wie du Listen bzw. Arrays den @boardname@ zu einem Codierer bzw. Decodierer programmierst.
Mit den Knöpfen A und B sollst du durch das Alphabet schalten können. Wenn du beide Knöpfe gleichzeitig drückst soll dir die verschlüsselte bzw. entschlüsselte Variante angezeigt werden.

## Schritt 1: Erstelle eine Liste
``||basic:Beim Start||`` des @boardname@ soll eine ``||arrays:Liste||`` mit dem Alphabet von A bis Z erstellt werden. Erstelle dafür die ``||variables:Variable||`` ``||variables:Buchstabenliste||``.
Auf die Variable soll nun ein ``||arrays:leeres Array||`` gespeichert werden. Dieses kann mit dem + Symbol erweitert werden. Jetzt kannst du in jedes Feld einen Buchstaben eintragen.
```blocks
let Buchstabenliste = ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"]
```
## Schritt 2 Durch die Buchstaben schalten
Wenn du schon die Jukebox aus der KISS-MINT Tutorialreihe gemacht hast sollte dir dieser Schritt bekannt vorkommen.
Nehme als erstes den Block ``||input:wenn Knopf A gedrückt||`` in diesen Block kommt die ``||logic:wenn dann ansonsten||`` Bedingung.
Nun soll bei einem Knopfdruck die Variable ``||variables:buchstabenNummer||`` auf 25 gesetzt werden wenn diese kleiner 1 ist. Anonsten soll sie um eins verringert werden.
Ähnlich wird es auch für den Knopf B gemacht sobald die ``||variables:buchstabenNummer||`` hier größer 24 wird soll sie auf 0 gesetzt werden. Ansonsten soll sie um 1 erhöht werden.
Hinweis du kannst auch den ganzen ``||input:wenn Knopf A gedrückt||`` Block nach einem Rechtsklick duplizieren so musst du nur noch die Werte ändern.

```blocks
input.onButtonPressed(Button.A, function () {
    if (buchstabenNummer < 1) {
        buchstabenNummer = 25
    } else {
        buchstabenNummer += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (buchstabenNummer > 24) {
        buchstabenNummer = 0
    } else {
        buchstabenNummer += 1
    }
})
``` 
## Schritt 3: Erweitern der Liste
Erweiter nun deine Liste um ein weiteres Alphabet, sodass nach dem Z einfach nochmal das A bis Z kommt. Dies brauchen wir zum Ver- und Entschlüsseln.
```blocks
let Buchstabenliste = ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z", "A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"]
```

## Schritt 4: Die Buchstaben anzeigen lassen
Nun sollen uns die Buchstaben ``||basic:dauerhaft||`` angezeigt werden und bei einem Knopfdruck beider Tasten der Codierte Buchstabe angezeigt werden. Hierzu nehmen wir nochmals eine ``||logic:wenn dann ansonsten||`` Bedingung. 
In die Bedinung kommt der Block ``||input:wenn Knopf A+B ist gedrückt||``. Sobald dies erfüllt ist soll die ``||basic:Farbe der RGB LED auf grün gesetzt||`` werden und über ``||basic:zeige Text||`` soll der ``||arrays:Wert aus der Liste||`` ``||variables:Buchstabenliste||`` bei ``||variables:BuchstabenNummer||`` ``||math:+13||`` abgerufen werden
Um dies eine Kurze Zeit anzeigen zu lassen verwende am besten noch eine ``||basic:pause||`` von 100ms.
Ansonsten soll die ``||basic:RGB LED ausgeschalten||`` werden. Dafür setzt du die Farbe einfach auf schwarz. Ebenso soll hier über ``||basic:zeige Text||`` der ``||arrays:Wert aus der Liste||`` ``||variables:Buchstabenliste||`` bei ``||variables:BuchstabenNummer||`` abgerufen werden.

```blocks

basic.forever(function () {
    if (input.buttonIsPressed(Button.AB)) {
        basic.setLedColor(0x00ff00)
        basic.showString("" + (Buchstabenliste[buchstabenNummer + 13]))
        basic.pause(100)
    } else {
        basic.setLedColor(0x000000)
        basic.showString("" + (Buchstabenliste[buchstabenNummer]))
    }
})

let buchstabenNummer = 0
```
## Schritt 5: Verwende deine eigene verschlüsselung
Dein Programm sollte nun fertig sein und mit einer ROT13 Verschlüsselung funktionieren. Änderst du die Zahl 13 in dem Block aus ``||math:Mathematik||`` zu einer anderen Zahl kannst du den Schlüssel selbst festlegen.

```blocks
input.onButtonPressed(Button.A, function () {
    if (buchstabenNummer < 1) {
        buchstabenNummer = 25
    } else {
        buchstabenNummer += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (buchstabenNummer > 24) {
        buchstabenNummer = 0
    } else {
        buchstabenNummer += 1
    }
})
let buchstabenNummer = 0
let Buchstabenliste = ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z", "A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"]
basic.forever(function () {
    if (input.buttonIsPressed(Button.AB)) {
        basic.setLedColor(0x00ff00)
        basic.showString("" + (Buchstabenliste[buchstabenNummer + 13]))
        basic.pause(100)
    } else {
        basic.setLedColor(0x000000)
        basic.showString("" + (Buchstabenliste[buchstabenNummer]))
    }
})
```


> Diese Seite bei [https://r00b1nh00d.github.io/geheimsprache-kryptographie/](https://r00b1nh00d.github.io/geheimsprache-kryptographie/) öffnen

## Als Erweiterung verwenden

Dieses Repository kann als **Erweiterung** in MakeCode hinzugefügt werden.

* öffne [https://makecode.calliope.cc/](https://makecode.calliope.cc/)
* klicke auf **Neues Projekt**
* klicke auf **Erweiterungen** unter dem Zahnrad-Menü
* nach **https://github.com/r00b1nh00d/geheimsprache-kryptographie** suchen und importieren

## Dieses Projekt bearbeiten ![Build Status Abzeichen](https://github.com/r00b1nh00d/geheimsprache-kryptographie/workflows/MakeCode/badge.svg)

Um dieses Repository in MakeCode zu bearbeiten.

* öffne [https://makecode.calliope.cc/](https://makecode.calliope.cc/)
* klicke auf **Importieren** und dann auf **Importiere URL**
* füge **https://github.com/r00b1nh00d/geheimsprache-kryptographie** ein und klicke auf Importieren

## Blockvorschau

Dieses Bild zeigt den Blockcode vom letzten Commit im Master an.
Die Aktualisierung dieses Bildes kann einige Minuten dauern.

![Eine gerenderte Ansicht der Blöcke](https://github.com/r00b1nh00d/geheimsprache-kryptographie/raw/master/.github/makecode/blocks.png)

#### Metadaten (verwendet für Suche, Rendering)

* for PXT/calliopemini
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
