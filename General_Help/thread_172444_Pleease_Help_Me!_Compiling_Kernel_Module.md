---
title: "Pleease Help Me! Compiling Kernel Module"
date: 2006-05-08
forum: General Help
---

### Post by Gonzakpo on 2006-05-08
Hi everuyone, first i wanna sya that i speak spanish so if you don't understand my english, thats the reason! :S

Ok, let's start. I want to instal a fu****** network adapter (DLINK DFE-520TX) drivers because ubuntu didn't detected it when i was installing the distro (ubuntu 5.10).

Well, i downloaded the drivers but when i tried to compile i noticed taht the make command whas missing, so i installed it from the ubuntu cd.
Then it tried again to make the install of teh drivers and the make command said that i the gcc-3.4 was missing...

OKKKKKKK....i search it in another computer (thru internet) and i burnt the compiler in a cd and installed it in the lovely ubuntu (i'm a little upset!) 

Yeah! i tought it was my moment of glory........but NO......when it was compiling several erros ocured .......
(i can't copy the entired console text because i don't hace a program to burn cds in that machine and my floppy isn't working and, of course, I CAN'T USE INTERNET!!) 
well....the errors are:

pci_save_state -------> TOO MANY ARGUMENTS
pci_restote_state ------> TOO MANY ARGUMENTS

and the last one i will write it entired (i'm copying then from a sheet of paper ....i printed it :S)

IN FUNCTION ´rhine_ethtool_ioctl´: error: structure doesn´t hace a member called ´slot_name´


welll....that were all the problems ...
ANOTHER THING I FORGOT TO SAY...........i'm a linux newbie sooo...pleeease try to help meee with this.....once i have internet in the linux machine all is going to be muuuuuuuuch easier for me!!! ..i realy want to learn how to use it PROPERLY! 

i want to mention also that i looked everywhere!! ...but i didn't found nothing.......except one guy in another forum that said that the arguments of pci_save_state and the pc_restore_state ...could be solved by deleting their second argunment becuase it isn't needed.....BUUT....I'M NOT SURE.....I DON'T WANT TO BURN OUT MY NETWORK ADAPTER...
and...anyway ....i have the other compiling error :s


ok....i don't know if you need it but i'm going to upload the drivers to a rapidshare server...
here is the link...

[http://rapidshare.de/files/19974431/dlkfet-4.39.tar.gz.html](http://rapidshare.de/files/19974431/dlkfet-4.39.tar.gz.html)

the linux.txt is a description of how to compile the source ...
and the rhino_main.c ....is the one with the compiling problems


I KNOW THAT I'M ASKING TOOOOOO MUCH....BUT PLEEASE HELP MEEEE....I REALLY NEED HELP....I'M GOING CRAZYYYYYYYYYYYYYYYY

THANKKKSSS....(AT LEAST FOR READING! :) )

---

### Post by Gonzakpo on 2006-05-08
loook! ---this guy has my sameee problem....same errorss! ..(but under suse)

[http://forge.novell.com/modules/xfmod/newsportal/article.php?group_id=1459&msg_id=666&group=novell.support.suse.linux.standard-server](http://forge.novell.com/modules/xfmod/newsportal/article.php?group_id=1459&msg_id=666&group=novell.support.suse.linux.standard-server)


HEEEEEEEEEEEEEEEEEEEEEEEELP :´(

---

### Post by Gonzakpo on 2006-05-08
[http://www.linuxforums.org/forum/linux-networking/49511-struct-pci_dev-has-no-member-named-slot_name.html](http://www.linuxforums.org/forum/linux-networking/49511-struct-pci_dev-has-no-member-named-slot_name.html)


looooook what i found!!....do you think it might work?????

please heeeeeeelpp
i¿m waiting for a linux guru answeeeeerrrrrr

---

### Post by Gonzakpo on 2006-05-08
i find the first fixxxx.....i thing (i didn't try it yet) but i'm pretty sure

+            /*strcpy(info.bus_info,pInfo->pcid->slot_name);*/
+            strcpy(info.bus_info,pci_name(pInfo->pcid));

thats one of the changes i hace to do! 

.....pci_save_state! ...i'm coming to youuuuuuuu MUAJAJA

(this is driving me crazy!)

---

### Post by Gonzakpo on 2006-05-08
i found the other fixeeees

here is the lines i have to "patch"

[http://www.big-bubbles.fluff.org/scripts/rhine_main.patch](http://www.big-bubbles.fluff.org/scripts/rhine_main.patch)

Welll...now i'll will try to post thru my linux computerrrr! :) 
i hope it works!

i'll let you know if it work...

I'M TALKING ALOOOONE!

---

### Post by Gonzakpo on 2006-05-08
nooooooo
i couldn'ttt

pleaaaase help !

---

