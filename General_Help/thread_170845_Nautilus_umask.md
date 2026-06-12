---
title: "Nautilus umask"
date: 2006-05-05
forum: General Help
---

### Post by kaptainlange on 2006-05-05
I'm not to sure were to check if a specific bug in gnome has been fixed, but I was wondering if there has been any update on the nautilus umask issue.

It's been referenced on these forums here:
[http://ubuntuforums.org/showthread.php?t=127084&highlight=nautilus+umask]("http://ubuntuforums.org/showthread.php?t=127084&highlight=nautilus+umask")

I tried installing libgnomevfs2-0 (version *.14 I think) to replace the current version which is *.12.  That went horribly when a package dependency problem made apt decide I should uninstall every package on my system.  Quick thinking averted disaster there.  Any one have any idea if the bug has been fixed in .14 and could someone explain how I can install it without apt going insane.

---

### Post by kaptainlange on 2006-05-06
Sorry to bump this, but this is kind of important to me.

Is there any way to get nautilus to respect my xsession's umask.

---

### Post by slashdevnull on 2006-07-26
Another bump.

I have 2 customers being affected by this issue currently, and am hesitant to roll out more Ubuntu systems for customers unless I know that something as basic as setting default unix file permissions can be done.

This is a bad situation, since I actually have other customers asking to migrate to Ubuntu from Windows, and I'm sure that as Microsoft puts the financial squeeze on their installed userbase with Vista's release, we'll see even more of this sentiment.

Thanks for all of the hard work, Ubuntu & Gnome devs.  Looking forward to a patch.

---

### Post by slashdevnull on 2006-08-03
I have just put out a bounty to get this fixed:
[https://launchpad.net/bounties/nautilus-ignores-umask](https://launchpad.net/bounties/nautilus-ignores-umask)

The initial USD value I'm able to apply to this is $250. I'm looking for additional sponsors as well, to make this attractive to would-be bugfixers.

Any takers?

---

