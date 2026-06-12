---
title: "HOWTO install ubuntu on HP Pavilon ze4805us"
date: 2011-03-24
forum: General Help
---

### Post by LewisGNoa on 2011-03-24
[CENTER][LEFT][FONT=Book Antiqua][SIZE=3]This will be my guide on  installing Ubuntu 10.04 LTS on the HP Pavilion ze4805. I dont know if  this will work on other HP Pavilion models. Note, Go to  System-->Preference-->Apperance got to the Visual Effects Tab and  turn it one None. Okay i dont exactly know how i did it, so i would  encourage comments telling which instructions do crap and more pointers,  as i am only 14, and when i say it doesnt work, it means it didnt work  for me. This requires a seperate pc with internet. Sorry, try a local  library. So here it goes:[/SIZE][/FONT]

[SIZE=2][FONT=Arial]Downlod and burn the alternate i[so file ]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download")[/FONT][/SIZE][here.]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download") [SIZE=2][FONT=Arial]Then go into windows or whatever distro you are using, and find out your IP, Gateway, and subnet. you cant find you[r IP ]("http://www.whatismyip.com/")[/FONT][/SIZE][here. ]("http://www.whatismyip.com/")So if you did format your drive, but tried to have an OS installed [go to here]("http://www.puppylinux.org/").  Now, GRUB wont boot if the hd wasnt previously formatted (i know its  weird, but it works like that.) So, with Windows, go to "My Computer" or  "Computer" and Right Click on your Hard Drive, usualy C, and click  format. Alternately, which i encourage, go to puppy linux <a  href="http://www.puppylinux.org"/>here</a>, download it, and go  to live cd. It is the only thing i found that actually boots into live  cd. So once in it go into the terminal, and type ```
fdisk  /dev/sda
```  press ```
p
``` when it asks to give a command,  you see some commands, and tpe ```
d
``` then 1 and repeat and  replace it with 2 then 3 etc. Boot from ubuntu alternate installer. Its  text-base, the web page gives a good howto but it isnt tht hard to  figure out. So, now you have installed ubuntu, but OH  NO!!!!!!!!!!!!!!!!!! The internet isnt working.To solve this prolem, go  to another computer. Now I then did this, and here is t[he original  article]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") All right, get this [cabextract]("http://security.ubuntu.com/ubuntu/pool/universe/c/cabextract/cabextract_1.2-3+lenny1build0.10.04.1_i386.deb") and [ndiswrapper here ]("http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download")download this file, r[ight here ]("ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe")then type this in terminal:
```
cabextract sp34152.exe
``` then ```
**[B]sudo ndiswrapper -i bcmwl5.inf**[/B]
``````
**[B]ndiswrapper -l**[/B]
``````
 **[B]sudo depmod -a**[/B]
``````
**[B]sudo modprobe ndiswrapper**[/B]
``````
**[B]sudo cp /etc/network/interfaces /etc/network/interfaces.orig**[/B]
``````
**[B]echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces**[/B]
```[B][B]
```
**[B]sudo ndiswrapper -m**[/B]
```**[B]```
[B][B]echo 'ndiswrapper' | sudo tee -a /etc/modules**[/B]
```**[B][B][B][B][B][B][B][B][B][B][B]```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```**[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B] Make it permanent like this: ```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```Now,  reboot, not from the Power Button though!! Plug in a wired Internet  chord. Now install go to System-->Admininstration-->Additional  drivers, or somethign like that, install, reboot afterward, and take out  the wired connection, then configure wlan0 or something, maybe its  automatic, and you can connect to the WiFi internet. :popcorn: 

[SIZE=3][FONT=Arial Black]Why did i do this, well, because   i had so much trouble with it, and i would like to share. This was all  done on my grndparent's pc, who upgraded to win7, and this pc was the  weakest link (xp), so i did the above instructions. Also, i am having  problems with the win7 theme, which i will post on a different thread,  and mac4lin ooks great, but it slows it done. Stick to the default  desktop.[/FONT][/SIZE] [/LEFT]
[/CENTER]

---

### Post by LewisGNoa on 2011-03-25
Oh yeah if it seds errors at boot, your fine. As long as it doesnt say grub error>
and you can type in it like a terminal. Then you have a problem or didn't previously format your hd

PS don't use Unity

---

