---
title: "One of the only reasons Linux/Firefox isn't hacking it"
date: 2010-04-30
forum: General Help
---

### Post by ndroftheline on 2010-04-30
Integration between Firefox and Ubuntu is bad. Not that any other browser is well-integrated in this way, mind you - but its really annoying with freakin' firefox.

When I go to try and open a document - almost any kind of document, but in this example a .docx document, firefox only gives me one option to open it with: Microsoft Office Word. Or, I can just "Save" the file, and open it manually. I shouldn't have to do that, and I'm pretty sure it was working at some point. I have Office installed via PlayonLinux and it runs fine. But in this case, I have 2003 and Openoffice seems to support docx better than 2003. So I'd like to open docx's with openoffice. But it's not an option on the "Open With" radio button in the firefox download prompt. I can click "Browse" but, because I'm still a fairly novice user, I don't know where the openoffice.org executable is located (partly because of the cryptic names of the directories...bin, sbin? etc? these aren't well named for novice users.) Even when I choose soffice.bin, it won't open. I can open it manually but it won't do it straight from the browser. gah!
Also, when I right-click a .docx in nautilus, and select "Open With", it gives me "Openoffice.org, MS Excel, MS Excel, MS Excel, MS Excel, MS Excel, MS Excel." It says MS Excel like 15 times; as much as I'd like to believe that M$ actually MADE their product act like a VIRUS and replicate its entry a zillion times, I don't. What's going wrong here and how do I remove the duplicate entries in the "Open with" box?

I'm going crazy over this! Dammit, I don't want to have to switch back to my win7 partition!

~Micah

---

### Post by cogier on 2010-04-30
If, while in Nautilus, you right click on the offending file and select **Properties>Open with** you should be able to choose which programme opens the file.

---

### Post by lovinglinux on 2010-04-30
The correct path is /usr/bin/soffice

---

