---
title: "failed attempt to install lexmark printer driver"
date: 2012-08-29
forum: General Help
---

### Post by bertmung on 2012-08-29
I tried to install a lexmark printer driver on 12.04. The latest available version was for 10.04 so that should have clued me that I was headed for trouble.

Now the update application and software center are broken. I have a red disk with a white horizontal stripe across it at the top of the display. Clicking on it gives the following error message:

```
An error occurred, please run Package
 Manager from the right-click menu or apt-get
 in a terminal to see what is wrong. The error
 message was: 'Unknown error: 
'<type' exceptions.SystemError'>' 
(E: The package lexmark-inkjet-legacy-wjre 
needs to be reinstalled but I can't find an
 archive for it.)'. This usually means your 
installed packages have unmet dependencies
```

As far as I can tell Package Manager isn't available from the right-click menu. I've tried running apt-get but I don't know what I need to do with apt-get to solve the problem.

---

### Post by CaptainMark on 2012-08-29
usually to correct unmet dependencies the command is ```
sudo apt-get install -f
```i think, im sure if im wrong the correct code will be quickly posted here

---

### Post by bertmung on 2012-08-29
> **CaptainMark said:**
> usually to correct unmet dependencies the command is ```
sudo apt-get install -f
```...

Tried it. I get the error message about not being able to find the archive for lexmark-inkjet-legacy-wjre. I think what I need to do is get rid of lexmark-injet-legacy-wjre and learn to live without using this particular printer.

---

