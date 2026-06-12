---
title: "Trying to Edit Grub but NOTHING there"
date: 2010-05-03
forum: General Help
---

### Post by jschille on 2010-05-03
I am attempting to fix my 10.04 problems from [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) and the OP tells me to go edit my grub file with this command.

gksu gedit /etc/default/grub  

I enter the command, gedit opens grub but there is no text in the file. I am assuming this isn't right. What am I doing wrong?

---

### Post by WorMzy on 2010-05-03
Are you booting from a Live CD or your installation? If it's a Live CD you need to mount your installation directory, then open files relative to its mount point. (e.g. /media/<PartitionName>)

If you're doing this from your installation, and that file doesn't exist, perhaps you have grub legacy; in which case, you need to modify /boot/grub/menu.lst. But be careful of what you do with that file - if the tutorial is written for grub2, you'll need to convert what it tells you to write into something that grub legacy can interpret.

---

### Post by jschille on 2010-05-03
> **WorMzy said:**
> Are you booting from a Live CD or your installation? If it's a Live CD you need to mount your installation directory, then open files relative to its mount point. (e.g. /media/<PartitionName>)

If you're doing this from your installation, and that file doesn't exist, perhaps you have grub legacy; in which case, you need to modify /boot/grub/menu.lst. But be careful of what you do with that file - if the tutorial is written for grub2, you'll need to convert what it tells you to write into something that grub legacy can interpret.

ugg, now im worried. I am doing this from my installation
I am fairly confident that I do have legacy.

Do I want Grub 2 instead of legacy?

Being fairly new to ubuntu should I just not touch anything and pray that they come out with a hotfix for the issue in the next week or so?

EDIT: Is Grub2 needed for 10.04 instead of legacy? Can that be the issue giving me such a slow boot time?

---

### Post by WorMzy on 2010-05-03
I prefer legacy because that's what I'm used to, but grub2 is much more powerful and robust (apparently), so it's up to you which one you use. I'm not sure what the procedure is for switching from legacy to 2, but I presume you just remove grub, install grub-pc, and run sudo update-grub.

I'd wait for someone to provide more certain instructions, or check google for a tutorial, rather than following my instructions. That is, if you want to switch.

---

### Post by jschille on 2010-05-03
I found the guide on how to change from Legacy to Grub 2
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

I just don't know if it is necessary or not.  The problem is all these guides for the Bug Fix's in 10.04 are giving instructions with Grub2. gah, thanks for your help. 
I think Ill just sit on this for a week or two and hope for a hot fix.

---

### Post by GSF1200S on 2010-05-03
It would help to have more information available pertaining to your setup and what it is exactly that you are trying to fix.

I would suggest pasting the results of the following commands in a post here:
```
sudo fdisk -l
sudo blkid
```
as well as explain what you need to fix :)

---

### Post by WorMzy on 2010-05-03
Hopefully there will be something of that nature. I take it that it's the splash image that you're trying to fix? I've given up with that too for the time being too.

---

### Post by jschille on 2010-05-03
I am trying to fix the splash image, as well as the really slow boot.
I entered in those commands and this is what came up with.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf7c0c486

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1918       47728   367967024    7  HPFS/NTFS
/dev/sda4           47729       60801   105008872+   5  Extended
/dev/sda5           47729       60264   100695388+  83  Linux
/dev/sda6           60265       60801     4313421   82  Linux swap / Solaris
jb@jb-laptop:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="6A346D70346D4065" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="46686F9A686F878F" TYPE="ntfs" 
/dev/sda5: UUID="75d59b76-ab9f-4260-94a3-42d24bc1a280" TYPE="ext3" 
/dev/sda6: UUID="5108b146-fc4b-4920-b330-1ff8b5df4a37" TYPE="swap"

Edit:
I was trying to edit my grub file from these instructions [**[http://ubuntuforums.org/showthread.php?t=1469475]](http://ubuntuforums.org/showthread.php?t=1469475])** but I have legacy instead of Grub2.

I think I am just giving up for now, but if you have any ideas on how to fix my slow boot i'd love to hear it.  Most ppl say disable the floppy from the BIOS but I have no floppy.

---

### Post by jschille on 2010-05-04
I am trying to fix the splash image, as well as the really slow boot.
I entered in those commands and this is what came up with.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf7c0c486

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1918       47728   367967024    7  HPFS/NTFS
/dev/sda4           47729       60801   105008872+   5  Extended
/dev/sda5           47729       60264   100695388+  83  Linux
/dev/sda6           60265       60801     4313421   82  Linux swap / Solaris
jb@jb-laptop:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="6A346D70346D4065" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="46686F9A686F878F" TYPE="ntfs" 
/dev/sda5: UUID="75d59b76-ab9f-4260-94a3-42d24bc1a280" TYPE="ext3" 
/dev/sda6: UUID="5108b146-fc4b-4920-b330-1ff8b5df4a37" TYPE="swap"

---

### Post by GSF1200S on 2010-05-04
> **jschille said:**
> I am trying to fix the splash image, as well as the really slow boot.
I entered in those commands and this is what came up with.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf7c0c486

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1918       47728   367967024    7  HPFS/NTFS
/dev/sda4           47729       60801   105008872+   5  Extended
/dev/sda5           47729       60264   100695388+  83  Linux
/dev/sda6           60265       60801     4313421   82  Linux swap / Solaris
jb@jb-laptop:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="6A346D70346D4065" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="46686F9A686F878F" TYPE="ntfs" 
/dev/sda5: UUID="75d59b76-ab9f-4260-94a3-42d24bc1a280" TYPE="ext3" 
/dev/sda6: UUID="5108b146-fc4b-4920-b330-1ff8b5df4a37" TYPE="swap"

One last question: what video card do you have? I will edit this post with a fix, so refresh in a little while.

**EDIT** If you have an intel card, do not do this yet- you need to change nomodeset to something else, and it depends on what intel card you have. A 855GM user can use i915.modeset=0 in place of nomodeset, but I dont have an intel computer to test this with**

Enter the following commands in a terminal:
```
sudo apt-get remove grub
sudo apt-get install grub-pc
sudo grub-install /dev/sda
sudo update-grub2
```
After running that last command, you should see your linux and windows install listed in the terminal output. Next, we try to fix your splash problem (and hopefully it speeds up your boot):
```
sudo apt-get install v86d
gksu gedit /etc/default/grub
```
Look for the line that says:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and replace it with:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
Then, look for the line that says:
> #GRUB_GFXMODE=640x480
and replace it with:
> GRUB_GFXMODE=1280x1024
Save the file and exit gedit.

Next, run the following command:
```
gksu gedit /etc/initramfs-tools/modules
```
and add this line at the end of the file:
```
uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap
```
Save the file and close gedit.

Then, run this command in a terminal:
```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
```

Finally, run the following two commands:
```
sudo update-grub2
sudo update-initramfs -u
```

The above worked for me on an Nvidia 9800GTX.

---

### Post by jschille on 2010-05-04
See Below

---

### Post by jschille on 2010-05-04
ALRIGHT! I got the file to open with the text

Type in all your code.
HERE IS THE RESULT:
When the computer boots up the GRUB screen is in 1200x800 resolution, BUT when the UBUNTU screen comes up it is EVEN BIGGER and worse resolution before.  Making huge strides forward at least.

thank you!

---

### Post by GSF1200S on 2010-05-04
> **jschille said:**
> Alright man, thank you so much.  Progress is definitely being made here.  I have installed Grub2 and it works.  Didn't speed up the boot, now instead of being stuck on a screen that said "Boot from (hd0, 4) ... Starting up..." I just get a "_" that flashes for about 15 seconds and then it starts to boot.  But at least I have Grub2 now....

As for the rest of the lines of code, once I run the gedit command to get into the grub file to change the lines of code I open it and I get an empty file.... So I am stuck now.  

Again, I got to installing Grub2, but once you ask me to edit it I am out of luck because once I open the edit file it opens as an empty file with nothing in it :(

Thanks for the help, I can feel this getting closer!

Well, you can just use mine- all the file does is tell the command "update-grub" how to update /boot/grub/grub.cfg when it runs. Thats really strange that its not there..

Open nautilus as root:
```
gksu nautilus /etc/default
```
You should see plenty of other files there. Create a new file and name it:

grub

and then place the following text in it (remember ONLY if you have an nvidia card- you will need to change the 'nomodeset' part if you are an intel user):
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024
GRUB_GFXPAYLOAD_LINUX=1280x1024
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Then save the file and exit gedit. Rerun the commands:
```
sudo update-grub
sudo update-initramfs -u
```
and try booting again. This fix works for some, and not for others.. so it will take luck too.

---

### Post by GSF1200S on 2010-05-04
> **jschille said:**
> ALRIGHT! I got the file to open with the text

Type in all your code.
HERE IS THE RESULT:
When the computer boots up the GRUB screen is in 1200x800 resolution, BUT when the UBUNTU screen comes up it is EVEN BIGGER and worse resolution before.  Making huge strides forward at least.

thank you!

Im not sure what you mean.. Do you mean the Ubuntu plymouth screen (boot screen)?

**EDIT** When grub starts up, press 'c'

In the command line that follows, type:
> vbeinfo

and take a note of the resolutions it gives you. One of those resolutions is what you need to use for the resolutions in above commands. Usually that resolution above works, but apparently not for you..

---

### Post by jschille on 2010-05-04
> **GSF1200S said:**
> Im not sure what you mean.. Do you mean the Ubuntu plymouth screen (boot screen)?

**EDIT** When grub starts up, press 'c'

In the command line that follows, type:


and take a note of the resolutions it gives you. One of those resolutions is what you need to use for the resolutions in above commands. Usually that resolution above works, but apparently not for you..

Hmm.. good question.
Sequence of Boot.

Dell Screen.
Grub Screen.
    - I select Ubuntu.
Screen with '_' flashing (only flashing for 3-5 seconds now, interesting)
UBUNTU Screen (Red and White Dots - Appears for longer than before now, interesting.)
Login Screen (to enter PW)

Not quite sure what this Plymoth screen is... I'm not getting it unless I see it and don't know what it is.  Going to reboot and press 'c' during Grub.

---

### Post by jschille on 2010-05-04
Pressed 'C' on Grub Screen.

0x100 640 x 400 x 8 packed
0x101 640 x 480 x 8 packed
0x102 800 x 600 x 8 packed
0x103 1024 x 768 x 8 packed
0x104 320 x 200 x 16 packed
....

The very bottom line said: "Configured VBE mode (vbe_mode) = 0x101

Useful?
Thanks again for all your help. This is amazing

EDIT: just went through and changed all the resolutions to 1024x768 going to restart now.

---

### Post by GSF1200S on 2010-05-04
> **jschille said:**
> Pressed 'C' on Grub Screen.

0x100 640 x 400 x 8 packed
0x101 640 x 480 x 8 packed
0x102 800 x 600 x 8 packed
0x103 1024 x 768 x 8 packed
0x104 320 x 200 x 16 packed
....

The very bottom line said: "Configured VBE mode (vbe_mode) = 0x101

Useful?
Thanks again for all your help. This is amazing

Well, you are seeing plymouth ;) Plymouth is the Ubuntu logo with the flashing dots (in my case an Xubuntu logo as I run Xubuntu). The few seconds of the blinking cursor I have as well (before the logo comes up), and I believe this is due to the fact that plymouth is being run with vesa as opposed to your graphics drivers. Plymouth is still a work in progress and MANY people have had issues with it so far...

I would suggest changing the above commands to match the 1024x768 resolution as output by vbeinfo- perhaps that will make it a little prettier, but then I cannot be sure because the above worked for me. After editing the above numbers (in all the files listed above, not just one), rerun:
```
sudo update-grub
sudo update-initramfs -u
```

**EDIT** Just to let you know, the purpose of Plymouth is to make the boot process more aesthetically pleasing. It was intended to get rid of the flashing, text, and graphical anomalies of usplash, which was used prior. Obviously, its a work in progress.. It requires features that arent incorporated in the Nvidia and ATI proprietary drivers (yet at least), and as such I had you set it up where it uses vesa to run instead.

---

### Post by jschille on 2010-05-04
Booya, thank you so much.
After going through and changing the values to 1024x768 it works!

Thank you so much GSF - correct resolution is now made.  The "_" screen only lasts a few seconds.  Now there is just a significant load on the Ubuntu (red and white dot screen).  Before this whole fiasco it would be on that Ubuntu (red and white dot screen) for about 2 seconds, now it fills all the white dots with red and then white again - no big deal, I can live with it, just want to see the fast load that 10.04 holds to have.

Again, thank you so much GSF, was getting a little frustrated with this earlier but you really helped.

---

### Post by GSF1200S on 2010-05-04
> **jschille said:**
> Booya, thank you so much.
After going through and changing the values to 1024x768 it works!

Thank you so much GSF - correct resolution is now made.  The "_" screen only lasts a few seconds.  Now there is just a significant load on the Ubuntu (red and white dot screen).  Before this whole fiasco it would be on that Ubuntu (red and white dot screen) for about 2 seconds, now it fills all the white dots with red and then white again - no big deal, I can live with it, just want to see the fast load that 10.04 holds to have.

Again, thank you so much GSF, was getting a little frustrated with this earlier but you really helped.

Does it take longer to boot then it did before you started this whole process? Perhaps its an illusion in the sense that you see that screen longer? You can revert the changes back to nil and rerun:
```
sudo update-grub
sudo update-initramfs -u
```
and you should be back to the way it was.. If you mean it all works good now, well then Im glad I could help :)

---

### Post by jschille on 2010-05-04
nah, probably boots a few seconds faster, just not getting that 10 second load they say.
thanks again

---

### Post by GSF1200S on 2010-05-04
> **jschille said:**
> nah, probably boots a few seconds faster, just not getting that 10 second load they say.
thanks again

That depends heavily on your hardware. Ubuntu boots in about 8 seconds for me, but I am running on RAID so that helps.. Boot time depends heavily on hard drive speed, seek time for the hard drive, processor, and even ram speed. You can search around the forums though- I have seen guides suggesting ways to improve your bootspeed.

You might also check out a program called bootchart (and also a gui if youd like for bootchart called pybootchartgui). Bootchart allows you to see the loading times for each thing Linux does when it starts up, so you can focus on areas that need improvement. Some fixes are easy, while others are not. Both apps are installable in the repos either by command line:
```
sudo apt-get install bootchart pybootchartgui
```
or by using Synaptic to install them ;)

---

