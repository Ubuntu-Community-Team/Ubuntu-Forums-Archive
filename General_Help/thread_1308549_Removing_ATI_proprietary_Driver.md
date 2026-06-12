---
title: "Removing ATI proprietary Driver"
date: 2009-10-31
forum: General Help
---

### Post by Gosport on 2009-10-31
How do I uninstall an ATI proprietary driver.  I will probably have to do this in the terminal because past a certain point my monitor says "out of range" and I can't see anything.

I am a bit of a noob so I need a little hand holding, but I have used the terminal before.  

I don't know if it will do any good but I found the info below from [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat84-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat84-inst.html)

**[FONT=Verdana][COLOR=#003c28]Uninstalling the ATI Linux Proprietary Graphics Driver [/COLOR][/FONT] **

      [FONT=Verdana][SIZE=2]Un-installing the ATI Linux Proprietary Driver is dependent on the mode of initial installation.[/SIZE][/FONT] 
   **    [FONT=Verdana][COLOR=#003c28]Automatic or Custom Driver Installations [/COLOR][/FONT] **

      [FONT=Verdana][SIZE=2]If the ATI Proprietary Linux Graphics Driver was installed using either the Automatic or Custom options, then do the following:[/SIZE][/FONT] 
  
[LIST=1]
[*] [FONT=Verdana][SIZE=2]Launch the Terminal Application/Window and navigate to the [FONT=Verdana][SIZE=2]/usr/share/ati[/SIZE][/FONT] folder.[/SIZE][/FONT]
[*] [FONT=Verdana][SIZE=2]With super user permissions, enter the command "sh ./fglrx-uninstall.sh"[/SIZE][/FONT]
[/LIST]
      [FONT=Verdana][SIZE=2]You have now successfully uninstalled the ATI Linux Proprietary Graphics Driver.[/SIZE][/FONT] 
   **    [FONT=Verdana][COLOR=#003c28]Package Generation [/COLOR][/FONT] **

      [FONT=Verdana][SIZE=2]If the initial installation of the driver was done via the Operating Systems package management software (rpm, apt, etc.) then please use that package management software to remove the ATI Proprietary Linux Graphics Driver.[/SIZE][/FONT]

---

### Post by Gosport on 2009-11-02
OK, the answer to my own question is to borrow an old CRT monitor (or possibly just any other monitor) and you may be able to see well enough to use the regular menu options to remove the proprietary driver.  I'm just glad that I didn't have to reload the operating system again.

---

### Post by Zoot7 on 2009-11-02
Open up the terminal and do:
```
sudo apt-get remove --purge xorg-driver-fglrx 
```
-Enter your password and hit Enter.

That'll get rid of any installed packages relating to the ATi Driver.

```
   1.  Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.
   2. With super user permissions, enter the command "sh ./fglrx-uninstall.sh"
```
to do that in the terminal run
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```

Also what version of Ubuntu are you using and what ATi card have you?

---

### Post by Gosport on 2009-11-02
I have an onboard ATI Radeon HD 4200 and am running the 64 bit version of Karmic.  I installed the proprietary driver via the menus but my monitor reports "out of range".   At this point I have reset the non-proprietary drivers and have given up on enabling 3D capabilities.  Things work fine in 2d but would like to someday enable 3D.

Someone else suggested this link but I have yet to try: [http://nickhumphrey.net/showthread.php?p=3345](http://nickhumphrey.net/showthread.php?p=3345)

(From this post: [http://ubuntuforums.org/showthread.php?t=1281846&page=2](http://ubuntuforums.org/showthread.php?t=1281846&page=2))

---

### Post by Zoot7 on 2009-11-02
Try out the guide posted here, it's pretty comprehensive and it walks you through a package based install along with the necessary tweaks to have a much more stable driver install:
**[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")**
Granted it's for Jaunty but the only thing to change is just to use the option --buildpkg Ubuntu/karmic so the line 
```
sh ati-driver-installer-9-7-x86.x86_64.run --buildpkg Ubuntu/jaunty 
```
would become
```
sh ati-driver-installer-9-7-x86.x86_64.run --buildpkg Ubuntu/karmic 
```

This method is what's always worked for me with my HD4870, although I'm get to try out Karmic.

---

### Post by Gosport on 2009-11-02
Thanks for the information!

---

