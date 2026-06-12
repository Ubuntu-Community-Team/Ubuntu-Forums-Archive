---
title: "Desktop Effects could not be enabled"
date: 2010-04-27
forum: General Help
---

### Post by skarme on 2010-04-27
I'm using Ubuntu 9.10. My Monitor is undetected; however the screen resolutions are working fine. I cant enable the 'Extra' or 'Normal' visual effect; the message "Desktop Effects could not be enabled is displayed". I'm new to Ubuntu and I need to work around with this. Any kind of assistance would be highly appreciated.
This is a bit of the descriptiion
description: VGA compatible controller
       product: CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz

---

### Post by limey_rick on 2010-04-27
This could be because for your particular graphics card or setup, special drivers are needed. 

I don't know much about VIA chipsets, but have you looked at their website for specific linux drivers? 

[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

From this it seems that they do not support 3D graphics in Linux, so that may be why you can't specify advanced effects.

---

### Post by quadproc on 2010-04-27
> **skarme said:**
> I'm using Ubuntu 9.10. My Monitor is undetected; however the screen resolutions are working fine. I cant enable the 'Extra' or 'Normal' visual effect; the message "Desktop Effects could not be enabled is displayed". I'm new to Ubuntu and I need to work around with this. Any kind of assistance would be highly appreciated.

Which driver are you using?
Do you have an xorg.conf file?

quadproc

---

### Post by ghostborg on 2010-04-27
If all else fails and you have a desktop get an Nvidia card from your local store and hang onto your receipt. A couple of years ago I threw in a Geforce 8400 GS for less than $50. I'm sure you can do better. I had ATI HD3200 on board graphics but would frequently get an unbootable system after system updates. I haven't had an problems since. knock on wood.

---

### Post by skarme on 2010-04-27
@[limey_rick]("http://ubuntuforums.org/member.php?u=669103")
The website dosen't have drivers for ubuntu 9.10. Do you recommend trying the driver out for Ubuntu 9.04.

---

### Post by skarme on 2010-04-27
@quadproc
I was running Compiz check and this is what I got:
 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: openchrome driver in use 

Hence I'm using the Openchrome driver. (I had no clue as to what driver I was using)
I'm new to Ubuntu like I said; so I'm not sure about the xorg.conf file.

---

### Post by peterj on 2010-04-27
question answered in simultaneous post.

---

### Post by quadproc on 2010-04-27
> **skarme said:**
> 
Hence I'm using the Openchrome driver. (I had no clue as to what driver I was using)
I'm new to Ubuntu like I said; so I'm not sure about the xorg.conf file.
OK, I have not worked with the openchrome graphics so I don't know for sure how it will interact with Compiz and X windows but here are a couple of thoughts:

There is a lot of information available at [http://www.openchrome.org/](http://www.openchrome.org/).

You can also learn a good deal by typing man openchrome into a terminal window.  Also, info openchrome.

If you look in the file /etc/X11/xorg.conf then you will find a lot of entries and one of them will relate to your active driver.  Try ```
grep "river" < /etc/X11/xorg.conf
``` and look for a line that does not start with # (those lines are comments).  That will tell you what X windows is using for a driver.

To get stable results you need a driver that is compatible with the version of your kernel, the X windows version that you have, and the graphics card itself.  Usually the manufacturer's web site can tell you about compatibility.

You may have a choice of more than one driver.  If you do decide to try different drivers then there are a couple of important points which are usually not obvious:

1. The new driver will not take effect until X windows is restarted.  This means that you will have to log back in.  One way to do the restart is ```
sudo service gdm restart

```
2. If there is a problem with the new driver then X windows may not run at all.  In this case you will probably want to fall back to the configuration that used to work so it is wise to keep a backup copy of any file(s) that you change during the process.  You will probably have to do the fallback from the command line.

3. You should remove all traces of an old driver before installing a new one.  If you don't then weird and bizarre problems can occur.  The system may seem to run but may do things like have no mouse operation, not produce appropriate screen size, or run only in "low graphics mode".

4. You can usually recover a system from a damaged xorg.conf file by using the recovery mode option that grub provides at boot time.  But you'll be doing it through the command line.

5. If you have ssh (or even rsh and rlogin) installed and you have another computer connected to the one in question then you may be able to use that connection to restore the system.

6. Some graphics card vendors have software which modifies your xorg.conf file.  Sometimes those mods do not work.  Therefore, if things don't work after driver installation, you might find that your xorg.conf file needs repair.

I hope that these ideas are at least somewhat useful to you.

quadproc

---

### Post by limey_rick on 2010-04-27
So you could try the 9.04 drivers, but they may not work, I guess it could be a bit hit or miss - not really my level of expertize I am afraid.

The other suggestion from ghostborg is not a bad one. This is exactly what I did when I had lots of problems with an ATI card. Since then, I have always used NVidia graphics cards and had no problems.

---

### Post by skarme on 2010-04-28
@[quadproc]("http://ubuntuforums.org/member.php?u=1004489"):
Is the code correct? 
[CODE]
grep "river" < /etc/X11/xorg.conf
On pasting the same in the terminal I get the following:
bash: /etc/X11/xorg.conf: No such file or directory

---

### Post by skarme on 2010-04-28
@[limey_rick]("http://ubuntuforums.org/member.php?u=669103"):
Thanks for your help and suggestions. Unfortunately the Ubuntu 9.04 drivers didn't work. I'll keep '[ghostborg]("http://ubuntuforums.org/member.php?u=298901")' suggestion in mind; in case I fail trying to fix this.
Thanks once again :)

---

### Post by quadproc on 2010-04-28
> **skarme said:**
> @[quadproc]("http://ubuntuforums.org/member.php?u=1004489"):
Is the code correct? 
[CODE]
grep "river" < /etc/X11/xorg.conf
On pasting the same in the terminal I get the following:
bash: /etc/X11/xorg.conf: No such file or directory
Yes, that is correct code.  It means that you don't have an xorg.conf file, or that the file's permissions do not allow you to read it.  Most likely the former.

The xorg.conf file is optional in the later Ubuntu versions.  If it doesn't exist then X windows looks at your hardware and makes its best guess about what makes sense to do.  If you want to tell X windows how to operate then you can create and furnish the xorg.conf file to the system.  That approach may be the only way to get the most out of your graphics hardware.

quadproc

---

### Post by skarme on 2010-04-28
@[quadproc]("http://ubuntuforums.org/member.php?u=1004489")
I looked up ways to create the xorg.conf file and hence made it. I entered the code you mentioned. This is what I got:
Driver      "kbd"
    Driver      "mouse"
        ### Available Driver options are:-
    Driver      "openchrome"
Do you recommend trying the manual installation given in the following link to enable my desktop effects.
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by quadproc on 2010-04-29
> **skarme said:**
> @[quadproc]("http://ubuntuforums.org/member.php?u=1004489")
I looked up ways to create the xorg.conf file and hence made it. I entered the code you mentioned. This is what I got:
Driver      "kbd"
    Driver      "mouse"
        ### Available Driver options are:-
    Driver      "openchrome"

The line above tells you that the graphics driver is "openchrome".
> 
Do you recommend trying the manual installation given in the following link to enable my desktop effects.
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
I am not sure what that driver will do with the effects because I don't know which capabilities the effects draw upon.  The installation procedure there is about a year old and a few things have changed, for example the gdm start/stop functions are now done by using "service" so you probably will run into things in that procedure that don't work.  You can probably figure out what the workarounds are by looking in the Ubuntu documentation.

If the effects do not use any 3D stuff, and if you are not into graphics games, then you would probably be OK with the open source driver.  Otherwise, I would recommend trying the vendor's proprietary driver.

quadproc

---

### Post by skarme on 2010-05-01
@[quadproc]("http://ubuntuforums.org/member.php?u=1004489")
well i guess i cant enable the desktop effects till via launches driver's for ubuntu 10.04(I upgraded from 9.10 recently); I've searched a lot, seems like i'll have to go with ghostburg's suggestion or just let it be. The ubuntu desktop effects are cool, hence wanted them.
Thanks for your help though.
If you still find something useful, plz post it. Thanks again

---

### Post by skarme on 2010-05-04
Well I've upgraded to Ubuntu 10.04; still working on the desktop effects.
I installed the 'mesa' utilities and ran 'glxinfo' in the terminal.
Direct Rendering: Yes.....
Dosen't that mean that i have the 3D effects enabled...
yet i can't enable my desktop effects.

---

