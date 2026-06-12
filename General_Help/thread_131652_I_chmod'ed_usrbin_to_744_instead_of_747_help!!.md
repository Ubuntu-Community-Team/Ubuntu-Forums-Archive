---
title: "I chmod'ed /usr/bin to 744 instead of 747 help!!"
date: 2006-02-16
forum: General Help
---

### Post by loweb1 on 2006-02-16
Please Help!

I accidentaly changed the permissions on /usr/bin from 747 to 744 and now I can't change them back!

I can't log in graphically.

I can't sudo anything.

I'm lost, please don't tell me I'm going to have to reformat or something.

Any help would be appreciated. 

Thank you.

---

### Post by mr.p on 2006-02-16
Your best bet would be to boot up into a Linux live CD and then mount the root filesystem and chmod that directory correctly. :confused:

---

### Post by o_fortuna on 2006-02-16
[QUOTE=loweb1]Please Help!

I accidentaly changed the permissions on /usr/bin from 747 to 744 and now I can't change them back!

I can't log in graphically.

I can't sudo anything.

I'm lost, please don't tell me I'm going to have to reformat or something.

Any help would be appreciated. 

Thank you.[/QUOTE]
From the GRUB boot-up menu (press escape when it says "Loading GRUB stage 1.5, or something like that), select recovery mode. Then, do the chmod 744 /usr/bin command at the command prompt once you log in.

Just as a general rule, though -- don't chmod stuff unless you're copying and pasting commands. It's just too easy to screw stuff up. If the above doesn't work, I'm afraid a reformat is your only choice -- unless someone has another option?

---

### Post by loweb1 on 2006-02-16
Thank you! Just knowing there's something I can try takes a huge weight off my chest. Unfortunately I don't think my installation cd is a live one, and I don't have a way of getting a live cd for quite a while. Is there anything I can try in the meantime?

---

### Post by loweb1 on 2006-02-16
Ok I'll try the boot-up option too. Thanks!

I was trying to fix a link in there to open up the firefox browser for webHTTracker is how all this got started. I'm very unexperienced with linux obviously, but I still love it and even though this has been harrowing I want to learn more. So thanks for your help.

---

### Post by nanotube on 2006-02-17
you should still be able to run your commands, you just have to specify the full path. so, you should run
```
/usr/bin/sudo chmod 755 /usr/bin
```
and that should get you back to normal.

---

### Post by loweb1 on 2006-02-19
Thanks everyone, I was able to use the recovery mode to set the permissions back to 747.

Nanotube: You say I should change it to 755, is there a specific reason? I think it was originally 747.

Thanks again.

---

### Post by nanotube on 2006-02-19
by default /usr/bin is set to 755 (rwx root, r-x group, and r-x everyone). you really should not set it to 747 (which is rwx root, r-- group, and rwx everyone).

i am very sure that it was not originally 747 - it is 755 in default install on every linux/bsd system i have ever seen. :)

---

### Post by lha on 2006-02-19
[QUOTE=loweb1]Thanks everyone, I was able to use the recovery mode to set the permissions back to 747.

Nanotube: You say I should change it to 755, is there a specific reason? I think it was originally 747.

Thanks again.[/QUOTE]
It was originally 755. If you make it 747, every has write access to that directory and that's not what you want.

---

