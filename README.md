# Soul Link Tracker – Anleitung

Gemeinsame Liste für einen Pokémon-Soul-Link-Run. Beide Spieler öffnen dieselbe Web-Seite, geben denselben **Run-Code** ein und sehen alle Änderungen live.

- **Seite:** läuft kostenlos über GitHub Pages
- **Daten:** liegen kostenlos in Firebase (Google), Firestore-Datenbank
- Einrichtung einmalig ca. 15 Minuten, nur durch **eine** Person nötig

---

## Teil 1 – Firebase einrichten (Datenbank)

1. Öffne <https://console.firebase.google.com> und melde dich mit einem Google-Konto an.
2. **„Projekt erstellen“** → Name z. B. `soullink` → Google Analytics kannst du **deaktivieren** → Projekt erstellen.
3. Links im Menü: **Build → Firestore Database** → **„Datenbank erstellen“**
   - Standort: `eur3 (europe-west)` oder `europe-west3 (Frankfurt)`
   - Modus: **Produktionsmodus** → Erstellen
4. In Firestore oben auf den Tab **„Regeln“** klicken, den Inhalt komplett ersetzen durch den Inhalt der Datei **`firestore.rules`** und auf **„Veröffentlichen“** klicken.
5. Links oben auf das **Zahnrad ⚙ → Projekteinstellungen**. Ganz unten bei „Meine Apps“ auf das **Web-Symbol `</>`** klicken.
   - App-Spitzname: `soullink` → **App registrieren** (Firebase Hosting **nicht** anhaken)
   - Es erscheint ein Code-Block mit `const firebaseConfig = { ... }`. **Diese 6 Werte brauchst du gleich.**

## Teil 2 – Konfiguration eintragen

Öffne `index.html` mit einem Texteditor (z. B. Notepad, VS Code) und ersetze oben im Skript-Teil den Block

```js
const firebaseConfig = {
  apiKey: "HIER_EINFÜGEN",
  ...
};
```

durch deinen Block aus Firebase. Speichern.

> Der `apiKey` ist kein Geheimnis – er darf öffentlich auf GitHub stehen. Geschützt werden eure Daten durch die Regeln und den Run-Code.

## Teil 3 – Auf GitHub veröffentlichen

1. Auf <https://github.com> anmelden (bzw. kostenloses Konto erstellen).
2. Oben rechts **„+“ → New repository** → Name z. B. `soullink` → **Public** → **Create repository**.
3. Auf der neuen Seite auf **„uploading an existing file“** klicken, `index.html` (und gerne auch `firestore.rules` und `README.md`) hineinziehen → **Commit changes**.
4. Im Repository: **Settings → Pages** → bei „Branch“ **`main`** und **`/ (root)`** wählen → **Save**.
5. Nach 1–2 Minuten steht oben die Adresse, z. B. `https://DEINNAME.github.io/soullink/` – das ist eure Seite.

## Teil 4 – Loslegen

1. Seite öffnen → **„🎲 Neuen Code erzeugen“** → **Öffnen**.
2. In **⚙ Einstellungen** eure Namen und den Run-Namen eintragen. Dort steht auch der Run-Code mit **Kopieren**-Knopf.
3. Deinem Kollegen **den Link + den Run-Code** schicken. Er gibt den Code einmal ein – fertig.

Der Code wird im Browser gespeichert. Auf einem neuen PC / Browser muss er nur einmal neu eingegeben werden.

---

## Gut zu wissen

- **Run-Code = Passwort.** Wer Link und Code kennt, kann mitschreiben. Nicht öffentlich posten.
- **Mehrere Runs:** Einfach in den Einstellungen „Run wechseln“ und einen neuen Code erzeugen. Jeder Code hat seine eigene Liste.
- **Kosten:** Der kostenlose Firebase-Tarif (Spark) reicht für so eine Liste bei Weitem; es wird keine Kreditkarte verlangt.
- **Später etwas ändern:** Neue `index.html` auf GitHub hochladen (gleicher Dateiname überschreibt). Eure Daten bleiben erhalten, weil sie in Firebase liegen.
- **Fehlermeldung „Zugriff verweigert“:** Die Regeln aus Schritt 1.4 sind nicht veröffentlicht.
- **Fehlermeldung „Firebase ist noch nicht eingerichtet“:** Die Konfiguration aus Teil 2 fehlt.
