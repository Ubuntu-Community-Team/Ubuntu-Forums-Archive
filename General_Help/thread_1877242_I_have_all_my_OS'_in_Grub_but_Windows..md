---
title: "I have all my OS' in Grub but Windows."
date: 2011-11-07
forum: General Help
---

### Post by irv on 2011-11-07
I know what I did, but need some help to fix it. See screen shots:

As you can see I have three Linux OS' installed. The last one I did was Elive. Without thinking i set the boot drive sda1 to reiserfs file system. Because of this I can boot all Linux's but now I can't see Win7 in the grub. It is still there as you can see in gparted.
To fix this I believe I will need to boot with the Windows CD and run some sort of fix. Then I will need to run a fix on the grub from a live Linux cd.

Am I right about this? Can someone guide me with a step by step process?

Thanks all you good guys and gals out here.

I have done this before but it was a long time ago so I forgot how to do it.
[ATTACH]206614[/ATTACH]    [ATTACH]206615[/ATTACH]

---

### Post by Mark Phelps on 2011-11-07
Since it is a 100MB partition, I'm guessing you're running Win7, right?

That being the case, boot from your Win7 disk.  You should see an option to Repair the PC.  Select that. You should then get a list of options, one being Startup Repair.  Select that.

Do this process three times. Not once, three times.

Then, when you remove the disk and reboot, you should go straight into Win7.

Once you get that working, you will need to come back to see how to restore access to the other OSs.

---

### Post by oldfred on 2011-11-07
Before you run the Windows repairs as suggested by Mark Phelps you need to move the boot flag back to sda2. Your boot files were in sda1 and it was flagged as boot. Windows 7 uses a separate 100MB boot/recovery(window repair) partition so you can encypt the main install.

That should fix Windows, but will reinstall the Windows boot loader to the MBR.

Depending on what system you want in control of MBR you will have to reinstall a grub boot loader. Ubuntu uses grub2 since 9.10 and has a great os-prober that finds other operating systems to boot. Not sure about your other installs.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by irv on 2011-11-07
Thanks for all the help on this one, but I was just spinning my wheels. 
When I booted with Win7 CD and running Bootrec.exe /fixboot I got a message that it could not find. When I run bootrec.exe /fixmbr, it ran OK. I did a bootrec.exe /help and both commands were type right. When I tried to reboot the computer would not boot at all.

I just installed one of the Linux OS' and it fix the grub. I have all three Linux OS' but still no Windows.

I could of just install Windows again and maybe go everything working, but I can't even remember the last time I went into Windows so I guess it no big loss.

---

### Post by oldfred on 2011-11-07
Windows only repairs the partition with the boot flag, as that is the 'active' partition. 

Did you move boot flag? Or from a Windows repairCD set the active partition to your Windows partition?

---

### Post by irv on 2011-11-07
> **oldfred said:**
> Windows only repairs the partition with the boot flag, as that is the 'active' partition. 

Did you move boot flag? Or from a Windows repairCD set the active partition to your Windows partition?

How do I set the active partition?

---

### Post by garyed on 2011-11-08
I don't know much about Windows but I assume that sda1 needs to be NTFS & thats where the boot flag needs to be. I'm dual booting Win7 & just checked my partitions & sda1 is my Windows system partition NTFS 200mb & flagged as boot (59mb used) & sda2 is NTFS 100gig7 then the ext4 partitions. If you haven't already I would change sda1 to NTFS & set the boot flag there.In Gparted highlight sda1 & go to partition/manage flags to set boot flag.  
Then try to restore Windows boot again.

---

### Post by irv on 2011-11-08
I see what changed on my setup in gparted. My NTFS was sda1 and now it is sda2. And the flag was not set to Boot. I set it to boot and now I will try to boot from the Win7 CD.
[ATTACH]206660[/ATTACH]

---

### Post by oldfred on 2011-11-08
If Windows repairs not do not work post results.txt, but I expect Windows repairs to work.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by irv on 2011-11-08
Ok I can mark this one solved. After setting the boot flag in sda2 where Windows was installed and booting with the Win7 CD and running bootrec.exe with /fixboot and /fixmbr, and running the repair on Windows it booted into windows. Then I had to install Ubuntu 11.04 because I was having problem with 11.10 (No network). After installing I had everything back in my grub.
I am running Kubuntu 11.10, Ubuntu 11.04, Mint, Win7 on a 500gig HD. I plan to replace Ubuntu 11.04 with 12.04 beta next month to do some bug testing.

While I am add it, can I just got from 11.04 to 12.04 or do I have to goto 11.10 first? I have had so many issues with 11.10 I want to avoid it.

---

### Post by oldfred on 2011-11-08
Glad that worked.

Only long term LTS versions can skip to the next LTS. Each 6 month release only upgrades to the next 6 month release. 

I always do clean installs to a new 20 or 25GB partition so I can still copy some old settings over if desired.

---

### Post by irv on 2011-11-08
> **oldfred said:**
> Glad that worked.

Only long term LTS versions can skip to the next LTS. Each 6 month release only upgrades to the next 6 month release. 

I always do clean installs to a new 20 or 25GB partition so I can still copy some old settings over if desired.

I do the same (clean install), but I couldn't get Ubuntu 11.10 to install because it would not find my Ethernet card after installing, and I needed a network connection to install my wireless driver. It saw the Ethernet card from the live CD but not after it was installed.

What I did to work around this was to install 11.04 and then do an upgrade to 11.10 but got some error during the upgrade and couldn't even send or same bug reports because I lost my network again and couldn't even write to the hard drive. 11.10 has some bad bugs.

I actually got it going right now, but I now I am going to have some issues come up because I didn't get a clean install. This is why I am waiting for 12.04 to see if some of these issues are fixed.

By the way thank for your input on this thread.

---

