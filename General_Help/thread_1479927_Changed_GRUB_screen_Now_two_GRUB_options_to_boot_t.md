---
title: "Changed GRUB screen: Now two GRUB options to boot to Ubuntu"
date: 2010-05-11
forum: General Help
---

### Post by MorrisseyJ on 2010-05-11
Hi, i was wondering if anyone can explain this to me (i can't seem to run a suitable search on google to query this):

My GRUB screen has changed. Previously it looked like this:

> Ubuntu, with Linux 2.6.32-22-generic-pae
Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)
Memory test (memtest 86f)
Memory test (memtest 86f, serial console 1....0)
Microsoft Windows XP Home Edition (on /dev/sda2)Now it looks like this:

> Ubuntu, with Linux 2.6.32-22-generic-pae
Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)
Ubuntu, with Linux 2.6.32-22-generic-pae
 Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)
Memory test (memtest 86f)
Memory test (memtest 86f, serial console 1....0)
Microsoft Windows XP Home Edition (on /dev/sda2)So for some reason my GRUB now has a second option to boot to Ubuntu. I am not sure what i did that precipitated this. There is nothing distinctive that i remember doing before it started happening.

Could anyone tell me why its happened, if its a problem and how i fix it?

Thanks.

---

### Post by MorrisseyJ on 2010-07-01
From the last time i posted this issue i have reinstalled 10.04. Clean reinstall ran without this issue for some time but now as I have just run the updater, installed recommended updates and done the mandatory restart i got this screen again with two GRUB options to boot to Ubuntu.

Anyone have any ideas what this means, if its a problem and/or what might have caused it?

---

### Post by laithbsoul on 2010-07-01
are you sure the second option isn't a different version when you update after fresh installing it'll put the last version on there i'm pretty sure there a way to clear it mine is the same way any way what i'm saying is that it's no big deal

---

### Post by MorrisseyJ on 2010-07-01
Two things:

1. i have updated numerous times before and this has not happened, so i don't think that its just the update.

2. Assuming you're correct, should i be booting to the second option in order to be working on the updated version?

---

### Post by ShinIori319 on 2010-07-01
Is there any tool to modify the GRUB options? I've tried many, but none seems to work (they don't show the OS list). With the latest kernel update (I got it this morning) I now get three Linux options (with their Recovery modes) in my list. Any way to safely remove the older kernels?

[COLOR=Red]**EDIT: **[/COLOR][COLOR=Black]After "googling"[/COLOR] a bit, I found a solution that might help us both with this.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

### Post by MorrisseyJ on 2010-07-01
Great, this is really useful. I hadn't even realised that what i was seeing was two kernels. 

With this in mind can you answer my question about which GRUB option i should choose. The two that i have are identical in the GRUB menu. Should it be the top one, or the second one?

---

### Post by laithbsoul on 2010-07-01
when i say update i mean in the update manager not like from 8.04 to 10.04 idk for sure if that's it but i have 2 options as well and always have you just boot the one it automatically highlights to boot from

---

### Post by laithbsoul on 2010-07-01
ya thats what i meant is not a different version but the old kernel

---

### Post by MorrisseyJ on 2010-07-01
Ok great. So keep two kernels (as per [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)) and boot from the top one on the list - unless your GRUB highlights another start option first.

Thanks for the input and it'd be great if you can let me know if anything else comes up on this front.

---

### Post by teisho on 2010-07-01
Here's a lot of technical jargon.  If you want, skip to the end for the simple answer.

Ubuntu and most other linux distros used to use grub 1.0, which would have a file named menu.lst in /boot/grub that you could easily edit, and just sa easily make your system unbootable.

Now grub configuration is kept in /etc/grub.d/ and is dynamically transferred to /boot/grub/ whenever apt changes the kernel.

The part the writes the kernel select options is located in /etc/grub.d/10_linux, and if you open it with a text editor, you'll notice that it looks in the kernel directory and creates an entry for each of the kernels located there.

You probably have a slightly newer kernel installed with a version number change not significant enough to have a different grub texts.  You can see the installed kernels in /boot/ - they're the files that begin with vmlinuz.  If you've got two in your grub menu, you should have two vmlinuz files in your boot directory.

Sooooooooooooo, the simple answer is to remove the extra kernel. It's kept there so you can go back if the new kernel doesn't work out.  It worked out, congratulations!  Get rid of the old kernel:
[LIST]
[*]Use "dpkg -l | grep linux-image" to find the package names of all the installed kernels
[*]Use "sudo apt-get purge <packagename>" or aptitude/synaptic to completely remove the old kernel package
[/LIST]
Once you've removed the kernel with apt or one of its graphical children, the grub menu should get recompiled, and the old kernels will be gone from your list.

---

### Post by laithbsoul on 2010-07-01
ya that's exactly what I was thinking

---

### Post by MorrisseyJ on 2010-07-01
Thanks for this teisho. In /boot/ i do have two kernels: 2.6.32-22- and 2.6.32-23-.

One more question: You say that my new kernel has 'worked'. Do i know this because it booted or should i wait to see if everything works for a while (i.e. no crashes). I seem to see a lot of posts online with Lucid giving problems and people staying on old kernels. 

Am i wrong here or does effective booting mean that it has, as you say, 'worked'?

---

### Post by Leppie on 2010-07-01
it's always best to keep 2 kernel versions installed. even if you've been using a kernel for a while, you never know what you'll run into and with only 1 kernel version the system might be much harder to get up and running again.

---

### Post by MorrisseyJ on 2010-07-01
Wonderful. Thank you all for all the input.

---

### Post by MorrisseyJ on 2010-07-01
Wonderful. Thank you all for all the input.

---

### Post by teisho on 2010-07-02
> **MorrisseyJ said:**
> Thanks for this teisho. In /boot/ i do have two kernels: 2.6.32-22- and 2.6.32-23-.

One more question: You say that my new kernel has 'worked'. Do i know this because it booted or should i wait to see if everything works for a while (i.e. no crashes). I seem to see a lot of posts online with Lucid giving problems and people staying on old kernels. 

Am i wrong here or does effective booting mean that it has, as you say, 'worked'?

This is correct.  If your computer boots up fine, then your new kernel is working.

Like Leppie says, it's a good idea to keep two kernels around just in case.  Ubuntu is very good at testing their new kernels before they go out, but the actual kernel files are small and it doesn't hurt anything to let them stay there.  The newest kernel will always be the one that is used when your grub_wait times out.

Probably best to start worrying about grub cosmetics when you have three or more options to choose from.  I actually think that Ubuntu might remove later kernels when installing new ones.  I've never heard this before, but I can't remember ever seeing more than two kernel versions in an Ubuntu grub boot list.

Anyways, glad I could help.

---

### Post by Leppie on 2010-07-03
> **teisho said:**
> ...but I can't remember ever seeing more than two kernel versions in an Ubuntu grub boot list.
that's because you most probably remove older versions when a new kernel is installed.
i once did a safe-upgrade:
```
sudo aptitude safe-upgrade
```which installed a new kernel, but at the same time removed the old kernel as well. a bit off topic, but i wouldn't say that's a safe upgrade...
anyways, apt-get upgrade doesn't remove older kernel version so you could have like 10 installed on your system and appearing in the grub menu. but with some minor modifications you can limit the amount of entries to 2 or 1 (without actually removing the older kernels from your system).

---

