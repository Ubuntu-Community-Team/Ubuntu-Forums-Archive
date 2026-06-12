---
title: "[Booting] Errors were found while checking the disk drive for /"
date: 2010-09-26
forum: General Help
---

### Post by shokkapic on 2010-09-26
Good evening,

I've experienced some "problems" while booting 10.04 sometimes, from my laptop.

See the following pictures, please:
[[IMG]http://img267.imageshack.us/img267/2324/img20100926103608.th.jpg[/IMG]]("http://img267.imageshack.us/i/img20100926103608.jpg/")_[[IMG]http://img830.imageshack.us/img830/3528/img20100926103629.th.jpg[/IMG]]("http://img830.imageshack.us/i/img20100926103629.jpg/")_


If I press F on the first screen, the second one appears and the system reboots after 2 seconds and it starts normally.

I think this doesn't have an actual impact on the performance, because I wasn't able to spot a single problem while on Ubuntu.

The weird thing is that this only happens sometimes, and I can't find an explanation to this "problem".


I've a dual-boot laptop, with Windows Seven and Ubuntu (on different HDDs). Grub is configured correctly, afaik.



Any information regarding this?

Thanks.

---

### Post by sikander3786 on 2010-09-26
It often happens if you power down your computer without properly shutting it down. Have you got that habbit?

Check the disks for error when you boot successfully or if you can't you can also use a live cd and gparted to check disks for errors.

---

### Post by leomrlima on 2010-12-14
Hello. 

I had this error on a 10.04.1 Server Ubuntu after a power outage with several spikes (that even damage another HD). I was wandering if there's a way to automatically "press" F without me having to press F manually, because it's a server and on a remote location.

I've search the interwebs but failed to find a answer to this question (I did found this thread...)

Could you please advice?

Thank you for your response,
Leo.

(I hope I'm not necro'ing this or even hijacking, but otherwise I'd start a thread with the same name...)

---

### Post by CharlesA on 2010-12-14
As far as I know, there is no way to press "f" automagically.

---

### Post by leomrlima on 2010-12-14
Thanks for your response!

I saw there's a configuration in /etc/fstab to make it mount readonly when in error, something like "errors=remount-ro". Do you know if this would prevent the F screen showing up? Because then I'd schedule an auto-fix in next boot when I detect a readonly situation... Is this feasible?

Thanks again for your support,
Leo.

---

### Post by CharlesA on 2010-12-14
I know my fstab is set to do that by default, but I don't know how it works.

Note, you'd normally force a fsck by doing something like this:

```
sudo touch /forcefsck
```

Which isn't possible if the root file system is mounted as read only.

---

### Post by leomrlima on 2010-12-20
Hello!

Thanks for your response.

I find it "sad" that we can~t set fsck to auto-fix if it finds an error. Specially because I use the server version, and I should never have to attach a keyboard/monitor to it if I have a power failure... 

If I set the option to ignore errors, that command (touch /forcefsck) would schedule a scan to next boot? Or immediately?

Thanks again for your time,
Leo.

---

### Post by CharlesA on 2010-12-20
It would run on next boot.

The whole reason for not running fsck automatically can be found in this [thread]("http://ubuntuforums.org/showthread.php?t=1320478").

---

### Post by leomrlima on 2010-12-21
Thank you very much for the post link.

I see that it's "stupid", but all the times that I came across an interactive fsck, I pressed F and it "oooh" fixed all the errors and carried on.

I'll try the ignore errors and force on next boot to see what happens.

Thank you very much.
Leo.

---

### Post by leomrlima on 2011-01-24
Searching the internet, again, I found [this thread]("http://ubuntuforums.org/showthread.php?t=118260") that mentioned a way to change fsck to run with -y instead of -a... I double checked with the [man pages]("http://manpages.ubuntu.com/manpages/lucid/man5/rcS.5.html") and I think this should work.

So I set this option and now I should get things more automagically fixed, right?

Regards,
Leo.

---

### Post by CharlesA on 2011-01-24
Should work, but do so at your own risk.

---

