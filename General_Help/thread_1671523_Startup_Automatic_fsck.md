---
title: "Startup Automatic fsck"
date: 2011-01-20
forum: General Help
---

### Post by spade on 2011-01-20
The startup automatic fsck is a nice feature, but a partition check duration may be 15 minutes for my PC.
So I would like to know if there is a way:

1/ to have more verbosity to know what partition is currently checked and what is the status of the current check (%)

2/ to set a background check that allow the startup process to carry on (other checks, logon, ...) for particular partitions.
The automatic mount could occur when the user is logged on and the check is achieved. A popup message would be great.

My ubunu is up-to-date Maverick.
Thanks.

---

### Post by lithopsian on 2011-01-20
The default boot is "quiet".  You can change your boot options so it isn't quiet and will display the information you want.  It will also show some other messages.  Try it and see what you think.

You can code anything you like :)  The file system check will be skipped if you press ESC, also it won't start if you're on battery power.  It will then try to run again at the next boot.  fsck is not run on mounted volumes because it can cause corruptions so running it after you login is not generally a good idea unless you really know what you're playing at.

---

### Post by spade on 2011-01-20
> **lithopsian said:**
> The default boot is "quiet".  You can change your boot options so it isn't quiet and will display the information you want.  It will also show some other messages.  Try it and see what you think.

OK I tried to remove the "quiet" option and all I get is:
- a first very verbose but unuseful step
- a second non-verbose check step
What I exspect is exactely the way around, rather following the policy "don't-say-anything-except-if-something-is-wrong". An automatic fsck is an exceptional event, so it would be great to have basic informations about what is running: partition id and % of running

> **lithopsian said:**
> 
fsck is not run on mounted volumes because it can cause corruptions so running it after you login is not generally a good idea unless you really know what you're playing at.
I know a file system should not be mounted when checked. But generally only the "home" partition is absolutely necessary to boot and login. Other partitions mounting could be postponed after their eventual backgrounded check, without blocking the boot and login process. Is there any setting to get this behaviour ? (fstab ?)

---

### Post by lithopsian on 2011-01-20
That's Maverick for you :(  They kind of dumbed down a lot of stuff.  Older versions tell you about the fsck if you remove the quiet option.  I'm slightly surprised that 10.10 doesn't also.  You'd have to look into the /etc/init.d/check script to see why.

"home" meaning "root" :)  /home is not required for the early stages of booting, but it certainly is at about the time your splash screen disappears and you are asked to log in, or you switch over to the desktop.  Checking file systems before then is still going to delay you, and checking after that is not safe.

---

### Post by spade on 2011-01-20
It is the first time I read the rule that it is not safe to check a partition when you are logged in, I thought it was only necessary not to mount it.
I can easily accept to be delayed with my /home partition check because this partition is necessary to the user session, but not for other ones, particularly for a backup one which is 1.3 To and that takes 15 minutes to be checked. I don't need it to be mounted as soon as I log in. So I wondered if it was possible to:
- background the check process
- postpone the mounting after the check achievement.
If you need me to write it for a third time, I would be delighted to do it as well as me if you could give me an information about this subject.

---

### Post by psusi on 2011-01-20
I get a percent progress indicator on maverick.  You can't do it in the background, but you can disable the check entirely since it isn't really necessary:

sudo tune2fs -i 0 -c 0 /dev/sda1

---

