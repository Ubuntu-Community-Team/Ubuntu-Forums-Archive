---
title: "Misreported amount of RAM"
date: 2012-01-05
forum: General Help
---

### Post by MichaelGld on 2012-01-05
I just upgraded my RAM, going from 2GB to 4GB. POST and BIOS  now report 4GB. Once booting into 10.04, however, my system only shows a total of 3,024MB of memory as shown here:

```
michael@michael-desktop:~$ free -m -t
             total       used       free     shared    buffers     cached
Mem:          3024       2866        158          0        140        779
-/+ buffers/cache:       1946       1078
Swap:         5890          0       5890
Total:        8915       2866       6049
```Before I did the upgrade the system showed the proper amount. In addition, I had a 2GB swap partition, which I did not change. Now, the partition has grown to 5890MB. Can anyone tell me what is going on and how to fix it?

---

### Post by imachavel on 2012-01-05
sounds like your bios isn't reporting it correctly. It very well may be a bios problem. Anyway before a moderator comes and explains that I should be banned(or maybe not), I'm going to tell you that I don't know. Restart the pc, load the bios, before Os loads, f8 or f2 it. Look thoroughly, perform a memory test. Very possible you got bad ram. Did you buy ddr2 pc5300 ram? It is fairly standard, what model of computer do you have? What os linux ubuntu oneiric ocelot of the previous natty narwhal? If you give your computer model, I will find your mobo, and list the compatible ram that will work with the controllers that read the random access memory.

If your computer boots up, most likely your hard drive and processor and psu are good to go. Let's not confuse it. Thanks

---

### Post by efflandt on 2012-01-05
To use more than 3 GB, you either need 64-bit Ubuntu (or Windows) or a special 32-bit pxe kernel that can address more RAM.  For example I am using 64-bit 11.10 and it sees all my RAM other than what the kernel may have reserved (don't need swap):

```
efflandt@XPS-8100-1110:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          7930       2123       5806          0        352        973
-/+ buffers/cache:        797       7133
Swap:            0          0          0
Total:        7930       2123       5806
```

---

### Post by MichaelGld on 2012-01-05
I have four sticks of RAM @ 1GB each. My BIOS is reporting 4GB. Why do you say my BIOS is reporting it incorrectly? I did not buy DDR2 PC5300 RAM.  That's not the type my system uses. It's a home-built system; see my signature. Look under my avatar for my O/S information.

---

### Post by Mark Phelps on 2012-01-05
Your BIOS is reporting it properly, your OS can't use all of it -- if it is 32-bit. See the explanation provided by "efflandt".

---

### Post by imachavel on 2012-01-05
> **MichaelGld said:**
> I have four sticks of RAM @ 1GB each. My BIOS is reporting 4GB. Why do you say my BIOS is reporting it incorrectly? I did not buy DDR2 PC5300 RAM.  That's not the type my system uses. It's a home-built system; see my signature. Look under my avatar for my O/S information.

whoops

---

### Post by spacecheck on 2012-01-05
According to the manual for your mainboard:

jp.evga.com/support/manuals/files/122-M2-NF59.pdf

page 13,  the modules have to be the same types (brand, make model, color, smell, whatever) because they will be used for "dual-channel" (2x64=128bit access) support. Prior post is accurate about 32-bit system not able to recognize entire 4 GB of memory. 64-bit OS is a horse of a different (much more opulent) color.

BTW, Your sub-avatar cited OS does not indicate 32 or 64 bit...

Good Luck!

---

### Post by MichaelGld on 2012-01-05
I added the exact same model/size/speed RAM that I already had installed in my system. I am using 32-bit version of 10.04.

> **spacecheck said:**
> According to the manual for your mainboard:

jp.evga.com/support/manuals/files/122-M2-NF59.pdf

page 13,  the modules have to be the same types (brand, make model, color, smell, whatever) because they will be used for "dual-channel" (2x64=128bit access) support. Prior post is accurate about 32-bit system not able to recognize entire 4 GB of memory. 64-bit OS is a horse of a different (much more opulent) color.

BTW, Your sub-avatar cited OS does not indicate 32 or 64 bit...

Good Luck!

---

### Post by imachavel on 2012-01-05
I believe he just said that since you are using a 32 bit version of linux on a 32 bit processing bus, that no more then 3gb or ram can be addressed. Perhaps it is hard for your system to identify what it can not read. If I'm incorrect please don't ban me :confused:

---

### Post by MichaelGld on 2012-01-05
Since my CPU is 32-bit, I cannot use the 64-bit Ubuntu, right? If I re-install 10.04 32-bit while connected to the Internet, will that do the trick? Do any later versions of Ubuntu support >3GM of RAM?

Thanks for your help.

> **efflandt said:**
> To use more than 3 GB, you either need 64-bit Ubuntu (or Windows) or a special 32-bit pxe kernel that can address more RAM.  For example I am using 64-bit 11.10 and it sees all my RAM other than what the kernel may have reserved (don't need swap):

```
efflandt@XPS-8100-1110:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          7930       2123       5806          0        352        973
-/+ buffers/cache:        797       7133
Swap:            0          0          0
Total:        7930       2123       5806
```

---

### Post by spacecheck on 2012-01-05
Umm, your CPU is "**AMD dual-core 4800+" **which is guaranteed to be a 64bit dual core processor**, **so when you ask **"**I cannot use the 64-bit Ubuntu, right?**" **The answer has to be "Wrong!" Your mainboard was designed for an "AMD Athlon64 AM2 CPU".

You need to make sure the DIMMs are mated at least in pairs (slot 1+3 one brand, slot 2+4 the other brand), hopefully all are the same model & format, etc. Then you need to use the amd64.iso to install a true 64-bit system, which should recognize all the RAM.

Good luck!

---

### Post by imachavel on 2012-01-05
my mistake

**Operating Mode 32 Bit**Yes 	 		**Operating Mode 64 Bit**Yes
[http://products.amd.com/pages/DesktopCPUDetail.aspx?id=46&AspxAutoDetectCookieSupport=1](http://products.amd.com/pages/DesktopCPUDetail.aspx?id=46&AspxAutoDetectCookieSupport=1)

---

### Post by spacecheck on 2012-01-05
> If I re-install 10.04 32-bit while connected to the Internet, will that  do the trick? Do any later versions of Ubuntu support >3GM of RAM?

A 32-bit OS will run fine on an AMD 64-bit processor, but it will not be able to address 4 GB of RAM. You could easily install a 64-bit version of Ubuntu, but you cannot convert a 32-bit installation into a 64-bit version.

If you download the amd64.iso and then right click on it, you should be able to burn it to disk, then boot from it and replace 32bit with 64bit. With Internet access, you don't need to download the entire DVD.iso, but can let the livecd.iso suffice, as it should then pick up the rest of the system from the nearest mirror.

I'm sure you can find this to download, but I can set some links if you like.

---

### Post by imachavel on 2012-01-05
I'm confused? You said he boots from live cd, then downloads something?

---

### Post by spacecheck on 2012-01-05
No, since he already has a 32-bit system, I wrote:
> If you download the amd64.iso and then right click on it, you should be able to burn it to disk, then boot from itIf he boots from the amd64 livecd, he can use it to install the 64-bit version. I pointed out, that he doesn't
> need to download the entire DVD.iso, but can let the livecd.iso suffice,  as it should then pick up the rest of the system from the nearest  mirrorduring the installation, including the latest updates, if he so desires. The amd64 livecd.iso is only about 700 MB, s compared to a multi-GB DVD. 

Which would you prefer to have to download & burn to disk??

Have fun!

---

### Post by asasoft on 2012-01-05
You can try go to Synaptic and install linux-generic-pae and linux-image-generic-pae

---

### Post by spacecheck on 2012-01-05
> **asasoft said:**
> You can try go to Synaptic and install linux-generic-pae and linux-image-generic-pae
But this foregoing suggestion would not give you a 64-bit system and you would not "get the full benefit of the 64 bit architecture":

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

BTW, this thread should probably be marked "solved."

Have fun!

---

### Post by jwbrase on 2012-01-06
> **efflandt said:**
> To use more than 3 GB, you either need 64-bit Ubuntu (or Windows) or a special 32-bit pxe kernel that can address more RAM.

Not quite. Each *process* can only use 3 GB. You can address up to 4GB of memory total on 32-bit, unless you have PAE, in which case you can address up to 64 GB (but each process still only gets 3 GB (or whatever userspace size corresponds to the OS in question and kernel compile options used)).

That said, it's fairly typical for an OS not to report all of the available RAM, even without 32/64 bit issues coming into play. My family's desktop only reports having 3.25 GB (out of 4 GB) under 32-bit PAE WinXP, and 3.75 under 64-bit Linux. My laptop reports 2.9 out of 3 GB under 64-bit Linux. 

I'm more concerned by the extra few gigabytes that have appeared in the OP's swap partition.

---

### Post by MichaelGld on 2012-01-06
I did that, but when I rebooted. I was presented with a white on black background text-only screen asking for my login. I input my user name and password, which it accepted, but I was left with only a prompt - no desktop. Any idea how to fix that?

On a positive note, I tried the "free" command, and the total amount of memory was listed as 4GB, so it appears we are on the right track.

Thanks for your help.


> **asasoft said:**
> You can try go to Synaptic and install linux-generic-pae and linux-image-generic-pae

---

### Post by MichaelGld on 2012-01-06
OK, I got it working now. There are two more package necessary to make it work. 
 linux-headers-generic-pae and linux-headers-<version number>-generic-pae. 

Now my system sees the 4GM of RAM. I still don't know how my swap space adjusted itself.

```
michael@michael-desktop:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          4021       3839        182          0         60       1980
-/+ buffers/cache:       1797       2224
Swap:         5890          0       5890
Total:        9912       3839       6073

```Thanks for the help.


> **asasoft said:**
> You can try go to Synaptic and install linux-generic-pae and linux-image-generic-pae

---

### Post by dcstar on 2012-01-07
> **jwbrase said:**
> ........
That said, it's fairly typical for an OS not to report all of the available RAM, even without 32/64 bit issues coming into play. My family's desktop only reports having 3.25 GB (out of 4 GB) under 32-bit PAE WinXP, and 3.75 under 64-bit Linux. My laptop reports 2.9 out of 3 GB under 64-bit Linux. 

The manufacturers of most 32-bit MBs will not waste money on the extra hardware required to allow resource address mapping above 4GB (unless it is a server board deliberately designed for such a thing), also MBs designed to only take 4GB maximum RAM will also rarely have that extra hardware.

64-bit MBs designed to take more than 4GB RAM can allow some hardware to be mapped above 4GB, but to maintain 32-bit compatibility some things must remain mapped under 4GB so that essentially wastes the address space the RAM could use.

Once MBs are designed only to use 64-bit OSs and the ye-olde IBM-PC basic address reservations in the first GB of RAM are no longer used then we all may see every byte of RAM available for use!

---

### Post by spacecheck on 2012-01-07
> **dcstar said:**
> The manufacturers of most 32-bit MBs will not waste money on the extra hardware required to allow resource address mapping above 4GB (unless it is a server board deliberately designed for such a thing), also MBs designed to only take 4GB maximum RAM will also rarely have that extra hardware.

64-bit MBs designed to take more than 4GB RAM can allow some hardware to be mapped above 4GB, but to maintain 32-bit compatibility some things must remain mapped under 4GB so that essentially wastes the address space the RAM could use.

Once MBs are designed only to use 64-bit OSs and the ye-olde IBM-PC basic address reservations in the first GB of RAM are no longer used then we all may see every byte of RAM available for use!
Of course, in this instance, it is a mainboard designed for amd64 processors which claims (in the manual) to allow installation and use of up to 8GB RAM in 4 DIMMs for dual-channel access.

Have fun!

---

