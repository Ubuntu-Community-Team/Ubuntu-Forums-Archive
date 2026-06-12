---
title: "Lost Boot with Ubuntu Install (W7 RAID SSD)"
date: 2011-11-27
forum: General Help
---

### Post by SkOrPn on 2011-11-27
Hello everyone

Today I got bored and decided I was tired using a dedicated machine for Ubuntu. My old AMD machine is like 6 years old and I wanted Ubuntu on a more modern faster rig. I decided to install Ubuntu onto a new OCZ Vertex SSD that I had lying around unused, but in order to do so I had to enable the onboard Marvell Sata controller and set it to AHCI. All six of my ICH10 ports are currently filled with drives, four drives for Windows 7 raid 0, and two 1TB drives for storage. I noticed my mobo had these two additional red Sata ports, apparently the Marvel 9128, so decided to use it for Ubuntu.

Anyway, I decided on a clean install from a fast USB flash drive and everything seemed to go great, the installer even seen the Windows 7 Raid array and everything else. So I selected the blank Vertex SSD and had the bootloader installed to the same Vertex SSD as well. Everything seemed to install without a hitch, but upon first reboot I did NOT get the Grub dual boot setup with Windows 7 like I had hoped.

Can someone please explain where I went wrong and if I can easily fix it with a Grub edit? Again, I did not mess with the Windows Raid 0 array during install, so Im baffled as to why Im not getting the normal dual-boot grub entries. Do I need to edit the Windows Bootloader instead and have the machine first boot to the raid array as before? Or can I still use Grub somehow to dual boot?

TIA
SkOrPn

---

### Post by drs305 on 2011-11-27
SkOrPn,

Welcome to the Ubuntu forums.  :-)

Just to be clear - is it currently booting Ubuntu and you just aren't getting the menu (with Windows on it)?

If that is the case, it's possible Grub didn't find Windows during the installation. Try running this from a gnome-terminal:
```
sudo update-grub
```
Watch the terminal to see if it finds Windows.

If it doesn't find Windows, you could try the Boot Repair app (see the link in my signature line).

If this doesn't work let us know. I'll move these posts to their own thread where you can get more inputs.

---

### Post by SkOrPn on 2011-11-27
> **drs305 said:**
> SkOrPn,

Welcome to the Ubuntu forums.  :-)

Just to be clear - is it currently booting Ubuntu and you just aren't getting the menu (with Windows on it)?

If that is the case, it's possible Grub didn't find Windows during the installation. Try running this from a gnome-terminal:
```
sudo update-grub
```
Watch the terminal to see if it finds Windows.

If it doesn't find Windows, you could try the Boot Repair app (see the link in my signature line).

If this doesn't work let us know. I'll move these posts to their own thread where you can get more inputs.

Yes, I installed Ubuntu on a machine that already had a Windows 7 install on the Intel ICH10 Raid 0 array. During the install process it told me I had Windows 7 and asked me what to do. I selected install Along-Side Windows and then selected the empty non-used SSD (I had just installed moments before). After the Install was complete I rebooted and I do NOT have a Windows entry in the Grub Bootloader. I disabled the onboard Marvell controller to boot back into Windows 7 and it tells me a bunch of code and something Grub Rescue, on a black screen. Not sure how I messed this up when the install went so smoothly. Now I can't seem to find my Windows 7 install, although I know the array was not touched during the Ubuntu install process. Any ideas what I did wrong?

Although I have been messing with Linux on and off for 15 years or so, please consider me a n00b. I guess Ubuntu still does not like Raid arrays? I am trying the boot repair and will get back soon with the outcome. Thanks very much for your help...

SkOrPn

---

### Post by drs305 on 2011-11-27
I've moved your posts to a new thread.

So it does boot Ubuntu if you have everything hooked up?

Try Boot Repair. If that doesn't work, run the Boot Info Script and post the contents of RESULTS.txt or the link provided by Boot Repair.

You should be able to get Windows working again by inserting the W7 disk. This will remove the ability to boot Ubuntu, but first things first. I'm not a Windows user but I think it will automatically attempt to repair the MBR and boot files. If not, there is a repair utility - you probably need to fix the MBR.

There is also a way to restore the Windows boot via the Ubuntu LiveCD but we can deal with that if Boot Repair doesn't restore things or your Windows repair disk doesn't restore Windows.

---

### Post by SkOrPn on 2011-11-27
> **drs305 said:**
> I've moved your posts to a new thread.

So it does boot Ubuntu if you have everything hooked up?

Try Boot Repair. If that doesn't work, run the Boot Info Script and post the contents of RESULTS.txt or the link provided by Boot Repair.

You should be able to get Windows working again by inserting the W7 disk. This will remove the ability to boot Ubuntu, but first things first. I'm not a Windows user but I think it will automatically attempt to repair the MBR and boot files. If not, there is a repair utility - you probably need to fix the MBR.

There is also a way to restore the Windows boot via the Ubuntu LiveCD but we can deal with that if Boot Repair doesn't restore things or your Windows repair disk doesn't restore Windows.

Yes it appears Ubuntu boots and runs just fine, but the problem is I somehow lost my Windows 7 install (which I run an eBay business from, lol) so I'm kinda in panic mode (not really). I was going to sit and watch a good movie tonight but I need to get this fixed before I go to bed later tonight. Below is the Boot Repair paste info. It did NOT fix it, I get the same entries, Ubuntu, Ubuntu Recovery, and Memtest options, nothing else is present for me to select.

[http://paste.ubuntu.com/752191/](http://paste.ubuntu.com/752191/)

I have no clue how to get back my Windows 7 install and I hope to heavens that I did not inadvertently destroy it somehow. I also provide DeBrick services for Samsung smartphones among other services which is another reason I wanted Ubuntu on this more modern PC of mine. Its been many years since Ive done a dual boot, but this is the first time I tried it with a raid array already present. oops lol

Let me know if I have to redo my Windows setup so I can get on that before I hit the sack. Thank you very much for you kind help.

Rod
a.k.a The SkOrPn

---

### Post by SkOrPn on 2011-11-28
I'm just going to disable the controller that Ubuntu is on and do a repair to my Windows install. After that Im going to research how to add the Ubuntu drive into my Windows bootloader. Maybe since Im using raid I should have done that anyway... lol

SkOrPn

---

### Post by drs305 on 2011-11-28
You will definitely need to repair Windows, as the Windows boot files/folders appear to be missing (unless it has something to do with RAID and the script not picking things up).

The boot script can't find the  /bootmgr and /Boot/BCD folders nor the  /Windows/System32/winload.exe file. Grub looks for these when it builds the menu - since it can't find them, it can't make a Windows menu entry. But of course more importantly, Windows won't boot without these either.

Hopefully you can repair Windows with it's CD/DVD. Once Windows is repaired and boots on its own - since the Ubuntu Grub files look OK - you should be able to return control to Ubuntu/Grub at a time that is convenient for you.

---

### Post by SkOrPn on 2011-11-28
> **drs305 said:**
> You will definitely need to repair Windows, as the Windows boot files/folders appear to be missing (unless it has something to do with RAID and the script not picking things up).

The boot script can't find the  /bootmgr and /Boot/BCD folders nor the  /Windows/System32/winload.exe file. Grub looks for these when it builds the menu - since it can't find them, it can't make a Windows menu entry. But of course more importantly, Windows won't boot without these either.

Hopefully you can repair Windows with it's CD/DVD. Once Windows is repaired and boots on its own - since the Ubuntu Grub files look OK - you should be able to return control to Ubuntu/Grub at a time that is convenient for you.
Ok, Windows was very easy to fix, just inserted my usb flash drive and booted to the recovery console, launched the command and typed "bootrec fixmbr" and "bootrec fixboot" and then Windows booted successfully. I then re-enabled the Ubuntu controller/drive and used EasyBCD to make an entry to Ubuntu on its drive "F" (according to windows) and then rebooted. I got the two entries I wanted during bootup, but now only Windows boots and Ubuntu gives me an error. Im now at a loss because Im 110% sure I told Ubuntu to put the bootloader on that same drive as the Ubuntu OS. Yet my Windows bootloader was corrupt when it shouldn't have been and now Ubuntu wont boot when it should. lol, now Im afraid to run the recovery because it might put me back to this exact same problem that I am trying to fix in the first place.

Any ideas?

---

### Post by drs305 on 2011-11-28
> **SkOrPn said:**
> Any ideas?

As I've mentioned, you are in areas I don't know a lot about (RAID, SSD, EasyBCD, etc) but if you keep both drives connected and can run the boot info script again perhaps something will stand out for someone.

I'm thinking EasyBCD needs Grub to be installed on a partition and not to the MBR. You would probably have to force Grub to install itself on the PBR (partition). Boot repair can do this I believe. But don't take my word without looking it up, as I've not used EasyBCD.

---

### Post by SkOrPn on 2011-11-28
> **drs305 said:**
> As I've mentioned, you are in areas I don't know a lot about (RAID, SSD, EasyBCD, etc) but if you keep both drives connected and can run the boot info script again perhaps something will stand out for someone.

I'm thinking EasyBCD needs Grub to be installed on a partition and not to the MBR. You would probably have to force Grub to install itself on the PBR (partition). Boot repair can do this I believe. But don't take my word without looking it up, as I've not used EasyBCD.

W00t,

Wow, using EasyBCD was just that VERY easy to fix this setup. I just forgot to click on the "Write MBR" button within EasyBCD before which is why it didn't work the first time around. Ubuntu now boots as normal. I setup everything to use the Windows bootloader because its on a super fast 4 ssd raid 0 array and I don't want to go through the process of learning how to make Grub work with Intel/Windows based raid arrays. So now I have two entries "Windows 7", and "Ubuntu 11.10" during bootup.

How-to: I first created a second entry in EasyBCD under the Linux tab, then I selected Grub2 and named it "Ubuntu 11.10" and it automatically created the necessary settings and entries (I have no clue how it knows where my Ubuntu install is but it did automagically), then I had to write it to the mbr which apparently I forgot yesterday, so today trying it again it was easier to understand. Apparently this should not be tried on a tired mind, lol... So, once I successfully booted into Ubuntu I started up a terminal session and typed...

```
sudo gedit /etc/default/grub
```

Entered my password, then in the window that popped up I changed the "GRUB_TIMEOUT=10" to "GRUB_TIMEOUT=0" and then saved and exited. Then back in terminal I simply typed "sudo update-grub" and hit enter and rebooted to test everything. Now, when selecting the Ubuntu 11.10 entry it boots straight to the Unity desktop exactly like I want.

Result = Works beautifully now. If only I could change the threads Title to [SOLVED] id be happy.

Thank you again for the help

SkOrPn

---

### Post by drs305 on 2011-11-28
> **SkOrPn said:**
> 
Result = Works beautifully now. If only I could change the threads Title to [SOLVED] id be happy.

Glad it's working.

You can mark it SOLVED via the 'Thread Tools' link to the top right of the original post.

Does EasyBCD allow Grub to be written to the MBR of the Ubuntu drive, or does Grub have to be installed on the partition? I'll edit my earlier post if it doesn't have to be on the partition so it doesn't confuse anyone who reads your thread.

Happy Ubuntu-ing !

---

### Post by SkOrPn on 2011-11-28
> **drs305 said:**
> Glad it's working.

You can mark it SOLVED via the 'Thread Tools' link to the top right of the original post.

Does EasyBCD allow Grub to be written to the MBR of the Ubuntu drive, or does Grub have to be installed on the partition? I'll edit my earlier post if it doesn't have to be on the partition so it doesn't confuse anyone who reads your thread.

Happy Ubuntu-ing !

Hmm, good point. I believe, but don't quote me on this, that it gets written to the MBR. Maybe if I put a link to the guide I followed you can tell me more clearly exactly how/why this worked for me?

GUIDE to ***[Dual-Booting Ubuntu Linux and Windows 7 (with the Windows bootloader)]("http://neosmart.net/wiki/display/EBCD/Ubuntu")***

Just bypass the initial Ubuntu installation section (first 6 steps as I already had it installed) and go halfway down the page to the **"Adding Ubuntu to the Windows Bootloader"** section. I bypassed Step 1 since it wasn't working for me, lol, and started at Step 2 **"Once inside Windows 7, run EasyBCD"**. That is where I started from and it worked perfectly the rest of the way.

Still wish I knew how EasyBCD knows that there is a Ubuntu install and where it is located. It never asked me for location, paths, drive letters, partitions etc. It just instantly configured it the moment I selected Grub2 and named it. Nice... :D

Thanks again...

---

### Post by drs305 on 2011-11-28
Very nice link! Definitely one I'll bookmark - even though I don't use Windows.

It appears that Grub is installed normally to the MBR, then EasyBCD just puts the Windows bootloader back into the MBR, overwriting the Grub info that previously existed there.

If you wouldn't mind please mark the thread SOLVED with the 'Thread Tools' link near the top right of the original post. This post can be very helpful to others with the same problem.

---

