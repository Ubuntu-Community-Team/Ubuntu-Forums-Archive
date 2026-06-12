---
title: "Opera  doesn't load themes"
date: 2010-01-14
forum: General Help
---

### Post by TyrantWave on 2010-01-14
Ok, I recently installed Opera 10.10, and I'm loving the browser.

I decided to try out some themes, decided I didn't like them, and went back to the default theme which I like.

Now though, the right click menu of the mouse doesn't actually load a theme - similar to when a program that needs root privilages (Synaptec package manager for example) won't be skinned unless you put a theme folder in the .root directory.

I've attached an image of the right click menu.

Does anyone know how to get Opera to load the Gtk (I think) theme or inbuilt theme for context menus?

I've tried removing/reinstalling, but it didn't work :(

Edit: Just noticed - buttons, and windows inside opera, aren't being themed either.

So it seems anything that requires themes outside of Opera's main window won't work.

---

### Post by mechro on 2010-01-14
This is one of the problems of Opera in Linux and the solution seems to change every so often after an Opera upgrade.

Currently I solve this problem by installing **qt3-qtconfig** via synaptic and fiddle about with the settings.

---

### Post by TyrantWave on 2010-01-14
Hmm.. I've tried pretty much every option for qt3 and qt4, yet it's still giving me ugly menus =/.

This really suck, is there no reliable way to get native Qt to display properly under Gtk?

---

### Post by mechro on 2010-01-14
I guess you're right about the ugly menus. I just change the colour and font to match but the effect doesn't quite match the main Opera skin.

The main Opera skin doesn't include the menubar so I'm afraid you have to learn to live with the kludge.

---

### Post by Symod on 2010-01-25
You need to download qt4 version [here]("http://linux.softpedia.com/progDownload/Opera-Download-271.html") (for some idiotic reason, the official Opera page offers only qt3 version), which picks up the correct theme, and go to Tools -> Appearance, choose Opera Standard skin and System Color scheme. It looks absolutely great after that.

EDIT: I just saw you tried qt4, and still have problems. Weird, it worked for me. Hopefully, 10.05 will put a stop to this.

---

