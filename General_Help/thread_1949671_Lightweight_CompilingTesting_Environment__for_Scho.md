---
title: "Lightweight Compiling/Testing Environment  for School - Help?"
date: 2012-03-30
forum: General Help
---

### Post by MinionTech on 2012-03-30
Hi Ubuntu Forums,


At my university the number two reason for failed programming assignments is compilation errors, usually blamed on home and school machines having different compilers (#1: assignment not submitted).  I want to pitch a VM (VirtualBox?) for students to compile assignments at home and be sure they'll compile at school.  Since a lot of non-tech major students take first year programming classes this could help expose them to Linux!


Idealized checklist:

- small download size (<2 GB, but less is better)
- lightweight/small footprint
- basic desktop environment
- remotely version-match the school's apps (varies from distro)
- LTS vs. rolling (i.e. Ubuntu LTS vs. Arch or Mint Debian)
- easy to use and update
- allow end-users admin rights
- possibly sync files with Dropbox or similar service (good/bad?)


So far I have an A paper/presentation, a demo running Lubuntu and an acronym.  I'll probably post this idea around a bit as well.  With a little luck and a lot of help it could even end up an independent study project.  Your suggestions would be greatly appreciated!  Thanks!


WHAT I WANT FROM YOU:
-> How do we keep apps version-matched with the school?  I’ll be checking their systems regularly.
-> Any other tips, tricks, ideas or inspiration!


Best regards,

Derek

---

### Post by Paddy Landau on 2012-03-31
I'm not entirely sure what you are asking. If you want a very lightweight distro, you can try [Bodhi]("http://www.bodhilinux.com/"), which is very light indeed. There are even lighter distros, but Bodhi has a nice balance between light and functional.

For something not quite as light, but still very light, try [Lubuntu]("https://wiki.ubuntu.com/Lubuntu").

Regarding keeping the systems in sync, the easiest is to simply keep up-to-date with the updates.

---

### Post by MinionTech on 2012-04-04
My current demo is on Lubuntu, but Bodhi looks promising.  That it's even lighter than Lubuntu is particularly interesting.  Thanks for the suggestions!

What do you recommend for forcing remote machines to stay up to date?  Would adding something like "sudo apt-get update ; sudo apt-get upgrade -y" to their startup work well or cause chaos?  Is there a practical way to manually push programs or updates to remote machines if the school demands it?

---

### Post by Paddy Landau on 2012-04-05
If you wish to automatically install *all* updates, you can do this. Turn off automatic security updates. In root's anacron, run the following command daily:
```
apt-get update && apt-get --yes  dist-upgrade
```However, this is not generally recommended, because  you are unlikely to catch errors; and (rarely) the [FONT=Lucida Console]--yes[/FONT] option is not the best one.

The best solution is to turn on automatic security updates and train the user to run Update Manager weekly.

You turn on automatic security updates as follows. Update Manager > Settings > Updates > Automatic Updates > Check for updates: Daily, and Install security updates without notification.

**EDIT:** [Puppy Linux]("http://puppylinux.org/") is even lighter than Bodhi, but it is a terribly basic system.

---

### Post by MinionTech on 2012-04-15
After getting feedback from you and some other great Linux people, it looks like the simplest solution is the best.  I'll be pitching an image that can be replaced each semester, changing as necessary.  The earlier plans to push updates and software is just a bit too ambitious and naive.  Maybe later in my degree and/or career that'll change, but for now simple is perfect.  :D

With exams done for the semester I'm installing/trying Bodhi right now.  Thanks for your help!

---

### Post by Paddy Landau on 2012-04-16
I think you've made a good decision.

If you feel this has resolved your issue, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

