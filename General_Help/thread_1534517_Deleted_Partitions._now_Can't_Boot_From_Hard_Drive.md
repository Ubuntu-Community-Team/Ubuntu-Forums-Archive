---
title: "Deleted Partitions. now Can't Boot From Hard Drive"
date: 2010-07-19
forum: General Help
---

### Post by Mark76 on 2010-07-19
Why is grub such a menace? :(

---

### Post by pricetech on 2010-07-19
More information please.

---

### Post by Mark76 on 2010-07-19
I don't know any more.

All I know is I can't boot from the hard drive because grub doesn't see the partitions I have left.

I should make it clear, I only deleted partitions that I wasn't using (so my root and home partitions are still there, it's just that grub refuses to see them).

---

### Post by techunit on 2010-07-19
Well you probably deleted the partition that you had grub on... For Example I have grub installed on my Windows Vista Partition so I would have to reinstall ubuntu if I wanted only to have Ubuntu... (Thats the easy way)

What you could do is reinstall Ubuntu

---

### Post by Mark76 on 2010-07-19
Impossible. I have a separate home partition with all my personal data on and the new root won't see it.

There must be another way.

---

### Post by egalvan on 2010-07-19
> **Mark76 said:**
> I don't know any more.

All I know is I can't boot from the hard drive because grub doesn't see the partitions I have left.

 **I only deleted partitions that I wasn't using **(so my root and home partitions are still there, it's just that **grub refuses to see them)**.

Just because **YOU** were not using them does not mean that **GRUB** was not using them.  ;)

Anyway, try this post... #13 should be what you need

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


> Impossible. **I have a separate home partition** with all my personal data on and** the new root won't see it** 

Not sure at all what you mean by this...
but keeping HOME (and/or data) on a separate partition is one way to keep your data safe between installs...

---

### Post by Mark76 on 2010-07-19
Your link isn't working Egalvan

---

### Post by egalvan on 2010-07-19
> **Mark76 said:**
> Your link isn't working Egalvan

I tried it, and it works for me...

---

### Post by Mark76 on 2010-07-19
That's because you've just added it :p

It wasn't there before :lol:

---

### Post by anon.jdh on 2010-07-19
I've had this happen more times than I can count. 
If you wiped out a partition that you were no longer using, than re-install Ubuntu to that partition using the defaults.
You will see the new install and your old system in the Grub menu when you boot.

---

### Post by egalvan on 2010-07-19
> **anon.jdh said:**
> I've had this happen more times than I can count. 
If you wiped out a partition that you were no longer using, than re-install Ubuntu to that partition using the defaults.
You will see the new install and your old system in the Grub menu when you boot.

You have to make GRUB aware of the changes you've made...

most-times, running grub-update is enough...
some-times, you have to re-install GRUB.
In a few rare worst-case scenarios, you have to do a complete re-install

it's similar to moving to a new house/apartment...
if you don't let folks know about the move, they will be trying to find you at your old address...

---

### Post by Mark76 on 2010-07-19
I tried grub-update but it didn't work. Then I tried it from the grub prompt and it was an unknown command.

How do I reinstall grub to the hard disk?

---

### Post by oldfred on 2010-07-19
To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

You can reinstall grub2 with a liveCd:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by anon.jdh on 2010-07-19
> **egalvan said:**
> You have to make GRUB aware of the changes you've made...


When you reboot it will be using the freshly installed GRUB since it was originally wiped out.

This solution has worked for me recently.

---

