---
title: "Major problem sudoers with wrong permission!!"
date: 2006-01-20
forum: General Help
---

### Post by antroy on 2006-01-20
Hi all,

I have a serious problem with my Ubuntu installation. Not knowing about the visudoers command, I changed the permissions of the /etc/sudoers file to 0640 so I could edit it.

What I didn't realise was that the file has to have the permissions 0440 to run. So, I can not now perform the sudo command to change the permissions back again! Is this going to mean a reinstall? Or is there another way?

Thanks in advance,

Ant...

---

### Post by JamesNorris on 2006-01-20
I did this, once. I wrote down what I had to do to fix it on a piece of paper somwhere, I'll just look see if I can find it. 

You don't need to re-install, it can be fixed from grub, somehow, IIRC...

---

### Post by JamesNorris on 2006-01-20
Ok, right. This is what worked for me...

Restart the comp and when grub starts, press 'e' and edit the line you use to boot in with, adding "init = /bin/bash" (without the "s) to it.

Then continue and **b**oot up. 

you should be presented with a root bash prompt, then just type this...

mount -o remount,rw/
chmod 0440 /etc/sudoers


I hope this is correct, my syntax might be a little off, the pen has faded a bit... Someone will surely correct me if I'm wrong..

---

### Post by Luke on 2006-01-20
choose recovery mode from grub. this should bring you to a root prompt from which you should be able to edit permissions.

---

### Post by antroy on 2006-01-20
Thanks all! I couldn't use the grub suggestions, as (as I neglected to tell you - sorry!) I'm booting from yaboot on PPC. However, I put in a live CD and changed the permissions that way.

Just goes to show that if you have access to the physical machine, there's not much that can't be messed with on a computer if you have a live cd in your pocket...

Ant...

---

### Post by Luke on 2006-01-20
[QUOTE=antroy]Thanks all! I couldn't use the grub suggestions, as (as I neglected to tell you - sorry!) I'm booting from yaboot on PPC. However, I put in a live CD and changed the permissions that way.

Just goes to show that if you have access to the physical machine, there's not much that can't be messed with on a computer if you have a live cd in your pocket...

Ant...[/QUOTE]
well, that is usually the case but i think it could be prevented if one were to disable booting from cd and then password protect the bios.

glad you got your problem fixed

---

