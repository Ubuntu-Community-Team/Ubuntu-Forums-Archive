---
title: "How can i change Grub Menu?"
date: 2006-05-02
forum: General Help
---

### Post by Anilkumar on 2006-05-02
Hello Everybody,

Thanks for the support u are providing in this forum.
Now i need a small help to change grub menu. My question is

How can change the position of windows xp so that my default login can be windows. plz fix me and also i want to get rid of the other ubuntu options i want to have only ubuntu ,windows xp , safe login

with kind regards help me 
anil

---

### Post by DeathCarrot on 2006-05-02
you need to edit /boot/grub/menu.lst ('gksudo gedit /boot/grub/menu.lst' or 'sudo vi /boot/grub/menu.lst' in a terminal for example), just cut/paste the windows section to the top, and as for getting rid of selections, you can comment them out with a # at the start of each line :)

---

### Post by MenZa on 2006-05-02
Try doing a such on the fora, there's some application which enables you to easily -- with a GUI -- to change everything in your GRUB config.

---

### Post by mcduck on 2006-05-02
[QUOTE=DeathCarrot]you need to edit /boot/grub/menu.lst ('gksudo gedit /boot/grub/menu.lst' or 'sudo vi /boot/grub/menu.lst' in a terminal for example), just cut/paste the windows section to the top, and as for getting rid of selections, you can comment them out with a # at the start of each line :)[/QUOTE]
If you do this, you'll have to do it again after every kernel update..

Better way is to set default to point to the number of the windows entry, but let the entry itself be where it is now.. I remember that the setting is somewhere before the actual entries in menu.lst file, you should find it if you just read through the file.. If you can't find it, I'll give better instructions when I get home to my Ubuntu box.. :)

edit: the line is like 'default    1', change the '1' to whatever is the number for your windows entry, or to 'saved' to make last used entry the default.

---

### Post by Anilkumar on 2006-05-02
Hello plz guide me

---

### Post by mcduck on 2006-05-02
Ok. First you need to open the grub configuration file for editing. To do this, open a terminal window (I have it un Applications/Accessories, but I think it was in Applications/System tools in breezy), type 'sudo gedit /boot/grub/menu.lst', and enter your password.

All the lines with a # in beginning are comments, they are just to help you. All the important lines are those without a #. Now find a line like 'default      0'. That's where you select which OS will boot by default. You'll have to take a look at how many separate entries you have, and which one is windows. Most likely the first 2 are Ubuntu entries, and then there's memtest, and after that would be your windows. The first entry is number 0, second is 1 etc. So if windows was the 4th entry you have, change that 'default'-line to 'default   3', if it's sixth, use 'default    5'...

If you set the line to 'default     saved', grub will always default to the last used entry (if the entry has a line with 'savedefault'), so after running windows your machine would boot to windows by default, and after running Ubuntu it will boot to Ubuntu by default.

After you're done with that, save the file. That's it :)

---

### Post by Anilkumar on 2006-05-03
Thank you
 i have changed the default boot.

---

### Post by sligh on 2006-10-27
Thank you mcduck .. It's just the info I was looking for. My wife don't do ubuntu! So I need XP as default in Grub to keep the peace..

---

### Post by Uncle Spellbinder on 2006-10-27
See here: [GrubEd](http://www.ubuntuforums.org/showthread.php?t=228104&highlight=GrubEd)

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/GrubEd.png[/IMG]

---

### Post by zgornel on 2006-10-27
GrubEd is pretty functional ;)

---

### Post by elettronicha on 2006-10-27
> **Anilkumar said:**
> How can change the position of windows xp so that my default login can be windows. plz fix me and also i want to get rid of the other ubuntu options i want to have only ubuntu ,windows xp , safe login

Please, read the guides or try a search, before posting! This is a FAQ!

This is a [link]("https://help.ubuntu.com/community/GrubHowto")

Bye.

---

### Post by jazzz337 on 2007-10-18
> **mcduck said:**
> Ok. First you need to open the grub configuration file for editing. To do this, open a terminal window (I have it un Applications/Accessories, but I think it was in Applications/System tools in breezy), type 'sudo gedit /boot/grub/menu.lst', and enter your password.

All the lines with a # in beginning are comments, they are just to help you. All the important lines are those without a #. Now find a line like 'default      0'. That's where you select which OS will boot by default. You'll have to take a look at how many separate entries you have, and which one is windows. Most likely the first 2 are Ubuntu entries, and then there's memtest, and after that would be your windows. The first entry is number 0, second is 1 etc. So if windows was the 4th entry you have, change that 'default'-line to 'default   3', if it's sixth, use 'default    5'...

If you set the line to 'default     saved', grub will always default to the last used entry (if the entry has a line with 'savedefault'), so after running windows your machine would boot to windows by default, and after running Ubuntu it will boot to Ubuntu by default.

After you're done with that, save the file. That's it :)

Thank man I realy need this info I was constantly missing the boat to chose which os to use.

ok this is probably common knowledge but at the line in the menu.lst that sets the number of secound before auto boot if you change the number to -1 the grub list will stay up indefinitly

---

