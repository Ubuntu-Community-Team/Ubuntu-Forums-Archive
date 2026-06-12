---
title: "Debian boots only on second attempt"
date: 2009-08-26
forum: General Help
---

### Post by JohnLM_the_Ghost on 2009-08-26
I have a Debian Lenny Server which has peculiar behaviour to fail on first boot and boot fine on second attempt.
This is quite a problem because it is a primarily used as headless server, and I notice problem usually when services are down.

It prints no error message whatsoever. Simply freezes with no magic keys working either. (UPDATE: On rare occasions magic keys remain responsive.)

The problem seems fairly generic (as Ubuntu is also debian based and there isn't much difference from server and desktop boot process) so I posted it in General Help.

Machine is a Celeron 1.7Ghz.
512 MB RAM
Voodoo3 Video (and disabled onboard one)
VIA motherboard.

I'm completely clueless! Any help will be most appreciated.
I didn't want to flood thread with potentially useless info, so ask for any info you need.

NEW: Server fails to boot several times if restarted rapidly - errr, right after each freeze.
NEW: Eliminated Hard Disk as origin. Phew, at least my files are safe.
Read posts below...

---

### Post by MartinEve on 2009-08-26
Hi,

I'm not sure I'm fully qualified to diagnose the problems you are having, but wanted to ask if you've tried upgrading your kernel to the latest stable?

Martin

---

### Post by JohnLM_the_Ghost on 2009-08-26
EDIT: Hmm... I've done some more testing and there seems there's no correlation with whatever is printed on console (dmesg). It stops and freezes somewhere at random. However time of freeze is fairly constant - around 2 seconds within Debian boot process (i.e. after POST and GRUB).
Symptoms also are constant - freezing up with no messages and non-working Magic keys.

Among other things HDD has been acting funny before... think this could be related?

Well, defining funny is clicking sound and some "Drive seek retry messages".
I switched IDE cables and it was resolved, but it still makes me consider HDD.

> **MartinEve said:**
> Hi,

I'm not sure I'm fully qualified to diagnose the problems you are having, but wanted to ask if you've tried upgrading your kernel to the latest stable?

Martin

Thanks for reply, but
it is the latest stable one. Unless there's some bug I'm not aware of...

btw it is 2.6.26 (2-17lenny2) - latest from Lenny's (stable) DEB repository.

---

### Post by JohnLM_the_Ghost on 2009-08-31
Well my server no longer boots up strictly on second attempt.
Now that attached monitor I can instantly see when it freezes, so if I (hard) restart it right away it tends to fail as well with same symptoms.

Well I never thought of this before, and never heard either in my entire experience with computers, but... could it possibly be too cold to boot?

Well by that I mean mostly hard drive. It is not really cold (slightly below room temperature), but it's usual working temperature is rather high. (Samsung SP0812N IDE hard-disk)
I think rest of components don't exactly care about the low temperature.

Well I thought of this because HDD is rather cool to touch after downtime, and I would usually notice Server's boot failure after at least half an hour, unlike now, when I reboot it rapidly enough for it to remain cool.

Sounds a bit stupid, but it is currently best lead I have.

p.s. Slightly ironic is fact that my other PC suffers from overheating.

---

### Post by Kopachris on 2009-08-31
What about your other components?  How to they feel to touch?  Also, have you made entirely sure that EVERYTHING is plugged in correctly?  I've had similar problems with overheating and having things not plugged in right.

I'd also like a little more information.  First, does your system start up GNOME or KDE, or is it just command-line?  Second, where does it stop?  Earlier, you said that it stopped at a random place, but you later seemed to contradict that statement.  If it *does* stop at an arbitrary spot in the bootup process, give me a few examples of stopping spots.  There still might be an underlying pattern.

Other than hardware problems, I can only think of a problem with vmlinuz or initrd, or init itself.

---

### Post by JohnLM_the_Ghost on 2009-08-31
There's nothing else aside of HDD with moving parts (short of coolers), and it isn't cold enough here for either frost or simple water condensate to form.
Well I mean all devices are already at ambient temperature  when I try booting it up. Ambient = few degrees below whatever room temperature is in late summer.

The server is CLI-only (text mode, not framebuffer). Apart from usual boot procedure on startup there's currently only SSH and MySQL services and my firewall script. But neither of three are reached when it freezes.
It freezes after few seconds within Linux boot process at random position.
Also today noticed that HDD usually loudly clicks once exactly when server freezes, though it keeps spinning.

Usually at this point I would notice nothing and reboot it later when I notice (or someone else notices) that SSH is not up. And after "forcibly rebooting" (holding power-button for 5s and powering it up again) it worked. (That's why the thread title)

Now that I attached monitor I carefully watch the bootup. Apart from everything written above, it also tends to freeze when it is "forcibly rebooted" right away. But currently seems to boot up ok after few minutes it had idled (with power on).

Also I haven't had problems with it on runtime. It works stable for days, also with occational overnight data-transfer.

As with Linux itself... I've only done security updates for kernel and packages. Kernel version was always the same - only revisions changed. But didn't notice anything bad about those.

---

### Post by Kopachris on 2009-09-01
> **JohnLM_the_Ghost said:**
> There's nothing else aside of HDD with moving parts (short of coolers), and it isn't cold enough here for either frost or simple water condensate to form.
Well I mean all devices are already at ambient temperature  when I try booting it up. Ambient = few degrees below whatever room temperature is in late summer.

The server is CLI-only (text mode, not framebuffer). Apart from usual boot procedure on startup there's currently only SSH and MySQL services and my firewall script. But neither of three are reached when it freezes.
It freezes after few seconds within Linux boot process at random position.
Also today noticed that HDD usually loudly clicks once exactly when server freezes, though it keeps spinning.

Usually at this point I would notice nothing and reboot it later when I notice (or someone else notices) that SSH is not up. And after "forcibly rebooting" (holding power-button for 5s and powering it up again) it worked. (That's why the thread title)

Now that I attached monitor I carefully watch the bootup. Apart from everything written above, it also tends to freeze when it is "forcibly rebooted" right away. But currently seems to boot up ok after few minutes it had idled (with power on).

Also I haven't had problems with it on runtime. It works stable for days, also with occational overnight data-transfer.

As with Linux itself... I've only done security updates for kernel and packages. Kernel version was always the same - only revisions changed. But didn't notice anything bad about those.
Okay, try booting to a LiveCD and tell me what happens.  If the LiveCD won't boot, it's a hardware problem with something other than the HD.  If it does boot fine, then it's either a HD problem or a software problem.

---

### Post by JohnLM_the_Ghost on 2009-09-28
> **Kopachris said:**
> Okay, try booting to a LiveCD and tell me what happens.  If the LiveCD won't boot, it's a hardware problem with something other than the HD.  If it does boot fine, then it's either a HD problem or a software problem.

So I tried (my old trusty Dapper Drake) LiveCD, and it seemed to boot fine.
However I find test to be inconclusive because I was not able to get "HDD-fail -> LiveCD-success -> HDD-fail again" sequence. Debain always booted ok after LiveCD, but LiveCD obviously took it's time for boot.

I also got "new" HDD. I did *dd* the root (system) partition to the other HDD, so I now boot up from that one, though both HDDs are attached because there was not enough space to transfer user data.
In short my partition table now is:
"New" HDD:
/dev/hda1 (ext3) as root partition (/)
/dev/hda2 (swap) as swap
/dev/hda3 (ext3) - currently unused (not in fstab)

Previous "potentially problematic" HDD:
/dev/hdc1 (???) as Windnows/DOS (/mnt/windisk)
/dev/hdc2 (ext2) as rescue disk (not in fstab)
/dev/hdc5 (ext3) as old root (not in fstab)
/dev/hdc6 (swap) as currently unused swap space
/dev/hdc7 (ext3) as user files (/home)

A CDROM is attached as /dev/hdd (sec. slave)
And memory card reader is on USB (/dev/sd*)

After only sigle test though it seems that problem persists.
I'm starting to think that this is no HDD problem after all.

As a little side test, I tried to attach server's old HDD (/dev/hdc) to a USB-to-IDE serializer device (the thing from USB Hard Drive). Hooked that up to my main rig. Worked like a charm! One more point against HDD problem.

Quite Hesitant to reinstall Debian, but I guess I will need to do so and see what happens.

Also now that the server has failed on boot for quite a number of times, there seems to be some kind of pattern.
It's two best favourite fail point are after ```
ACPI: Processor [CPU1] (supports 16 throttling states)
```
or after ```
Please wait while /dev is being populated...
```
but it still fails at random position as well.

Your thoughts?

btw Is it safe to boot with disk containing /home to be removed? I might try removing old HDD at all before anything else to be really sure.

---

### Post by Kopachris on 2009-09-28
Have you tried booting it w/o acpi and stuff?  When you boot up, enter the GRUB menu (usually hit "esc" before the countdown at the bottom of the screen reaches 0).  When you're in the menu, select the boot option that you want and hit the 'e' key instead of enter.  When it comes up with the boot command, add "acpi=off noapic nolapic" and hit enter.  If it works, try it again a few times to make sure and let me know.  If not, well, just let me know.

---

### Post by JohnLM_the_Ghost on 2009-11-01
OK, still not resolved...

Putting "acpi=off noapic nolapic" didn't change anything.
However disabling ACPI and APM in BIOS broke the pattern of where it crashed, but it still crashed.

Also tried removing /dev/hdc altogether and reinstalling latest Debian on /dev/hda (my secondary HDD). Nothing changed.

Also now that winter is coming and I've begun to stoke furnace, temperature is fluctuating and it somewhat affects the damn server rig.
Haven't really spotted any patterns, but is sometimes freezes, while remaining responsive (and I can do REISUB sequence).
Having eliminated Hard disk as origin. There's still something that might be affected by ambient temperature. Apparently only thing that remains is the motherboard.

Among other quick ideas it might be PSU problem, but then again 420W should be more than adequate to power the rig, and it would crash under heavy loads instead on boot. Seems unlikely, but I might look into it if I eliminate everything else. (Or chance presents me with a new shiny PSU) :)

---

### Post by P4man on 2009-11-01
You could try this:
[http://ubuntuforums.org/showpost.php?p=6440020&postcount=7](http://ubuntuforums.org/showpost.php?p=6440020&postcount=7)

---

### Post by JohnLM_the_Ghost on 2009-11-01
> **P4man said:**
> You could try this:
[http://ubuntuforums.org/showpost.php?p=6440020&postcount=7](http://ubuntuforums.org/showpost.php?p=6440020&postcount=7)

Thanks, but how this is relevant?
I got no external HDDs and internal ones mount correctly.

I reckon if there were "race" condition, it would fail at random, but in my case it fails consistently on first boot.

---

### Post by P4man on 2009-11-01
Just a guess. If your harddrive spins up slowly.

---

### Post by JohnLM_the_Ghost on 2010-01-15
OK, My server appears to have met pearly gates after all.

The boots escalated to show Kernel Panics, and now its just blank screen and very annoying beep. All that is left to locate the failing part(s) and try to salvage what is left.

Thread closed! Thanks for help!

---

