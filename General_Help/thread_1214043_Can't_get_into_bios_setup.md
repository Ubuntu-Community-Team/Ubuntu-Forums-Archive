---
title: "Can't get into bios setup"
date: 2009-07-15
forum: General Help
---

### Post by bobke on 2009-07-15
I have recently had a hardware problem that caused replacement of my video card. When I booted after the repair, I get this: "Failed to start X server (your graphical interface) It is  likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

* Reloading postfix configuation"

I know the driver is in there and the new card is working because I booted ok in Mepis on another partition. But the Ubuntu partition dosn't boot. If I could get to the bios setup I tshould be able to easily fix this problem. 

When GRUB starts Ubuntu I try to boot in recovery mode which also fails, but does allow me to login as root: "root@computer-$" . But can I get into bois setup from here, or can I do an auto install of the driver (nvidia GeForce 9300 card)? I need a command to do one or the other.

---

### Post by t4thfavor on 2009-07-15
login as root, and run dpkg --reconfigure xserver-xorg then pick defaults. Next time you boot it should ask you to install the restricted drivers.

---

### Post by bobke on 2009-07-16
> **t4thfavor said:**
> login as root, and run dpkg --reconfigure xserver-xorg then pick defaults. Next time you boot it should ask you to install the restricted drivers.
I'm logged in as root and run "lspci" to get the pci devices list, and found VGA driver nvidia corp unknown device 0404. So I know the new graphics card is at least identified. However, when I run "dpkg --reconfigure xserver-org" I get "configuration error unknown item 'FAIL_DELAY"  Could there be something else wrong here?

I would like not to have to reinstall Ubuntu and lose my recent files, which don't have a recent backup. I wonder if I could get into the bois setup via the original installation DVD, which I do have, without losing data?

---

### Post by bobke on 2009-07-18
> **bobke said:**
> 
I would like not to have to reinstall Ubuntu and lose my recent files, which don't have a recent backup. I wonder if I could get into the bois setup via the original installation DVD, which I do have, without losing data?
Does anyone know if I can reboot with the installation DVD, so I can at least copy my files to another drive before  reinstallation, if I need to reinstall from scratch at all?

---

### Post by oldos2er on 2009-07-18
You need to enter your BIOS immediately after booting, during POST. Once grub comes up, it's too late.

---

### Post by jeppewinther on 2009-07-18
Sure you can boot up a LiveCD and move whatever files you feel like saving around.

And as mentioned, your BIOS is accessed right after you powerup, around the time it tallies up the RAM and so on.

---

### Post by bobke on 2009-07-22
> **jeppewinther said:**
> Sure you can boot up a LiveCD and move whatever files you feel like saving around.

And as mentioned, your BIOS is accessed right after you powerup, around the time it tallies up the RAM and so on.I got the BIOS to come up prior to GRUB but it isn't a complete BIOS setup for mouse, keyboard and monitor, etc. It is only to enable and disable certain components of the computer hardware. So I can't select the video driver, and still stuck with no xserver.

As for trying the LiveCD, all my files are for Edgy with updates over the past year or so. I will need a LiveCD, but if I get a recent CD will it work for the files which were created with Edgy? In other words - will I need a Edgy LiveCD?

---

### Post by bobke on 2009-07-23
> **jeppewinther said:**
> 

And as mentioned, your BIOS is accessed right after you powerup, around the time it tallies up the RAM and so on. My first post was to try to get a command to open up BIOS set up, but didn't know that I should do it before GRUB. The command I used was "del" upon restart of the computer. This brings up, like I said previous, a BIOS setup for computer components only. Maybe I'm using the wrong command to get into the setup to select the video drivers, mouse,etc. (If i can't do this, I'll have to go the LiveCD route.)

---

### Post by jocko on 2009-07-23
> **bobke said:**
> My first post was to try to get a command to open up BIOS set up, but didn't know that I should do it before GRUB. The command I used was "del" upon restart of the computer. This brings up, like I said previous, a BIOS setup for computer components only. Maybe I'm using the wrong command to get into the setup to select the video drivers, mouse,etc. (If i can't do this, I'll have to go the LiveCD route.)
The bios setup is just that. It knows *nothing* about your operating system or which drivers you may or may not have installed. Your problem is with the video driver, which has nothing to do with the bios.

---

### Post by lisati on 2009-07-23
> **bobke said:**
> My first post was to try to get a command to open up BIOS set up, but didn't know that I should do it before GRUB. The command I used was "del" upon restart of the computer. This brings up, like I said previous, a BIOS setup for computer components only. Maybe I'm using the wrong command to get into the setup to select the video drivers, mouse,etc. (If i can't do this, I'll have to go the LiveCD route.)

I had a quick look at the thread. I think the suggestion to get into get into bios prior to grub was in response to one of your own questions:
> I wonder if I could get into the bois setup via the original installation DVD, which I do have, without losing data? 


It might be more productive to use the "recovery mode" option presented by grub than to tinker with BIOS settings (beyond loading setup defaults) - the exact sequence of actions once you have started this way eludes me for the moment.

---

### Post by mcduck on 2009-07-23
> **bobke said:**
> My first post was to try to get a command to open up BIOS set up, but didn't know that I should do it before GRUB. The command I used was "del" upon restart of the computer. This brings up, like I said previous, a BIOS setup for computer components only. Maybe I'm using the wrong command to get into the setup to select the video drivers, mouse,etc. (If i can't do this, I'll have to go the LiveCD route.)

That *is* BIOS for you.

Drivers are what operating systems use, and thus are configured in the operating system you run. Definitely not in BIOS, which does it's work before you actually even start any operating system..

Anyway, simply entering the recovery mode, and then selecting the root shell option should get you into the system, and then running "dpkg-reconfigure xserver-xorg" should fix the problem. (note that this only works on 8.04 and older Ubuntu versions, but since youa re running Edgy it's fine).

If that doesn't do the trick then any Linux live-CD will work for backing up your files.

---

### Post by raymondh on 2009-07-23
> **mcduck said:**
> ... Then any linux live-cd will work for backing up your files.

+1

---

### Post by jocko on 2009-07-23
> **bobke said:**
> When GRUB starts Ubuntu I try to boot in recovery mode which also fails, but does allow me to login as root: "root@computer-$" . But can I get into bois setup from here, or can I do an auto install of the driver (nvidia GeForce 9300 card)? I need a command to do one or the other.
Then recovery mode does NOT fail. It should just give you a root terminal from where you should be able to fix the problem. (again: your problem is not anything that can be solved through the bios).

What graphics card did you have before you go the new one?
If you had an ati card and used the proprietary driver, you must completely remove any trace of that driver to be able to get anything else working.

---

### Post by bobke on 2009-08-11
This problem has been partially resolved. I now have xserver up and running, and have done a backup of all files, and can now edit xorg.conf.  So I'm almost good to go... Except now with the new graphics card  I can't seem to get the new driver installed, yet. It's downloaded from nvidia, but the install commands don't work. Currently have to use "vesa" instead of "nv". Apparently the drivers are different from the GeForce 7300GT and 8400GS. They were supposed to be the same when I bought the 8400, but appears there is some difference. Maybe it's how they are compiled.

---

### Post by michy99 on 2009-08-11
Support for Edgy ended on April 25th, 2008. It might be time to consider an upgrade.

---

### Post by bobke on 2009-08-12
This problem has been resolved. I got x-server up and running, and files backed up.

Thanks all

---

