---
title: "Edit Grub Menu"
date: 2010-05-23
forum: General Help
---

### Post by l3ecl on 2010-05-23
FIXED

Kindly help editing the grub menu. Here is a close[ picture of my grub menu]("http://img156.imageshack.us/img156/5383/img6914x.jpg") (which I stole from someone.) I would like to put my Windows Xp right next to the first entry of Ubuntu which is "Ubuntu, with linux 2.6......" 

I tried rearranging this via /boot/grub/grub.cfg but it doesn't look that simple.

summary: XP right next to Ubuntu (can be on top of Ubuntu or below Ubuntu) but Ubuntu still default OS.

---

### Post by akakingess on 2010-05-23
Which version of Ubuntu and Grub are you running?

---

### Post by l3ecl on 2010-05-23
Ubuntu 10.04

I do not know which version of grub that is, but I installed 10.04 from scratch, no upgrades from previous versions.

It seems the default OS is done by selecting who is on top of the list, so I can either:
a.) Ubuntu on top and XP second, and having the top most highlighted.
b.) Have XP on top and Ubuntu second,but have the second most (instead of top most) highlighted by default.

---

### Post by akakingess on 2010-05-23
Then you are using Grub 2, which is a little trickier to edit than it's predecessor so I would prefer to just point you to the help for editing Grub 2, which you can find by using the Ubuntu Help link at the top of the forum pages, but here is one [link]("https://help.ubuntu.com/community/Grub2") for you to check out, and if it doesn't have your answers, you can do another search for the Grub 2 manuals.

---

### Post by amite on 2010-05-23
u cannt modify grub.cfg as it is generated  by other files such as /etc/default/grub ,/etc/grub.d/ and usr/sbin/grub-mkconfig.

---

### Post by l3ecl on 2010-05-23
> **amite said:**
> u cannt modify grub.cfg as it is generated  by other files such as /etc/default/grub ,/etc/grub.d/ and usr/sbin/grub-mkconfig.

I edited it, putting windows on top, and the changed were actually reflected on the grub menu. Should I change this due to potential unforseen ramifications?

---

### Post by wojox on 2010-05-23
> **l3ecl said:**
> I edited it, putting windows on top, and the changed were actually reflected on the grub menu. Should I change this due to potential unforseen ramifications?

Yes as soon as you run 

```
sudo update-grub
```

It'll generate a new file.

See about Grub2 here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You may want to off load some of those kernels as well.

---

### Post by akakingess on 2010-05-23
> **wojox said:**
> Yes as soon as you run 

```
sudo update-grub
```It'll generate a new file.

See about Grub2 here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You may want to off load some of those kernels as well.

I guess I should have pointed it out, but that is the same link that I put in my previous post.

---

### Post by wojox on 2010-05-23
> **akakingess said:**
> I guess I should have pointed it out, but that is the same link that I put in my previous post.

Oh yeah, I see it now. I need to quit speed reading the post's. :)

---

### Post by akakingess on 2010-05-23
No biggie, I just didn't want the OP to think that there were 2 didn't versions of the same help/documentation. We are all here to help, anyhow ;)

---

### Post by l3ecl on 2010-05-23
got it working thanks alot!

---

