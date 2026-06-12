---
title: "Cannot find installed software"
date: 2009-09-12
forum: General Help
---

### Post by tatsuki on 2009-09-12
[COLOR=black][FONT=Verdana]Hi all[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Completely confused noob here![/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I recently downloaded and installed Opera browser 10 from there website in ubuntu 8.10 but can not find it in my main menu.:([/FONT][/COLOR]
[COLOR=black][FONT=Verdana]When I type sudo apt install opera it runs, but I can’t add it to my panel [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Can anyone tell me what the heck IV done?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]How can I fix this so I can add it to the panel?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thanks for any help[/FONT][/COLOR]

---

### Post by MelDJ on 2009-09-12
you installed the .deb? i think it will come under internet after a restart

---

### Post by tatsuki on 2009-09-12
[COLOR=black][FONT=Verdana]Thanks [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]IV tried that but still can’t find it[/FONT][/COLOR]
:(

---

### Post by howefield on 2009-09-12
Try running it from terminal. Open terminal, type opera and press enter.

Does it run ? or maybe return an error ?

---

### Post by tatsuki on 2009-09-12
yes
error ld.so:object`libjvm.so from ld_preload cannotbe preloaded ignored 
then after a few seconds it just opens opera
I guess I could just always open it this way, but i would like it in my panel

---

### Post by NoaHall on 2009-09-12
Try using "sudo ldconfig" and then try running it.

---

### Post by howefield on 2009-09-12
> **tatsuki said:**
> ...but i would like it in my panel

Well, you know it is installed and working.

If the icon hasn't appeared even after a restart, you could add it to your menu via System > Preferences > Main Menu

---

### Post by tatsuki on 2009-09-12
thanks hall 
 
i still get the cannot be preloaded error and after one or two seconds it opens 
Its there the browser opens but i just dont know how to add it to my panel.

---

### Post by NoaHall on 2009-09-12
Right click panel -> Add to panel -> Custom Launcher -> Add -> Under Command, put "opera", Name = Opera, comment -> opera -> Ok

---

### Post by tatsuki on 2009-09-12
[COLOR=black][FONT=Verdana]Its not in the main menu either[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR]

---

### Post by tatsuki on 2009-09-12
cool i will try that

---

### Post by tatsuki on 2009-09-12
:P
[COLOR=black][FONT=Verdana]That worked it’s on my panel now thanks hall[/FONT][/COLOR]
[SIZE=3][FONT=Times New Roman]Thanks to all that tried to help too.[/FONT][/SIZE]

---

