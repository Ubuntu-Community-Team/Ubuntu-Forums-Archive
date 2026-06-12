---
title: "Unable to Install new Fonts in 9.10"
date: 2010-02-17
forum: General Help
---

### Post by strange_cathect on 2010-02-17
After upgrading to 9.10, the fonts I had placed in my .fonts folder no longer function in any application.

I have tried to re-install them by just clicking on the font itself and going through the installation screen. But this doesn't do anything.

I have tried to delete and the re-create my .fonts folder in my /home partition. But that also fails.

Did Ubuntu do something different with user-installed fonts in 9.10? Should my fonts be relocated to another folder?

How can I install "after market" fonts?

Thanks for your help.

---

### Post by strange_cathect on 2010-02-17
For some reason, I HAD to place my fonts within /usr/share/fonts. Using the .fonts folder in my /home partition would not work.

Is there a bug report on this?

---

### Post by ajgreeny on 2010-02-17
In spite of the fact that I have always added fonts I want globally to /usr/share/fonts, I am pretty sure that they did work prior to that when just in ~/.fonts.

However, I did it so quickly after installation that I could be wrong, and perhaps the local /fonts folder system was not working as it should.

Do a search of launchpad and see if any bugs are reported.

---

