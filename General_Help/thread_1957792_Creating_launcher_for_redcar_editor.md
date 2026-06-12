---
title: "Creating launcher for redcar editor"
date: 2012-04-13
forum: General Help
---

### Post by warri0r on 2012-04-13
I have installed redcar but i can launch it only through terminal. how can i create a launcher for the application and add it to the menu options? thanks

---

### Post by brainwash on 2012-04-13
Create an application launcher and place it here:
```
~/.local/share/applications
```

Adding following line to the launcher will make sure, that the entry will show up in the right category:
```
[Desktop Entry]
...
**Categories=Development;**
```

---

### Post by Jose Catre-Vandis on 2012-04-14
If you want to do it via the gui (for a Panel entry):

1. Right click on a panel
2. Click on Add New Items
3. Click on Launcher (should be the first item)
4. Click Add then Close ( a blank launcher will appear in your panel)
5. Right Click on the new Launcher and select Properties
6. Click on the "Add a New Empty Item" icon
7. Enter the details for redcar & choose an icon
8. Close out

---

