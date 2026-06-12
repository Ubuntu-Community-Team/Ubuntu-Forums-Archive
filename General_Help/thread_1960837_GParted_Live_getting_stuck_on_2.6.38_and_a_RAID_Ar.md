---
title: "GParted Live getting stuck on 2.6.38 and a RAID Array"
date: 2012-04-18
forum: General Help
---

### Post by fragamemnon on 2012-04-18
Greetings,

I'm having a hard time with a x64 Ubuntu 11.04 after receiving the famous 2.6.38 Kernel and a day after that, a power outage.

The thing is that this machine is controlling a 12HDD array (currently 5x2 (160GB each) in RAID 0+1) and additionally has 2 hot-plug slots (only 1 in use).

After trying to boot up right when the power went back, the timer on the Grub wouldn't start so no automatic choice was taken. I thought "fine, I'll simply hit Enter this time" so I attempted to boot up normally. All was good for the GUI seemed.. odd /I'm not a long-experienced Linux user so I presume it's just a basic old version of X/. Aaand it wouldn't accept my user account password, neither the password from the second account. A wrong password is not the case, I guarantee that. 

I inserted the Ubuntu x64 client disc in attempt of a LiveCD boot - but nothing happened. After the Ubuntu screen with 4 dots, initramfs reported that no init was found, e.g. "Try passing init= bootarg" Which reassured me that it was gone. Recovery mode, other kernels - none of them happened.

Then I decided to make a bootable USB with gparted /went flawless/ and as I tried to run the default instruction set, after quite a long initiation and scan (as you can probably imagine with that array), it simply gets stuck after scanning what seems to be the last hard drive in it. The last lines I see are that DV has completed and it's asynchronous. After that nothing happens - I don't see/hear any activity from the array as well.

Could it possibly be a boot record failure, or perhaps something in the kernel? I am starting to doubt it's the array since it shouldn't mess up with the OS itself (I've installed Linux on the internal HDDs (RAID 1) of the computer, not the array). Or perhaps a bad drive? Wouldn't it still work then as it's mirrored on the second HDD?

Thank you for your time and help in advance!

Cheers,
Vesselin

P.S. I only have a 128MB USB stick atm, so I'll try getting the OS on a bigger one tomorrow. Still, any sooner workaround or just information on this would be much appreciated! I'd like to see your suggestions and further investigate the possible reasons - after all knowledge is power. :P

---

### Post by oldfred on 2012-04-19
I do not know RAID, but:

Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.

If using liveCD/USB install this as is used to only be in the alternative or server install ISO not the standard desktop liveCD as desktops do not normally have RAID.

[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)
Software RAID w/mdadm driver
[https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html)
[https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html)

---

