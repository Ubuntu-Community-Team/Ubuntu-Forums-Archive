---
title: "Lost all group associations for all users"
date: 2009-08-20
forum: General Help
---

### Post by paul_da_programmer on 2009-08-20
Hello,
I've been running Ubuntu very satisfactorily until ... I installed Oracle XE 10G.
After rebooting I find that I cannot run any privileged commands:
1. I tried launching Synaptic and after supplying my password it reports "Failed to run /usr/sbin/synaptic" as user root
2. Going to the terminal I cannot run sudo - again it prompts me for my password, but it reports "not in the sudoers file"
3. typing groups give me only:
paul dba
(paul is my id)
I suspected the problem was the Oracle installation - it gave me the group "dba" but **removed** all of my other groups. I KNOW there were many system assigned groups, plus I had VirtualBox working great and added myself to "vboxusers" group.

What I've done so far:
Since I suspected that the groups were messed up during the Oracle installation I looked at the /etc/group file. The last line was this:
```
dba:x:1002:paul,valerie
```1. I booted into recovery mode and as root removed paul,valerie from the /etc/group file
After rebooting, now I am only in group "paul"

QUESTION: Did the Oracle installation really screw up that bad - instead of **adding** me to the dba group did it disassociate me from ALL my other groups?

QUESTION: How can I recover all of my original groups? Can someone please post what groups our ids should belong to? Its a relatively new install.

Please help!
Thanks! 
--Paul

---

### Post by michy99 on 2009-08-20
These are the groups I belong to other than my username group:```
adm dialout cdrom plugdev lpadmin admin sambashare
```I make it a regular practice to make a backup of these four files for such emergencies:```
/etc/passwd
/etc/shadow
/etc/group
/etc/gshadow
```

---

### Post by paul_da_programmer on 2009-08-20
Me again :)
Ok ... I actually got my system working again - luckily I  noticed when I logged into root (via the single user mode) that there was a file in /etc named "group-" (trailing "-")

Luckily - it had all of the groups set for valerie (the other user id) ... so I copied group- to group:
1. cp group- group
2. edited it and globally replace all "valerie" with "paul,valerie" ( I needed to make one manual edit to handle the line starting with "valerie"
3. everything now seemed to work properly except VirtualBox. Luckily it gave me a great error message instructing me to recompile the VB kernel and gave the root command to run. I did that and now Vb works as well. It appears all is well again ...

I still completely dumbfounded that the Oracle XE installation (made for ubuntu by the way) would trash my system so completely. Hopefully this saves someone else the pain.

If I've done something that seems awry - I'd appreciate hearing from the experts on the board ... but for now I'm back in business.

---

