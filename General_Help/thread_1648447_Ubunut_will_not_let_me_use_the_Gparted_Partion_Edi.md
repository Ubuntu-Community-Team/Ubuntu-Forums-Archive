---
title: "Ubunut will not let me use the Gparted Partion Editor"
date: 2010-12-18
forum: General Help
---

### Post by Luke oX on 2010-12-18
I have had this same problem with Fedora and Ubuntu 10.10. This is what I get if I try to use Gparted, [IMG]http://img202.imageshack.us/f/screenshotnqc.png/[/IMG]http://img202.imageshack.us/f/screenshotnqc.png/

Please help...[IMG]http://img202.imageshack.us/f/screenshotnqc.png/[/IMG]

---

### Post by Quackers on 2010-12-18
Did you mean to post a screenshot?

---

### Post by Luke oX on 2010-12-18
> **Quackers said:**
> Did you mean to post a screenshot?

For some reason the image feature isn't working for me, so there is the link, sorry.

---

### Post by Quackers on 2010-12-18
> **Luke oX said:**
> For some reason the image feature isn't working for me, so there is the link, sorry.

oops, neither is the link :-)
You can just paste the link in to your post.

---

### Post by Quackers on 2010-12-18
Aha! I see you edited the first post :-)
Have you resized any partitions recently? If so, which partitions, and what program did you use?

---

### Post by Luke oX on 2010-12-19
> **Quackers said:**
> Aha! I see you edited the first post :-)
Have you resized any partitions recently? If so, which partitions, and what program did you use?

No I haven't resized it, my computer is using the RAID option where it sees two hard drives as one so I think that might be the problem.

---

### Post by ronparent on 2010-12-19
To make a long story short, if you are using 10.04 or 10.10, you need to install kpartx ('sudo apt-get install kpartx') to enable gparted to read the raid partitions. The problem has supposedly been fixed upstream.

---

### Post by Luke oX on 2010-12-19
> **ronparent said:**
> To make a long story short, if you are using 10.04 or 10.10, you need to install kpartx ('sudo apt-get install kpartx') to enable gparted to read the raid partitions. The problem has supposedly been fixed upstream.

Thanks a ton man! I'll be sure to try this out.

---

### Post by Luke oX on 2010-12-20
> **ronparent said:**
> To make a long story short, if you are using 10.04 or 10.10, you need to install kpartx ('sudo apt-get install kpartx') to enable gparted to read the raid partitions. The problem has supposedly been fixed upstream.
I tried sudo apt-get install kpartx in the command line and I got "Invalid operation install"...

---

### Post by ronparent on 2010-12-21
???????????? Pozzling.

I just tried cutting and pasting your command and it works fine!

It doesn't matter. You can also install with either Synaptics or the Ubuntu Software Center. Do a search in either for 'kpartx'.

---

### Post by Luke oX on 2010-12-21
> **ronparent said:**
> ???????????? Pozzling.

I just tried cutting and pasting your command and it works fine!

It doesn't matter. You can also install with either Synaptics or the Ubuntu Software Center. Do a search in either for 'kpartx'.

So you have no idea how I can install it on RAID without kpartx command not working?

---

### Post by ronparent on 2010-12-21
If gparted isn't showing the raid partitions, Ubuntu is uninstallable on the raids using the desktop distro. It is a simple matter to install kpartx to a live cd session and from there (without a reboot) go on to the install. With 10.10 the install proceeds normally in most cases and grub2 is written to the raid MBR. With 10.04 it gets a bit more complicated and you have to reinstall grub to place the grub boot on the raid (or wherever else you may want it).

---

### Post by psusi on 2010-12-21
> **ronparent said:**
> If gparted isn't showing the raid partitions

Not true.  The installer will see the raid array and partition it just fine, it's just a bug in gparted that prevents it from listing the array in the drop down list.  You can get around it easily either by installing kpartx, or running gparted from the command line and giving it the path to the raid array as an argument.

---

### Post by Luke oX on 2010-12-21
> **psusi said:**
> Not true.  The installer will see the raid array and partition it just fine, it's just a bug in gparted that prevents it from listing the array in the drop down list.  You can get around it easily either by installing kpartx, or running gparted from the command line and giving it the path to the raid array as an argument.
I have no idea how to do that.

---

### Post by ronparent on 2010-12-21
I do know how to do that, but, at this stage you don't need to know. A temporary install of kpartx to a live cd session does allow a normal running of the installer within that same session to install to a raid array.

---

