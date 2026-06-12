---
title: "Any way to freeze GRUB2 boot loader?"
date: 2010-09-30
forum: General Help
---

### Post by mp29k on 2010-09-30
I stupidly set the auto timeout on my dual boot machine to 1 second.  It will not allow me to select anything but the default option I had set, which is Windows XP.  I would love to be able to get back into Ubuntu, but I can't.

I tried logging in through a live CD I had for Xubuntu v9.1, but I was unable to successfully run "Startup Manager" to change the timeout back to 3+ seconds.

Please help.

-Kevin

---

### Post by sisco311 on 2010-09-30
Just hold down the SHIFT key during the bootup.

---

### Post by sikander3786 on 2010-09-30
Press and hold down the Shift key as soon as your PC gets past the Bios logo and then select Ubuntu. You already know about "Startup Manager" so changing the boot time back to 10 sec or x sec will not be too much difficult :-)

---

### Post by mp29k on 2010-09-30
I was quite excited for this simple/ elegant solution to work, but alas, it didn't seem to do anything.

I will try again I guess.

---

### Post by mp29k on 2010-09-30
Tried a second time, and still no luck.  Any other suggestions?

---

### Post by sisco311 on 2010-09-30
Boot a Live CD, mount the root partition (or the boot partition if you have a separate one), edit the <mount/point>/boot/grub/grub.cfg file and change the timeout:
```
...
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  **set timeout=10**
fi
### END /etc/grub.d/00_header ###

```
Reboot into Ubuntu and use StartupManager to change the timeout and generate a grub.cfg file.

---

### Post by sikander3786 on 2010-09-30
> **mp29k said:**
> Tried a second time, and still no luck.  Any other suggestions?
I've heard sometimes that Right Shift worked for someone and Left Shift for the others. Right Shift always works for me. Did you try with both the keys? If yes, then you need to follow **sisco311's **suggestions.

---

### Post by mp29k on 2010-09-30
Neither worked.

I logged into my machine using a LTS Lucid Lynx Live CD, but now it won't let me install startup manager, and it is absent from the applications list... guessing since i am running from the CD.

What now?

Sorry for asking such noobish questions, I just want by 'Buntu back!

---

### Post by sikander3786 on 2010-09-30
Mount the Ubuntu partition (The one that contains your Ubuntu Install) and got to a terminal and type

```

<mount/point>/boot/grub/grub.cfg

```

Replace <mount/point> with the actual location of the partition. And edit the lines mentioned in post # 6. And finally reboot.

You can't use startup manager to edit the Grub conf from a live CD.

---

### Post by oldfred on 2010-09-30
I have had grub remember keys hit before menu comes up. If you know how many down arrows to hit try that just after bios.

---

### Post by mp29k on 2010-09-30
> **sikander3786 said:**
> Mount the Ubuntu partition (The one that contains your Ubuntu Install) and got to a terminal and type

```

<mount/point>/boot/grub/grub.cfg

```

This may sound like a dumb question, but how do I find out what the <mount/point> is?

I typed "sudo gedit /boot/grub/grub.cfg" and I get a blank file.

I have several partitions.

Can't find out how to get the <mount/point> you are referencing.

---

### Post by WishDasher on 2010-09-30
For me, the timeout stops as soon as I press any key. So you should be able to just keep pushing "down" or anything else quickly while it starts just to stop the countdown immediately, with no need to even count your keypresses.

---

### Post by sisco311 on 2010-09-30
> **mp29k said:**
> This may sound like a dumb question, but how do I find out what the <mount/point> is?

I typed "sudo gedit /boot/grub/grub.cfg" and I get a blank file.

I have several partitions.

Can't find out how to get the <mount/point> you are referencing.

You can select the partition from the Places menu, then in the file manager navigate to the grub.cfg file, in a terminal type:
```
gksu gedit
```
and a space, then drag the file from the file manager into the terminal and press Enter.

---

### Post by mp29k on 2010-09-30
no amount of key pressing solves this, and I have found my mount point:

/dev/sda3
but...

"/dev/sda3/boot/grub/grub.cfg" does not exist...

I am at a loss.  I am afraid I am going to have to reinstall Ubuntu in a clean install... really don't want to do that as I have it sitting out there configured how I like it!

Is there any way to install a package while running in Live CD?  StartupManager was not found.

---

### Post by drs305 on 2010-09-30
> **mp29k said:**
> no amount of key pressing solves this, and I have found my mount point:

/dev/sda3
but...

"/dev/sda3/boot/grub/grub.cfg" does not exist...

I am at a loss.  I am afraid I am going to have to reinstall Ubuntu in a clean install... really don't want to do that as I have it sitting out there configured how I like it!

Is there any way to install a package while running in Live CD?  StartupManager was not found.

Run the commands this way:
```
sudo mount /dev/sda3 /mnt
sudo chmod +w /mnt/boot/grub/grub.cfg
gksudo gedit /mnt/boot/grub/grub.cfg

```

Note on second command: I think even with the LiveCD you have to make it writable as root before you can save the grub.cfg file.

---

### Post by sikander3786 on 2010-09-30
[QUOTE=mp29k;9909306]This may sound like a dumb question, but how do I find out what the <mount/point> is?

---

### Post by sisco311 on 2010-09-30
EDIT: drs305 beat me to it. [noparse]:)[/noparse]
/dev/sda3 is the device name of the partition you have to mount:
[s]```
sudo mount /dev/sda3 /mnt
```
```
gksu gedit /mnt/boot/grub/grub.cfg
```[/s]

---

### Post by oldfred on 2010-09-30
If your 9.10 was an upgrade you may still have menu.lst from old grub?

To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by drs305 on 2010-09-30
> **oldfred said:**
> If your 9.10 was an upgrade you may still have menu.lst from old grub?


And if it's using Grub legacy, to interrupt you would use the ESC key and not the SHIFT key.

---

### Post by mp29k on 2010-09-30
> **drs305 said:**
> Run the commands this way:
```
sudo mount /dev/sda3 /mnt
sudo chmod +w /mnt/boot/grub/grub.cfg
gksudo gedit /mnt/boot/grub/grub.cfg

```Note on second command: I think even with the LiveCD you have to make it writable as root before you can save the grub.cfg file.

This is what worked perfectly!!! You are da man!  Thanks so much for your help.

-Kevin :guitar:

---

### Post by drs305 on 2010-09-30
> **mp29k said:**
> This is what worked perfectly!!! You are da man!  Thanks so much for your help.

-Kevin :guitar:

You are welcome. You still need to accomplish some cleanup steps. You have edited grub.cfg but normally this is not the approved method. The reason is the grub.cfg file is created by various Grub 2 scripts. 

These scripts are automatically run for a variety of reasons (a grub package update, introduction of a new kernel, etc). So you really need to change the timeout of the script that makes the input to grub.cfg.

This script is */etc/default/grub*

Open this file for editing and change the GRUB_TIMEOUT= value to whatever you wish. Then save the file and update grub.

```
gksu gedit +7 /etc/default/grub
```

Also, you can *now* install StartUp-Manager if you wish. It can set the default OS and timeout, among other things. See the "SUM" link in my signature line for information on how to install and use it.

Happy Ubuntu-ing !

---

