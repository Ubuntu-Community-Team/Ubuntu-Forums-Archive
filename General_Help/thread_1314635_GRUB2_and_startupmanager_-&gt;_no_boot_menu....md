---
title: "GRUB2 and startupmanager -&gt; no boot menu..."
date: 2009-11-04
forum: General Help
---

### Post by Alexandre Charoy on 2009-11-04
Hi!

I installed Ubuntu 9.10 over my Jaunty installation today, as a dual boot along with Windows Vista.
Everything went fine, I restarted after the installation and the boot menu was there, working fine. Then after doing some configuration stuff, setting up things and getting some packages, I remebered startupmanager, and installed it. I changed the resolution of the boot loader menu using the package, and restarted in order to check it.

But instead of the boot menu, I get the following two messages, and then Ubuntu starts, without prompting me for what OS I want to start:
GRUB loading.
vga=796 is depreceated. Use set gfxpayload=640x480x8,640,480 before linux comm and instead.

So... after this error message Ubuntu 9.10 boots (without any problem), but I need to access my Vista.

I think that startupmanager is maybe not compatible to GRUB2?
And how do I restore/correct GRUB2?

Thanks,
Alex

---

### Post by ajgreeny on 2009-11-04
First thing to do is run ```
sudo update-grub
``` in a terminal and see if the grub menu then finds your Vista install.  It should do then you can set the default OS to boot.

See [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) for all the details of grub2.

---

### Post by ranch hand on 2009-11-04
SUM is not really working with grub2 yet, you should leave it alone until the developer gets a chance to upgrade it.

---

### Post by Alexandre Charoy on 2009-11-05
Thanks for your answers.

Yes, I already checked sudo update-grub, and it finds Vista. But if I set Vista as default OS, it will boot, and then I will not be able to access Ubuntu anymore... I think at least.

If I re-install Ubuntu, with formating and everything, will it install GRUB2 again cleanly? Is it a solution for my problem?

---

### Post by ranch hand on 2009-11-05
Well, a good place to start would be to get rid of SUM.  While you are in synaptic doing that you may as well remove grub-common, grub-pc and any other grub you see there.

Then install grub-common and grub-pc.

I think that should clean it up so that it works again.

---

### Post by ajgreeny on 2009-11-05
> **Alexandre Charoy said:**
> Thanks for your answers.

Yes, I already checked sudo update-grub, and it finds Vista. But if I set Vista as default OS, it will boot, and then I will not be able to access Ubuntu anymore... I think at least.

If I re-install Ubuntu, with formating and everything, will it install GRUB2 again cleanly? Is it a solution for my problem?
What exactly do you mean by your first statement?  Why should booting into windows stop you using ubuntu again?  Or do you mean that there is not enough time to see the grub menu and choose?

If that is the case, you just need to edit one of the files in the grub configuration.  All details are here:-
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
but you simply need to open /etc/default/grub as root ```
gksudo /etc/default/grub
```find the line GRUB_TIMEOUT="3" and change the number 3 (or maybe it is something different on your computer) to perhaps 10 to read GRUB_TIMEOUT="10"

That should then give you 10 seconds with the menu showing.  It is also possible that your menu may have been hidden for some reason, so if you see a line like #GRUB_HIDDEN_TIMEOUT=0 the menu should show, but if the #is missing no menu will appear.  You can remove the # at the line start to make the menu appear at boot, or you can just hold down shift when you boot and it should then show.

---

### Post by Alexandre Charoy on 2009-11-06
As I told in my first post, the grub menu doesn't show up at all. In the beginning, after using startupmanager I got the following error message:
[php]vga=796 is depreceated. Use set gfxpayload=640x480x8,640,480 before linux comm and instead.[/php]Then Ubuntu started up automatically, without any grub menu.

I opened the /boot/grub/grub.cfg and /etc/default/grub files, and I found one suspect thing in /etc/default/grub:
[php]GRUB_CMDLINE_LINUX=" vga=796"[/php]I removed it (just the content), and now I don't get any error message anymore, but grub menu doesn't show neither.

It's not a timeout problem (imo):
[php]GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0[/php]
I think if I just re-install Ubuntu from the CD, it would solve my problem? Because if I format and re-install, it will install GRUB2 again cleanly, right?

---

### Post by Alexandre Charoy on 2009-11-06
> **ranch hand said:**
> Well, a good place to start would be to get rid of SUM.  While you are in synaptic doing that you may as well remove grub-common, grub-pc and any other grub you see there.

Then install grub-common and grub-pc.

I think that should clean it up so that it works again.

In Synaptic, the package grub2 is not installed, that isn't normal, is it?
And grub isn't either, only grub-common and grub-pc are installed.

---

### Post by Alexandre Charoy on 2009-11-06
Problem solved: I simply re-installed Ubuntu, this way grub2 was installed cleanly :)


Notes:
- reinstalling grub-common and grub-pc didn't change anything
- installing package grub2 neither...

---

