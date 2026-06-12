---
title: "Ubuntu 12.04 Where are my ttys?"
date: 2012-06-11
forum: General Help
---

### Post by pepsifx357 on 2012-06-11
I have an Nvidia card, which is probably the problem.  I get a lot of abbrupt Xorg restarts when I'm watching YT vids or playing Minecraft, which deletes your saved games/worlds. Another problem is, When I hit the good ol' ctrl alt F1, 2, 3, 4, 5, or 6 to get to any of the terminals, my monitor turns off.  Clearly a video problem.  Right now I'm using the only Nvidia driver that seems to barely work for me in Ubuntu 12.04, 295.59 from Nvidia.  The default Nvidia driver from the repos turned my computer into a paper weight.  I've downloaded quite a few updates for X, but nothing that changes this disaster desktop experience.  lol

Is anyone else having these problems, and if yes, how long should we expect either X or Nvidia to fix this?

:confused:

---

### Post by pepsifx357 on 2012-07-02
As of today.  I'm still missing this feature.

---

### Post by Grenage on 2012-07-02
I don't have that problem on any of my 12.04 builds, and all have Nvidia cards with proprietary drivers.  Have you taken a look at xorg's error logs?  It's more than likely:

a) Failing hardware
b) Corrupt/bodged software

If it isn't, you'll probably want to report it as a bug.

> **pepsifx357 said:**
> how long should we expect either X or Nvidia to fix this?

They don't read the forums, and they can't read minds - as handy as that would be.

---

### Post by sgage on 2012-07-02
> **Grenage said:**
> I don't have that problem on any of my 12.04 builds, and all have Nvidia cards with proprietary drivers.  Have you taken a look at xorg's error logs?  It's more than likely:

a) Failing hardware
b) Corrupt/bodged software

If it isn't, you'll probably want to report it as a bug.



They don't read the forums, and they can't read minds - as handy as that would be.

It is not failing hardware, nor corrupt software. It is a known regression/bug in the nvidia drivers that seems to have been given extra-super-low priority, probably because it only affects certain nvidia gpus. Naturally, it affects Series 8, which is what I have (8500 GT). This has been a problem for months, but I wouldn't hold my breath waiting for them to address it. 

Just like jockey says - when using proprietary drivers "security updates and corrections depend solely on the responsiveness of the manufacturer". :KS

---

### Post by Grenage on 2012-07-02
That's odd, I've got a couple of machines with 8400s; I guess I've been lucky!

---

### Post by sgage on 2012-07-02
> **Grenage said:**
> That's odd, I've got a couple of machines with 8400s; I guess I've been lucky!

Yes, you have! It's pretty hit or miss. But it is a real issue. 

My graphical needs are minimal, so I've just reverted to nouveau. I like having virtual terminals available...

---

### Post by pepsifx357 on 2012-07-02
> **sgage said:**
> Yes, you have! It's pretty hit or miss. But it is a real issue. 

My graphical needs are minimal, so I've just reverted to nouveau. I like having virtual terminals available...

How do you revert back to nouveau?  I've removed Nvidia and reinstalled Nouveau, but I used the Nvidia binary package from their website and I remember it making changes to some xorg files to get rid of nouveau.

---

### Post by sgage on 2012-07-02
> **pepsifx357 said:**
> How do you revert back to nouveau?  I've removed Nvidia and reinstalled Nouveau, but I used the Nvidia binary package from their website and I remember it making changes to some xorg files to get rid of nouveau.

I think if you go to /etc/X11 and simply remove xorg.conf you should be good to go.

[Edit - if that doesn't work, you may need to go to /etc/modprobe.d, and see if there is a blacklist-nvidia.conf file - if so, delete it, and reboot.]

---

