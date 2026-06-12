---
title: "need help uninstalling linux ubuntu 9.04"
date: 2009-07-13
forum: General Help
---

### Post by omfgkrzy on 2009-07-13
okay so seriously ive been up four or five days trying around terminals , command prompts , booting sequences , d/loadable programs , f disk , system setup , and everything okay and nothing works wat soever the grub wont let me access the windows partitions or anything  i want to unistall because everytime i try to download anything such as a fps game i play or ventrilo or anything at all it wont download it gives me some dumb error

[/home/kyle/Desktop/ventrilo-3.0.5-Windows-i386.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/kyle/Desktop/ventrilo-3.0.5-Windows-i386.exe or
          /home/kyle/Desktop/ventrilo-3.0.5-Windows-i386.exe.zip, and cannot find /home/kyle/Desktop/ventrilo-3.0.5-Windows-i386.exe.ZIP, period.


i just want to uninstall and go back to Windows xp , if anyone can help please reply before i throw my computer out the window and break every last peice of it.

---

### Post by nothingspecial on 2009-07-13
Well before you throw it out of the window, what are your problems?

As this is your first post I take it you`ve not asked for any help yet.

---

### Post by omfgkrzy on 2009-07-13
well i cant uninstall through the restart boot menu i cant delete partitions then reboot menu to windows i cant run anything in terminal to reset my system back to windows i just want to completely remove ubuntu 
i cant download anything becuase it always gives me the same error and nobody knows how to remove linux completely from my comp

---

### Post by bigken on 2009-07-13
boot from your windows xp cd when you see the prompt hit R to enter repair console 
select your windows partition usually 1 hit enter twice for the admin password unless you use a 
admin password then type fixmbr enter fixboot enter last of all type exit you should now boot back into windows in windows use system managment to delete and format the linux partitions

---

### Post by nothingspecial on 2009-07-13
Load up the live cd you installed ubuntu with.

Go system > administration > partition editor

Delete the ubuntu partition and increase the windows partition into the free space.

Put in your xp disk

choose fix or repair or whatever it is

type fixmbr at the prompt 

reboot

---

### Post by Pasdar on 2009-07-13
The file you're trying to run is a windows file, that is why you get the error. To get windows back in your grub list:

type **sudo gedit /boot/grub/menu.lst**

and add the following at the bottom of the list and save the file.

> title Windows XP
rootnoverify 		(hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

You now restart and select Windows XP at menu... however the above could differ a bit in your case, just try it out to see if it works.

---

### Post by omfgkrzy on 2009-07-13
it doesnt show a partition editor in system>admin>

---

### Post by Pasdar on 2009-07-13
> **omfgkrzy said:**
> it doesnt show a partition editor in system>admin>

Maybe you don't have it installed, try install **gpart** from package manager

---

### Post by nothingspecial on 2009-07-13
You have to do it from the live cd.

You can`t delete a partition you are using.

---

