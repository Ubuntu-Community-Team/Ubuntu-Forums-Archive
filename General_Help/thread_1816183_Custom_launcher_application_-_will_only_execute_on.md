---
title: "Custom launcher application - will only execute once."
date: 2011-08-01
forum: General Help
---

### Post by KyleHyde on 2011-08-01
I'm running 11.04, and I installed the following script for a custom google docs launcher to put in the unity launcher.  However, if I execute the application it opens, but once I close the browser, the google docs launcher is no longer clickable

As a side note, I'd also like the launcher to open the new template of google docs because it opens to the older interface when selecting to make a new document.

```
[Desktop Entry]
Version=1.0
Name=Google Docs
Exec=xdg-open https://docs.google.com/
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=chrome-https___docs.google.com_
Categories=Network;WebBrowser;
StartupNotify=true
StartupWMClass=docs.google.com

X-Ayatana-Desktop-Shortcuts=Doc;Spreadsheet;Presentation;Drawing

[Doc Shortcut Group]
Name=New Document
Exec=xdg-open https://docs.google.com/?action=newdoc
TargetEnvironment=Unity

[Spreadsheet Shortcut Group]
Name=New Spreadsheet
Exec=xdg-open https://spreadsheets.google.com/ccc?new
TargetEnvironment=Unity

[Presentation Shortcut Group]
Name=New Presentation
Exec=xdg-open https://docs.google.com/?action=new_presentation
TargetEnvironment=Unity

[Drawing Shortcut Group]
Name=New Drawing
Exec=xdg-open https://docs.google.com/drawings/create?hl=en
TargetEnvironment=Unity
```

---

### Post by KyleHyde on 2011-08-03
Any thoughts?

---

