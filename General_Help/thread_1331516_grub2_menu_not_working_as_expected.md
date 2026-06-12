---
title: "grub2 menu not working as expected"
date: 2009-11-19
forum: General Help
---

### Post by EnlistedSquire on 2009-11-19
Hi,

When I had legacy Grub installed I had it set so the boot menu was hidden unless I pressed Esc at boot. This then bought up the boot menu and it worked fine.

When upgrading to Ubuntu 9.10 I installed Grub2 and I'm trying to achieve the same thing.

This is the top part of my /etc/default/grub:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="splash quiet"
```

which, from my understanding, should work in the same way.

The problem is, with this configuration, no amount of pressing the shift or Esc key at boot brings up the menu.

I've tried just about every other combination of options as well and I can only get two different outcomes - either the menu shows at every boot or the menu never shows at all. I am running update-grub after every change.

Am I doing something obviously wrong?

Thanks.

---

### Post by Giblet5 on 2009-11-19
Are you running grub-install to actually write the changes to disk?

```
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

---

### Post by EnlistedSquire on 2009-11-19
> **Giblet5 said:**
> Are you running grub-install to actually write the changes to disk?

```
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

Grub2 is already installed. I'm not sure what that command will do.

---

### Post by EnlistedSquire on 2009-11-25
> **EnlistedSquire said:**
> Grub2 is already installed. I'm not sure what that command will do.

Well I ran that command anyway. I still have the same problem.

---

### Post by drs305 on 2009-11-25
It may only be semantics, but you have to *hold* the shift key down during the initial boot. Pressing it won't work unless you happen to get it at just the right time. 

Try making this change as well to /etc/default/grub:
> GRUB_TIMEOUT=0
*to*
GRUB_TIMEOUT=10
or some other positive value so the menu is displayed for a while.
That setting should still keep the menu hidden by default, but display it for 10 seconds once it does become visible. Otherwise when called to display it would display for 0 seconds and then boot.

Don't forget to run "sudo update-grub" to make the change to the menu.

---

### Post by EnlistedSquire on 2009-11-25
> **drs305 said:**
> It may only be semantics, but you have to *hold* the shift key down during the initial boot. Pressing it won't work unless you happen to get it at just the right time. 

Try making this change as well to /etc/default/grub:

or some other positive value so the menu is displayed for a while.
That setting should still keep the menu hidden by default, but display it for 10 seconds once it does become visible.

Don't forget to run "sudo update-grub" to make the change to the menu.

I understand the hold shift key thing. I've tried what you suggest already. I can't remember which outcome it produces but as per my OP  the menu will either show *all* the time, regardless of any key presses, or not at all.

---

### Post by Gonzalo_VC on 2009-11-25
> **EnlistedSquire said:**
> Hi,

When I had legacy Grub installed I had it set so the boot menu was hidden unless I pressed Esc at boot. This then bought up the boot menu and it worked fine.

When upgrading to Ubuntu 9.10 I installed Grub2 and I'm trying to achieve the same thing.

This is the top part of my /etc/default/grub...


[COLOR="Blue"]Guys, a question still in this subject: in this GRUB 2.0, the old /boot/grub/menu.lst is now at  /etc/default/grub ?? How can we edit the boot list, change the booting preference, defaults, etc.? I used to do it with gedit easily before.
Thanks! [/COLOR]

---

### Post by drs305 on 2009-11-25
> **EnlistedSquire said:**
> I understand the hold shift key thing. I've tried what you suggest already. I can't remember which outcome it produces but as per my OP  the menu will either show *all* the time, regardless of any key presses, or not at all.

I've had problems at times with the display. If you don't have additional distributions on other partitions or don't care if they are updated, adding this line to /etc/default/grub allowed the menu to be hidden for me:
> 
GRUB_DISABLE_OS_PROBER=true


---

### Post by EnlistedSquire on 2009-11-25
> **drs305 said:**
> I've had problems at times with the display. If you don't have additional distributions on other partitions or don't care if they are updated, adding this line to /etc/default/grub allowed the menu to be hidden for me:

Thanks but I have a Windows XP installation that I very occasionally boot into.

---

### Post by caue.rego on 2009-11-30
double post. how can i delete this?

---

### Post by caue.rego on 2009-11-30
> **drs305 said:**
> I've had problems at times with the display. If you don't have additional distributions on other partitions or don't care if they are updated, adding this line to /etc/default/grub allowed the menu to be hidden for me: ```
GRUB_DISABLE_OS_PROBER=true
```

This seem to work for me as well.

But thing is I do care about the OS Prober, and I wish to leave it enabled. Maybe this is a bug and all we can do is wait for a fix (other than engaging it and fixing it, that is). It seems like it is, after all, a known bug for long time: [http://ubuntuforums.org/showthread.php?t=1291166](http://ubuntuforums.org/showthread.php?t=1291166)

As for **EnlistedSquire**, once grub probed and configured other OS, you don't need it to probe again. You can disable it and still boot into windows xp.

---

### Post by EnlistedSquire on 2009-12-01
> **caue.rego said:**
> This seem to work for me as well.

But thing is I do care about the OS Prober, and I wish to leave it enabled. Maybe this is a bug and all we can do is wait for a fix (other than engaging it and fixing it, that is). It seems like it is, after all, a known bug for long time: [http://ubuntuforums.org/showthread.php?t=1291166](http://ubuntuforums.org/showthread.php?t=1291166)

As for **EnlistedSquire**, once grub probed and configured other OS, you don't need it to probe again. You can disable it and still boot into windows xp.

If I disable the OS Prober I can bring up the menu by holding down shift - yay!

But if I disable it, running ```
sudo update-grub
``` doesn't discover my Windows partition so it doesn't appear in the grub menu.

If I disable it in /etc/default/grub but don't run ```
sudo update-grub
``` it doesn't fix my problem :(.

---

### Post by oldfred on 2009-12-01
Enable the prober. update. Copy the windows entry to 40_custom. disable prober & run update-grub again. You will keep your windows entry and will only need to run the prober if you install a new operating system.

---

### Post by caue.rego on 2009-12-01
That's weird **EnlistedSquire**. In my case I disable it, run update-grub and it detects both my win 7 and mac os properly. Plus holding shift works fine. I figured it would just not be able to detect anything newer automatically, like if I remove or add kernels (which don't need to run update-grub for it to identify and add to the list).

---

### Post by NFblaze on 2009-12-01
I was just about to ask this same question along with an additional one.

With Grub2, the number of menu items changes usually when you update and get more kernels. So, how is one suppose to create let's say have a consistent default boot into Windows XP located at menuentry number 5, if let's say down the line I get more kernels added and it get's pushed down to menu entry number 7? 

Anybody know a way around this? Only, way I can think of is editing /boot/grub/grub.cfg manually.

---

### Post by caue.rego on 2009-12-01
That's easy. Instead of using numbers, use the entry **name**. Pay attention on that option in the help, wiki or here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by NFblaze on 2009-12-01
Thanks, I totally glossed over that. I've edited it and will give it a spin.

---

### Post by EnlistedSquire on 2009-12-01
> **oldfred said:**
> Enable the prober. update. Copy the windows entry to 40_custom. disable prober & run update-grub again. You will keep your windows entry and will only need to run the prober if you install a new operating system.

That fixed it, thanks.

---

### Post by Cavsfan on 2009-12-01
> **Gonzalo_VC said:**
> [COLOR=Blue]Guys, a question still in this subject: in this GRUB 2.0, the old /boot/grub/menu.lst is now at  /etc/default/grub ?? How can we edit the boot list, change the booting preference, defaults, etc.? I used to do it with gedit easily before.
Thanks! [/COLOR]

Gonzalo_VC, I had the same question, I believe the answer is in the link provided by caue.rego:
 
[quote=caue.rego]That's easy. Instead of using numbers, use the entry name. Pay attention on that option in the help, wiki or here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)[/quote]

Guess we'll have to read it!
Thanks!

---

### Post by garvinrick4 on 2009-12-01
Booting preferences can be done via GUI in "startupmanager" if not installed.

sudo apt-get install startupmanager



Easiest way I know and convienent for dual or tri booters.

---

### Post by RodGer GR on 2009-12-06
I managed to have the menu hidden without disabling the prober by adding the 
```
GRUB_DISABLE_OS_PROBER=true
```line changed to
```
GRUB_DISABLE_OS_PROBER=false
```

---

### Post by caue.rego on 2009-12-07
> **RodGer GR said:**
> I managed to have the menu hidden without disabling the prober by adding the 
```
GRUB_DISABLE_OS_PROBER=true
```line changed to
```
GRUB_DISABLE_OS_PROBER=false
```

That would be great if it worked out for me! But it did not. :(

What else can you tell us that you've made to make this workaround do the job?

---

### Post by EnlistedSquire on 2009-12-07
It doesn't work for me either.

---

### Post by Gonzalo_VC on 2010-01-12
[COLOR="Navy"]I had to reinstall the "other" SO and I lost the boot sector. Now, wit GRUB 2 (Ubuntu 9.10), it is not easy to rescue the boot menu as in [http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)
[http://www.thpc.info/how/reinstall_grub.html](http://www.thpc.info/how/reinstall_grub.html) 
Any ideas on how to rescue the boot menu?
Thanks.[/COLOR]

---

### Post by drs305 on 2010-01-12
Gonzalo_VC

You may have to explain what you mean by 'rescue' the Grub 2 boot menu. If you are asking how to reinstall Grub 2, look at this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

If this isn't what you are looking for please let us know what you want to do (and what you can't).

---

### Post by Gonzalo_VC on 2010-01-13
> **drs305 said:**
> Gonzalo_VC

You may have to explain what you mean by 'rescue' the Grub 2 boot menu. If you are asking how to reinstall Grub 2, look at this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

If this isn't what you are looking for please let us know what you want to do (and what you can't).

[COLOR="Navy"]I'll study and try that one, so. Thank you.
 
I meant that with the other method (my previous link) you could just use the information on your "\boot\grub\" folder to copy the necessary files back into the first disk MBR to get back the boot menu you had before erasing that MBR (my case, since I reinstalled the 1st disk SO, but still got my Ubuntu in a secondary disk).
Cheers!
[/COLOR]

---

### Post by Leppie on 2010-01-13
reinstalling grub2 to the mbr isn't that hard using booting off the livecd. a lot of people use sda5 as their linux partition when dual booting, obviously if this is different for you you'll have to change that to the correct partition:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

