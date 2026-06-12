---
title: "Lost Gui after a proprietary video driver install"
date: 2011-12-24
forum: General Help
---

### Post by Mrmazz on 2011-12-24
i've tried to install a video driver for my laptop and ended up without gui

what i've done:

ctrl+alt+f1

```
sudo service lightdm stop

chmod +x NVIDIA-Linux-x86_64-290.10.run 

sudo ./NVIDIA-Linux-x86_64-290.10.run
```

after the install i didint turn the lightdm on again, but i typed

```
sudo shutdown -h now
```


i turned my laptop on, and there was no gui, so i went back to the terminal with ctrl+alt+f1 to turn lightdm on

```
sudo service lightdm start
``` 

with an output:
lightdm start/running, process 4104

then i tried to come back to the gui with the ctrl+alt+f7 , but it still the same way as it was.




what i've tried so far:

uninstall lightdm, reinstall

uninstall lightdm, install gdm


when i tried to start gdm with 

```
sudo service gdm start
```

, the screen flashes between gui and terminal, ending up again in the terminal with an output like "gdm start/running,process 4151"



could anyone help?

---

### Post by Mrmazz on 2011-12-24
i also tried 

```
sudo dpkg-reconfigure xserver-xorg
```

but it wont return anything

---

### Post by mystika1 on 2011-12-24
I install my drivers the debian way but some prefer to use drivers from the nvidia site. I found that using the following program automatic installs the newest drivers for ati/nvidia cards. 

> cd /usr/local/bin && wget -O sgfxi smxi.org/sgfxi && chmod +x sgfxi && sgfxi 

Enter the above at the command prompt(it should install the program and run it..if it installs but doesn't run type 
> sudo sgfxi
 and answer a few yes or no questions and you are done. The only down side to using drivers from the nividia site is that every time the kernel is updated you will need to reinstall the drivers. 

More info about sgfxi can be found here...
[http://smxi.org/docs/sgfxi-manual.htm](http://smxi.org/docs/sgfxi-manual.htm)
scroll down the page a bit to get to the section on sgfxi.

Penny

---

### Post by Mrmazz on 2011-12-24
Just tried

after download and install i answered 

 2)start-desktop

didnt work

it just got back to the page with many "[ok]"'s


there is a [fail] in stopping automatic crash report generation

---

### Post by mystika1 on 2011-12-24
Hi,
Last time I used the script I had to do it twice because it asked me a question about which driver to install and I didn't answer correctly. Just suggesting that you 

> sudo sgfxi

again just in case. :) I wish the script wouldn't run in color cause it makes it hard to see sometimes. Also...start-desktop never worked for me. I always had to reboot for it to work.

Penny

---

### Post by Mrmazz on 2011-12-24
tried it again, and rebooted,


not working


it's a new laptop, i will just backup important stuff and format


then i'll use that sgfxi you suggested,

thanks

---

### Post by Mrmazz on 2011-12-24
Just formatted and ran what you said
but...


[COLOR="Red"]FAILED [/COLOR]

[COLOR="Cyan"]Error removing[/COLOR] [COLOR="Magenta"]noveau[/COLOR] [COLOR="Cyan"]module for pre-install cleanup operation.
Please investigate this further since it may make your nvidia driver install fail[/COLOR]

[COLOR="Blue"]Adding[/COLOR][COLOR="Magenta"]/boot/grub/grub.cfg /etc/default/grub nomodeset/nouveau.modset=0[/COLOR] [COLOR="Blue"]for[/COLOR] [COLOR="Magenta"]nouveau[/COLOR] [COLOR="Blue"]blacklist items....Added[/COLOR]

[COLOR="blue"]Adding[/COLOR][COLOR="Magenta"] /etc/default/grub nouveau.modset=0[/COLOR] [COLOR="blue"]for[/COLOR] [COLOR="Magenta"]nouveau[/COLOR] [COLOR="blue"]blacklist items ....Added [/COLOR]

[COLOR="Blue"]Creating[/COLOR] [COLOR="Magenta"]/etc/modproble.d/kms-sg-blacklist.conf nouveau blacklist[/COLOR] [COLOR="Blue"]item...[/COLOR]
[COLOR="Blue"]Running[/COLOR] [COLOR="Magenta"]update-initamfs -u[/COLOR] [COLOR="blue"]to remove Nouveau/Radeon from initrd...[/COLOR]

update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic




and freezes

can't go back to gui
or go back to tty1 or tty2...

that report may contain some typing errors since i just handwrote it all



It doesn't even boot anymore


ok
what now

---

