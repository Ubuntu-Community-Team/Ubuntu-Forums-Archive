---
title: "/bin/sh: can't access tty; job control turned off"
date: 2006-05-12
forum: General Help
---

### Post by cocox on 2006-05-12
:cool: hi guys i've some problems after make my upgrade from Hoary to Breezy.... (i did all the steps following the tutorial that i 

found here in the forum...) i probed that my upgrade was succesfully done! i executed the command for look your distro and 

etc... etc... everything was fine ... 

1. I turn off my pc and when i turn on again my grub menu.lst was edited so i entered in a rescue mode and fixed it... 

2. the system prompts the login screen and i just could type numbers from the calc of the keybord .. but any vocal and 

consonant (A,B,etcc duhhh!!) weird isn't it ??? I try changing my keyboard language etc etc..

3. So.. i rebooted my pc again and when the BIOS was loading my harddrive just get freezed in the black screen where show us 

the amount of ram and speed of bus, IDE devices etc.... 

4. I thought that my HD was screw... but i made a last try i switched my flags and IDE of my CDROOM and HD and take off the 

pill and it again in my board... restart... configure the BIOS with the default values and...

5. the Grub menu was displayed!! nice nice... :twisted: i cant enter to windows but when i try to enter to my Ubuntu i get this message 

and the system shows me a shell waiting for my commands jeje....

this is what i see when i press "e" over the selected ubuntu menu in grub...

--------------------------------

root(hd0,1)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-386
save default
boot

-------------------------------

this what appears after i press enter over that menu...

-------------------------------

BusyBox v1.00-Pre10(Debian20040623-1Ubuntu22) built-in shell (ash)
/bin/sh: can't access tty; job control turned off
#/bin/sh:(here is the cursor waiting for some commands:mrgreen: )

------------------------------

6. I tried to mount my /dev/hda2 over /mnt dir from that shell... but i got this message[-( 

------------------------------

"No such file or directory"
and
"no such device"

-----------------------------

can anybody help me plzzz](*,) ](*,) ](*,)

---

### Post by cocox on 2006-05-14
hi everybody,

i didn't realize but after the upgrade from Hoary to Breezy, my fdisk table changed...

now when i do this "fdisk -l" all my partitions are in "hdc" ... before the upgrade they were in "hda" (i have just one disk...hdaX)

so... i just changed my /boot/grub/menu.lst pointing to my "hdc2"..... and well now i can boot Ubuntu... :rolleyes: 

but when im on the Login screen i just can type numbers(from the keyboard calc, and well the BloqNum and CapsLock keys).... my keyboard is allrigth because when i get into the shell pressing ALT + CTRL + F1 my keyboard is perfectly Ok! i can log into the system and do everything... so the problem is just when im on the graphical mode... 

any idea?? and by the way is there any way to fix this bug of the change of chracteres in the harddisk nomenclature?? (hda,hdc, etc...):mrgreen: 

i allready check another posts... many people have the same problem but nobody post a solution... plz help meeeee!!:p

---

### Post by cocox on 2006-05-15
i fixed my keyboard problem in the Xgraphic mode:mrgreen: 

i did this...

access to the console ALT + CTRL + F1
1. sudo dpkg-reconfigure xserver-xorg

with this command you'd be able to configure manually your settings for the X enviroment (graphical mode)
i screw up my graphical mode in this step haha i put some wrong information... the system shows me a blue screen with an error message hehe ;)  ( in my case i had to screw my graphical mode for fix this bug....)
reboot

2. sudo dpkg-reconfigure -phigh xserver-xorg
CTRL + ALT + F7

and surprise!! :mrgreen: 

now i have to resolve my problem with the switch of my HD nomenclature (hda to hdc)

gL

---

### Post by cocox on 2006-05-15
Did I tell you that I changed my HD IDE with the cd-room IDE ??

Look at this table…

hda - First active IDE channel (detected by Ubuntu) Master device

hdb - First active IDE channel (detected by Ubuntu) Slave device

hdc - Second active IDE channel (detected by Ubuntu) Master device

hdd - Second active IDE channel (detected by Ubuntu) Slave device

so, if I put my HD in the “Second active IDE channel” (Master device) it’d be now “hdc”

this is the answer why the nomenclature of my drive changed….

I hope all this post can help anyone somewhere!!!!

Now everything is fine

LOCKED!! W0000thhh:KS

---

