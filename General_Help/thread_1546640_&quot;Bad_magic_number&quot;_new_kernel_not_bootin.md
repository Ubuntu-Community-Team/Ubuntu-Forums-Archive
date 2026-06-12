---
title: "&quot;Bad magic number&quot; new kernel not booting."
date: 2010-08-05
forum: General Help
---

### Post by Neobuntu on 2010-08-05
Ubuntu 10.04 -

What in the world is the problem? I can find nothing to even start, in the right direction. 

I simply agreed to the Upgrade Managers request, and now I can't boot the newly installed kernel.

I went back in with the old one and reinstalled the new Kernel, with Synaptic. Still, it will not boot.

What happened? I "Googled" and nothing. 

I tried sudo update-grub and it still doesn't boot. 

Please help?

---

### Post by Neobuntu on 2010-08-05
It also says, I need to "load the kernel first". :(

WTF? Why would a new kernel, from the Update Manager upgrade, not load?

Obviously, if we can solve the Invalid magic number error, we can then boot the kernel.

---

### Post by Neobuntu on 2010-08-05
Kernel linux-image version 2.6.32-24.39

---

### Post by Neobuntu on 2010-08-06
I completely removed this kernel, rebooted and then reinstalled it, watching carefully for errors. There were no errors. This was time consuming. 

It still does not work. Same grub errors as before. Not a good thing, for newbies.

So, bump.

---

### Post by ibuclaw on 2010-08-06
I assume the "magic number" it is referring to is the filesystem magic number. Boot from the liveCD and try running a fsck on boot partition.

Regards

---

### Post by Neobuntu on 2010-08-11
I sincerely thank you for the suggestion. However, the fsck with the live CD was flawless.

Every time I turn on my Ubuntu 10.04 system, it fails to boot the kernel. I back out and go down to the last regular kernel listing and boot an old kernel, that may now be conflicting with new upgrades (parts).

I always told my Windows refugees, this kinda of thing would be fixed within hours. I'm left with no place to start.

Please help.

Still: "Bad magic number" and "load the kernel first".

---

### Post by Neobuntu on 2010-08-12
There are bug reports about syntax errors where a " is supposed to be a ""; but that is not a problem, in my system. There are related bugs; but they also seem to be different and older issues.

Kernel fails to launch. Same errors at Grub.

HELP!

---

### Post by Neobuntu on 2010-08-13
Grumble :(

WARNING: Reinstalling Grub 2 (grub-pc) didn't work!

Purging and installing didn't work.

Reinstalling again, didn't work.

Purging and installing legacy Grub didn't work(yet).

Grub didn't work at all with the above.

Purged grub grub-common and grub-pc.

Installed legacy grub. Chose package maintainers config

Ran 'Grub' and did...

**ADDENDUM:** See GRUB 2 fix link and instructions post below.

root (hd0,0) ......NOTE: This would be root(hd0,1) if Ubuntu is on you second partition.
setup (hd0) .......NOTE: DON'T USE MORE THAN ONE NUMERAL HERE or it will write over your stuff! (hd0) is the MBR area.
quit

update-grub again, for good measure.

Now, I have Grub legacy and the NEW Kernel still, will not boot!
The older kernel is accessible again. :) Whew!
I'm currently out of band :( , using GRUB legacy, on my clean installed 10.04.

Therefore, it's NOT grub 2. I'm not using GRUB 2, at this time and the new kernel STILL, will not boot.


Not GRUB syntax error (though that was some peoples bug)
Not GRUB 2

Any ideas?

When will the next kernel be available?
Where can I find this out?
How can we define the problem?

I KNOW, zero newbies would make it through, what I just did. wth!?

---

### Post by sdennie on 2010-08-13
Do you get any output from the following commands:

```

cd /
md5sum -c /var/lib/dpkg/info/linux-image-2.6.32-24-generic.md5sums | grep -v "OK$"

```

---

### Post by Neobuntu on 2010-08-13
Hey, thank you so much!

I'm very frustrated at the time loss here and I'm trying to watch what I say. You're helping me; a lot!

Those commands paused a few seconds, did not produce any output, as it then went back to prompt.

What I've been doing:

I had to try to get back up to Grub2. Booting from CD is a big time vampire. Yet, I tried it MANY ways and on reboot, only got something like:

"font file format error" and a GRUB (2) prompt and with no, at the prompt, help.

I followed FOUR different, how-to restore grub, instructions; with a live CD. I Checked every step; exactly and still, it would give me no menu.

My first attempt to get back to a working menu with GRUB (legacy), just like I successfully did earlier toady, did not work!

I set root and used 'find' command and the tab key to find the names of the kernel and initrd, that work (last kernel ...-22. The new one ...-24 STILL never works.) Therefore, if I get a GRUB prompt with GRUB legacy, I can hack it out, and get it to boot. However, the error was different.

Remembering (which sucks to have to remember) something like (GRUB LEGACY):

root (hd0,0)
kernel /boot/vmlinuz(hit 'the TAB key' here and finish the whole file) ro quiet splash root=/dev/sda1
initrd /boot/initrd(hit 'the TAB key' here and finish the whole file)
boot

...and  

Then typed 'help' at the grub prompt. I also know...

root (hd0,0)
setup (hd0)

Do those, thinking it might not be writing correctly to the MBR.
Upon reboot, at least, I have legacy menu working again! (not the new kernel).

I seems, I have to simply reissue/reinstall those command, over and over, checking for a menu each time after a boot. This is now on GRUB legacy. Perhaps that will save someone some time. I beats booting the live CD; if you, at least, get a working GRUB prompt. (time eater). 

Problem #1. Why doesn't grub-pc (GRUB 2) install or reinstall or upgrade from grub(legacy)? I did NOT FAIL to follow the Ubuntu directions, explicitly. 

ADDENDUM: See what GRUB 2 reinstall instructions worked, below.

Problem #2. New kernel, no booty. The GRUB legacy lines are EXACTLY the same as the old kernel that boot, except for -24 in place of -22 in two places. Exactly. I doubt it's a grub issue.> title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		8dcefa3c-db54-4793-8fa6-e5587d9ab4ed
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=8dcefa3c-db54-4793-8fa6-e5587d9ab4ed ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		8dcefa3c-db54-4793-8fa6-e5587d9ab4ed
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=8dcefa3c-db54-4793-8fa6-e5587d9ab4ed ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

---

### Post by Neobuntu on 2010-08-13
Currently trying just (and not the check command suggested):

grub-install /dev/sda

Again, with the idea that there's still some old non-ext4 code in the MBR that needs to be correctly written. Perhaps too, the new kernel matches all that.

Again, I was on a clean 10.04 install (now with GRUB legacy) and it is EXT4.

**ADDENDUM:**
After many hours, I just reinstalled GRUB legacy, again. GRUB "2" kept giving me the, "Font file format error!"

**ADDENDUM: **I think the MBR was not correctly written with GRUB 2 data (grub-install /dev/sda) NOT sda1. Plus, if you do this from the live CD, you may need to designate the root. Between grub-install and the /dev/sda1.

> sudo apt-get install grub
or sudo dpkg-reconfigure grub
sudo grub-install /dev/sda <-...and NOT /dev/sda1
sudo update-grub
I purged that new Kernel. Ubuntu is broken.

---

### Post by Neobuntu on 2010-08-14
-----------------I got GRUB 2 fully reinstalled (don't reinstall to attempt fixing the kernel) by referencing:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

..and see #12. It purges and shows reinstall.

AND, I did install-grub /dev/sda
_______________________^--No numeral! Just sda (or sdb if you're doing that.)
and update-grub for good measure. Also, if you're not doing this from the root directory, also specify your root target (see Live CD recovery and grub 2 reinstall.)

I also, commented out the line in the new GRUB 2 config file; so the menu would not be hidden. Hold the shift key, during boot, if you haven't.

--------------------------------------------------------------------------------------------

Getting a "Invalid magic number" error on the newest kernel, still.

All I did originally, was agree to upgrade with upgrade-manger.

The default, newest kernel fails for newbies. I'm still manually selecting the older kernel. :( Why?

Note: There was a syntax error where " (missing quote), was supposed to be "" ; but that is NOT the bug, with this problem.

---

### Post by Neobuntu on 2010-08-25
Last night, I permanently removed all other kernels and parts. Then reinstalled the subject kernel, and same error.

---

### Post by Neobuntu on 2010-08-29
SOLUTION (myself) - Turn UDMA off, in my computers BIOS settings. (Dell D8200 + Seagate 200GB PATA)

The question was, why this system, just this kernel, and not my other computer with same kernel. If you're having this problem, here's what fixed it, for me.

If not Grub(2) and not the kernel, then what's left? THE BIOS!

Once I started to painstakingly test things, in the BIOS; that might affect GRUB booting, I finally just turned UDMA off; just to be sure and viola! It booted the new kernel; for the first time.

Now, I think why this happens, is GRUB will take the UDMA settings from the BIOS, and if it's wrong, no booty. By turning UDMA off (which might be trouble for other duel booted OS systems, I run just Ubuntu alone), or actually setting it to the WRONG UDMA mode (I read), forces GRUB to call the CORRECT UDMA mode; from the actual drive!

*** (Perhaps this kernel build failed to do something different, with UDMA; because the other kernels worked!) ***
> 
hdparm -i /dev/sda1
(Yours might not be sda1) 

...reports UDMA 5, as active. Confirming the correct (faster) UDMA drive setting; even though it's off, in my DELL BIOS.

---

### Post by bcobb10b on 2012-02-14
> **Neobuntu said:**
> SOLUTION (myself) - Turn UDMA off, in my computers BIOS settings. (Dell D8200 + Seagate 200GB PATA)

The question was, why this system, just this kernel, and not my other computer with same kernel. If you're having this problem, here's what fixed it, for me.

If not Grub(2) and not the kernel, then what's left? THE BIOS!

Once I started to painstakingly test things, in the BIOS; that might affect GRUB booting, I finally just turned UDMA off; just to be sure and viola! It booted the new kernel; for the first time.

Now, I think why this happens, is GRUB will take the UDMA settings from the BIOS, and if it's wrong, no booty. By turning UDMA off (which might be trouble for other duel booted OS systems, I run just Ubuntu alone), or actually setting it to the WRONG UDMA mode (I read), forces GRUB to call the CORRECT UDMA mode; from the actual drive!

*** (Perhaps this kernel build failed to do something different, with UDMA; because the other kernels worked!) ***
 

...reports UDMA 5, as active. Confirming the correct (faster) UDMA drive setting; even though it's off, in my DELL BIOS.

Still a valid solution for older PCs (in this case an ancient Dell Optiplex GX280 resurrected for file sharing in a home network).  I wasted a day trying to sort out why the boot issue occurred after Ubuntu 11.10 update; finally gave up, reformatted hard drive & installed Xubuntu - & encountered same issue after first update this morning.  Grrrr.  Now smiles!!!

Thanks for reporting this solution -- I was beginning to doubt my sanity!!

Bill Cobb

---

### Post by drink on 2012-12-18
I'm actually *using* UDMA. Is there a fix for this that doesn't involve turning off things I'm using, or booting the old kernel manually like I've been doing? I'm having this problem in quantal!

---

### Post by oldos2er on 2012-12-18
Old thread closed, please start a new thread.

---

