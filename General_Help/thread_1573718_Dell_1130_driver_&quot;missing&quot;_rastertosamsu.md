---
title: "Dell 1130 driver &quot;missing&quot; rastertosamsungspl"
date: 2010-09-13
forum: General Help
---

### Post by ep1centre on 2010-09-13
Hello, 

I am yet again having the simplest of problems yet my lack of linux (ubuntu) knowledge lets me down...

I've recently bought a laser printer Dell 1130 and now I'm trying to get it to work with my Ubuntu machine but not having much luck.

So i do all the normally things to add a printer via the wizard thingy, but it doesnt find a driver for it automaticly so i downloaded the tarball from Dell's website and i browse for it to chose the driver myself, all very well to this point i find the right driver and everything it accepts it with no problems but then it comes up with an error which says:

"Missing Driver

Printer 'Dell-1130-Laser-Printer' requires the 'rastertosamsungspl' program but it is not currently installed.  Please install it before using this printer."


so i start searching for this rastertosamsungspl driver and i find it in the same folder that i got from dell i also found that its soposed to go in usr/lib/cups/filter so the next logical step for me was to copy and paste it ... well guess what it wont allow me apparently i haven't got the right permissions or something to paste into that folder, i've tried changing my account to an admin account and what not but no luck... can anyone give me a hand getting this printer going please?


thank you!

---

### Post by ep1centre on 2010-09-14
Any ideas?

---

### Post by anglican on 2010-09-14
> **ep1centre said:**
> 
so i start searching for this rastertosamsungspl driver and i find it in the same folder that i got from dell i also found that its soposed to go in usr/lib/cups/filter so the next logical step for me was to copy and paste it ... well guess what it wont allow me apparently i haven't got the right permissions or something to paste into that folder, i've tried changing my account to an admin account and what not but no luck... can anyone give me a hand getting this printer going please?

thank you!Open a terminal and type:
```
sudo cp <full_path_to_program>/rastertosamsungspl /usr/lib/cups/filter

```where you change <full_path_to_program> to the directory in which you found rastertosamsungspl.

H

---

### Post by ep1centre on 2010-09-14
hi anglican, 

thanks for the reply, i tried what you sugested but no luck... i pasted the file on the desktop for the sake of ease but i must be typing the path wrong, can you just confirm if this is how the command would look with the file on my desktop.

sudo cp /ertech1/desktop/rastertosamsungspl /usr/lib/cups/filter

i've also tried:

sudo cp /desktop/rastertosamsungspl /usr/lib/cups/filter

no luck eitherway it just tells me "no such file or directory"

---

### Post by TBABill on 2010-09-14
Is it desktop or Desktop? Verify the name of the folder it is in and verify the case (upper or lower) of all folders in the path you are referring to.

---

### Post by ep1centre on 2010-09-14
Well spotted! 

that worked a treat!

for the record in case anyone finds this thread on a random search about this problem, all you have to do to install this printer is follow the wizard, it wont find the drivers automaticly so browse for the ppd file which is in:

/cdroot/Linux/noarch/at_opt/share/ppd

then search the same folder (cdroot) for rastertosamsungspl copy and paste on your desktop the 43.2KB file (NOT the 55.3KB one - for some reason it didnt work for me)

then go to terminal and use the following command:

sudo cp Desktop/rastertosamsungspl /usr/lib/cups/filter


about the references i make to "cdroot" this is a folder you get from dell's own website, its pretty easy to get hold of and this should work as long as they dont change the file.

worked for me, my Dell 1130 now works perfectly!!!

---

### Post by catmandog on 2011-05-20
[FONT=monospace]Rastertosamsungpl

I found delete the printer and reinstall printer 

Just like i used to do in windows fixed the issue. 

give it a try. 
[/FONT]

---

### Post by hm_shurt on 2012-06-04
On a similar note, I used the Samsung Unified Driver Configurator, and it put the rastertosamsungspl in the /usr/lib directory and then there were problems because the system (CUPS on Gentoo) was looking for it in the /usr/libexec directory.  Took me a while to figure that one out.

---

