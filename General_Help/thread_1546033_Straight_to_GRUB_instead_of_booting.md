---
title: "Straight to GRUB instead of booting"
date: 2010-08-04
forum: General Help
---

### Post by nhv on 2010-08-04
Hi,

Since this morning my system refuses to boot Ubuntu 9.04 installed in Vista using Wubi.

It has been working for months, but now it fails to start. I get to the windows bootloader screen. When booting Ubuntu (pre-selected) it goes straight to GRUB. Performed test several times: it is consistent.

Any idea how to get Ubuntu to boot again?

Thanks for your help.

Niels.

---

### Post by phdb on 2010-08-04
It seems like you have re-installed windows or executed some kind of 'repair' from the install disk of your windows.
This means that the MBR is overwritten (a certain company in Redmont indeed assumes that only their system is on your computer and bluntly overwrite the MBR).

So what to do?
You should re-install grub.

Follow the instructions here:[]("https://help.ubuntu.com/community/Grub2") [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Ph.

---

### Post by nhv on 2010-08-05
Hi,
 
Thanks for your reply and link to the GRUB page. I've read the pages and tried a few things.
 
Just some additional input. When choosing Ubuntu from the windows bootloader, I arrive in the command line mode which shows:
 
GRUB4DOS 0.4.4 2009-04-21 Memory: 639K / 2022M, MenuEnd: 0x434E6 [Minimal BASH-like line editing is supported. For the first word, TAB lists the possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits.]
 
The commands referenced in section "Using CLI to Boot" do not work for me. The "set" command is not in the list of commands I can execute (setenv and setkey are known).
 
When typing errnum straight after arriving in the CLI it says ERRNUM is 0.
 
When doing ls /boot/ and hitting TAB I see a range of files (bcd, bootsdi, bootfix.bin, bootstat.dat, etfsboot, memtest.exe and a range of language subdirs), but no vmlinuz or vmlinuz-version.
 
What I don't understand is: when you suggest I should re-install GRUB, I don't see how I could do this. I mean, I don't have a real dual boot with GRUB as my main bootloader. With Wubi, I thout the bootloader remains the windows one, which calls grub when selecting Ubuntu.
 
I did not run any recovery process or crappy windows update process. In fact I did not boot in Windows for weeks. And there was no windows boot in between my last succesful Ubuntu boot and the moment it started to fail. The only thing was a total freeze of Ubuntu which I had to kill pressing the powerbutton.
 
Any ideas?
 
Thanks,
 
Niels.

---

### Post by bcbc on 2010-08-05
> **nhv said:**
> Hi,
 
Thanks for your reply and link to the GRUB page. I've read the pages and tried a few things.
 
Just some additional input. When choosing Ubuntu from the windows bootloader, I arrive in the command line mode which shows:
 
GRUB4DOS 0.4.4 2009-04-21 Memory: 639K / 2022M, MenuEnd: 0x434E6 [Minimal BASH-like line editing is supported. For the first word, TAB lists the possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits.]
 
The commands referenced in section "Using CLI to Boot" do not work for me. The "set" command is not in the list of commands I can execute (setenv and setkey are known).
 
When typing errnum straight after arriving in the CLI it says ERRNUM is 0.
 
When doing ls /boot/ and hitting TAB I see a range of files (bcd, bootsdi, bootfix.bin, bootstat.dat, etfsboot, memtest.exe and a range of language subdirs), but no vmlinuz or vmlinuz-version.
 
What I don't understand is: when you suggest I should re-install GRUB, I don't see how I could do this. I mean, I don't have a real dual boot with GRUB as my main bootloader. With Wubi, I thout the bootloader remains the windows one, which calls grub when selecting Ubuntu.
 
I did not run any recovery process or crappy windows update process. In fact I did not boot in Windows for weeks. And there was no windows boot in between my last succesful Ubuntu boot and the moment it started to fail. The only thing was a total freeze of Ubuntu which I had to kill pressing the powerbutton.
 
Any ideas?
 
Thanks,
 
Niels.
Yes you need the windows bootloader.

Have you tried mounting the root.disk from a live CD to see if it's alright? If you can mount it you can also backup important data in it. 

Wubi is vulnerable to hard shutdowns, as it's running off a single file. Instead (for future reference), try holding Alt-SysRQ and pressing REISUB.

If you can't mount the root.disk, you might have to run chkdsk on windows. See the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#Corrupted NTFS filesystem") for more info. (There's a section on how to loop mount the root.disk in there too).

---

### Post by nhv on 2010-08-06
Thanks for the hints.
 
I've tried a chkdsk /r /f last night (which took a few hours). This beast fixed one or two files, but these were irrelevant for the big Wubi file. So nothing happened.
 
I will try to boot from a live CD, mount the root disk and do a fsck to see if that helps.
 
And in the meantime, I'll put sticky note on my screen saying ALT+ SYSRQ + R + S + U + B :)
 
Will keep you posted.

---

### Post by nhv on 2010-08-08
Update: I managed to boot a live-cd and mount the windowz partition on /dev/sda1.

However, there is no root.disk in the ubuntu directory. So, no way to mount that disk and perform an fsck or recover files.

What is strange to me is that in the GRUB commandline I can ls /boot but vmlinuz is not there. It would not help me if I did find it because the GRUB shell does not know the linux command... And I can see there is no root.disk where people expect it to be.

Could files be located somewhere else?

Any other suggestions I could try?

Thanks,

Niels.

---

### Post by nhv on 2010-08-11
I've basically given up and kicked Wubi and Vista from my system. I'm now running Win7 and Ubuntu 10 next to eachother.
 
Wubi is nice for the unfortunate with a windows monopoly on their system wanting to give Ubuntu a spin. However, since it is contained in a single file and files can get corrupted, especially in Windows, one should not use it for productivity.
 
Good riddens. 
 
No data died in the process, since everything is on separate partitions.
 
Niels.

---

### Post by bcbc on 2010-08-11
> **nhv said:**
> I've basically given up and kicked Wubi and Vista from my system. I'm now running Win7 and Ubuntu 10 next to eachother.
 
Wubi is nice for the unfortunate with a windows monopoly on their system wanting to give Ubuntu a spin. However, since it is contained in a single file and files can get corrupted, especially in Windows, one should not use it for productivity.
 
Good riddens. 
 
No data died in the process, since everything is on separate partitions.
 
Niels.

Cool. Yes, wubi has it's uses, but you're better off doing the traditional dual boot. It doesn't make you immune - you still want to avoid hard shutdowns, and backup data (it's lucky you already had a separate data partition, but remember that drives can fail, so a backup is always a good idea).

But at least your whole ubuntu installation isn't going to disappear :)

---

