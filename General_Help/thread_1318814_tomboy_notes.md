---
title: "tomboy notes"
date: 2009-11-07
forum: General Help
---

### Post by beginner12 on 2009-11-07
i have used tomboy notes for a long time but wen i was updating it once the updater had an error and tomboy notes will not open. wen i go to shut down my laptop it says that tomboy notes is not responding. any ideas on how to make it work again?

---

### Post by tgalati4 on 2009-11-08
Examine the folder .tomboy carefully.  It contains your individual notes and the database file.  My guess is the database file is borked.  Make a backup:

cp -r .tomboy .tomboy-backup

Try deleting the database file and restarting tomboy.  It may come up--or it may not.  If that doesn't work, then delete the .tomboy directory (presuming you made a backup).  Tomboy should start up without any notes.  Then bring your notes back into .tomboy a few at a time.

If that doesn't work, then it's possible that your tomboy/mono installation is borked.

sudo apt-get remove tomboy
sudo apt-get install tomboy

---

### Post by beginner12 on 2009-11-08
ok bt i searched and cant find the .tomboy folder. where shud it be?

---

### Post by directhex on 2009-11-08
> **beginner12 said:**
> ok bt i searched and cant find the .tomboy folder. where shud it be?

It's moved to be XDG-compliant.

Try deleting ~/.config/tomboy, which should be unintrusive (i.e. not touch your notes)

Following that, back up ~/.local/share/tomboy and then delete it

---

### Post by beginner12 on 2009-11-09
tgalati4- i did the things u said but tomboy still doesnt open
any other ideas?
if not thank you trying

---

### Post by itsbrad212 on 2009-11-09
type Ctrl and H at the same time while in your home folder. that will show hidden files :D

---

### Post by itsbrad212 on 2009-11-09
sorry, that post i made was wrong about where to look. but Ctrl + H is the way to show hidden files :D

---

### Post by tgalati4 on 2009-11-09
Open a terminal:

tomboy --debug

Post the output.

It should look something like:

tgalati4@tpad-Gloria7 ~ $ tomboy --debug
** Running Mono with --debug    **
[DEBUG]: NoteManager created with note path "/home/tgalati4/.tomboy".
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]: 	       Name: Tomboy.Tomboy,0.10
[DEBUG]: 	Description: 
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/Tomboy.exe
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.EvolutionAddin
[DEBUG]: 	       Name: Evolution Mail Integration
[DEBUG]: 	Description: Allows you to drag an email from Evolution into a tomboy note.  The message subject is added as a link in the note.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Evolution.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.PrintNotesAddin
[DEBUG]: 	       Name: Printing Support
[DEBUG]: 	Description: Allows you to print a note.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/PrintNotes.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.BacklinksAddin
[DEBUG]: 	       Name: Backlinks
[DEBUG]: 	Description: See which notes link to the one you're currently viewing.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Backlinks.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FixedWidthAddin
[DEBUG]: 	       Name: Fixed Width
[DEBUG]: 	Description: Adds fixed-width font style.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FixedWidth.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.ExportToHtmlAddin
[DEBUG]: 	       Name: Export to HTML
[DEBUG]: 	Description: Exports individual notes to HTML.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/ExportToHtml.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.StickyNoteImportAddin
[DEBUG]: 	       Name: Sticky Notes Importer
[DEBUG]: 	Description: Import your notes from the Sticky Notes applet.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/StickyNoteImport.dll
[DEBUG]: StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG]: 	       Name: WebDav Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG]: 	       Name: Local Directory Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a local file system path
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found all system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: Tomboy is already running.  Exiting...

---

### Post by beginner12 on 2009-11-10
thanks that last 2 post really help 
thank you fo helping me!

---

