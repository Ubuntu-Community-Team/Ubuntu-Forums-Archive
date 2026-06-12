---
title: "Ubuntu and XP"
date: 2009-12-02
forum: General Help
---

### Post by lupeatx on 2009-12-02
Newbie here.

[B]I have two drives one with XP and another with Ubuntu 9.10. Now i'm trying to dual boot from them. I found a way to do it but i'm stuck on something.

 I already did all this but when I turn reboot my comp it loads straight to Ubuntu. All I see is *Grub loading *flash real quick and loads. Did I do something wrong?[/B]

You will need to edit your menu.lst file:
(Open a terminal, copy & paste one line at a time, press "enter" each time)

     Code:
     cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst 
The first line changes to the grub directory, the second line makes a backup of your menu.lst file, and the third line opens the menu.lst file using the gedit text editor.

Copy and paste the following lines above the line
###BEGIN AUTOMAGIC KERNEL LIST

     Code:
     title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1 

**Now when I first did this I actually entered the number 1 instead of L. Not sure if this causes the problem. I already went back and did it correctly. **

cd /boot/grub
sudo cp menu.[COLOR=Red]**1**[/COLOR]st menu.[COLOR=Red]**1**[/COLOR]st_backup
gksudo gedit menu.[COLOR=Red]**1**[/COLOR]st

---

### Post by Leppie on 2009-12-02
Karmic uses GRUB2, which in turn does not use menu.lst but grub.cfg.

Have a look at the [GRUB2 guide]("http://ubuntuforums.org/showthread.php?t=1195275").

---

### Post by lupeatx on 2009-12-03
Nothing on dual boot. Will search some more and see if there is something out there that can help me out.

Thanks!
:D

---

### Post by oldfred on 2009-12-03
Did you upgrade from 9.04, if so you have grub legacy. If you installed directly from a Karmic liveCD you have grub2.

Since you found a menu.lst you must have updated, since grub2 does not use that file?

If you used 1 not l it the copy should have said file not found? And the edit would have opened a blank file. Normally you can copy and paste the commands to avoid errors.

---

### Post by zman121 on 2009-12-03
/boot/grub/menu.lst is the instructions for grub at boot time.

Can you post the results of

     cat /boot/grub/menu.lst

?

It sounds like you have a default statement, and no time delay to allow choosing another option

Here's a vanilla RedHat grub menu.  My comments AFTER a ';'

default=0       ; means option 0 is the default
timeout=5      ; critical -- means wait 5 seconds to allow user to override
splashimage=(hd0,0)/grub/splash.xpm.gz     ; the splash screen to use.
hiddenmenu                        ; don't show the menu unless the use presses a key
title Red Hat Enterprise Linux Server (2.6.18-120.el5)     ; implicit option 0
        root (hd0,0)
        kernel /vmlinuz-2.6.18-120.el5 ro root=/dev/VolGroup00/lvRoot nodmraid rhgb quiet
        initrd /initrd-2.6.18-120.el5.img




Hope this helps

---

### Post by lupeatx on 2009-12-03
I installed 9.10 from livecd to a blank HD and yes it did say file not found when I did it both ways.

Here is what I get when I enter [I]cat /boot/grub/menu.lst


lupe@lupe-desktop:~$ cat /boot/grub/menu.lst
title              Windows XP
noverify           (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
### BEGIN AUTOMAGIC KERNEL LIST
lupe@lupe-desktop:~$ 

[/I]After I posted my last reply a window popped up stating something about new updates. After that I restarted my comp and grub screen came up. When I choose to boot into XP it gives me an error.

*error : invalid signature*

What's going on now? :(

---

### Post by oldfred on 2009-12-03
You can delete the menu.lst you created. You have grub2. You should be able to just rerun the update. Grub2 is very good at finding other working installs. Which drive are you booting from?
```
sudo update-grub
```

If that does not work, this will document you boot process:

Boot Info Script 0.37 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions
  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

cd to directory saved to: 
chmod 755 boot_info_script037.sh 
sudo ./boot_info_script037.sh 

or as example if on desktop from liveCD download 
sudo bash ~/Desktop/boot_info_script*.sh 

This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by lupeatx on 2009-12-04
Right now I have the Ubuntu as master and XP slave. Will do everything tomorrow and post what I came up with.

---

### Post by lupeatx on 2009-12-04
So i solved it.
[B]
my disk with windows and Ubuntu is /dev/sdb[/B]

```
sudo gedit /boot/grub/device.map
```**(hd0)    /dev/sda     _change to_****       (hd0)    /dev/sdb**

save

then

```
sudo os-prober
sudo update-grub
sudo reboot 
```

---

