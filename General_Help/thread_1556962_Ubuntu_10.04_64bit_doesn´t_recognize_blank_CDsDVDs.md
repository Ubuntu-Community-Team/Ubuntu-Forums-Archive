---
title: "Ubuntu 10.04 64bit doesn´t recognize blank CDs/DVDs"
date: 2010-08-20
forum: General Help
---

### Post by vickoxy on 2010-08-20
Hi,
i have severe problem with my Thinkpad R500 - it simple doesn´t recognize/won´t mount any blank/empty dvd. 
1) First, it is not hardware Problem: DVD Burner read all formats, and works good under Windows.
2) it is not CD/DVD Format issue- i tested Fuji, Platinum, Sony, CD-R, CD-RW, DVD-R...
3) it has nothing to do with brasero. I tested k3b, gnomebaker, nautilu-cd-burner and some other problems.

So, this Issue make my dvd burner useless...

Does anyone knows if this problem is solved, or what bug should i report?

Thanks for any help.

P.S. I tested linuxmint 9, mint 7 but the issue is still there...

---

### Post by ellgor on 2010-08-20
Hi,

Sorry to say I've had the same problem, Linux Mint 9 64bit, I have an older rig and I only noticed this when I burnt a dvd and when I came to play it, it wasn't recognised, stuck in another new disc, not recognised, re-installed k3b and all the associated apps to no avail, finally I had a newer dvd drive to hand swapped them and things are back to normal, not sure why it failed in the first place and hope it doesn't again, got no more dvd drives one last thing if your drive is a bit old, you could install an older version of k3b which I shall put here, remove the current one and get this (you might have to look for the 64bit version)


[http://packages.ubuntu.com/jaunty/libk3b3](http://packages.ubuntu.com/jaunty/libk3b3)
[http://packages.ubuntu.com/jaunty/k3b-data](http://packages.ubuntu.com/jaunty/k3b-data)
[http://packages.ubuntu.com/jaunty/k3b](http://packages.ubuntu.com/jaunty/k3b)

to stop it from being upgraded you might want to put this in /etc/apt/ preferences

sudo gedit /etc/apt/preferences

Package: k3b
Pin: version 1.0.5*
Pin-Priority: 1001

Package: k3b-data
Pin: version 1.0.5*
Pin-Priority: 1001

Regards, Ellgor.

---

### Post by vickoxy on 2010-08-20
Well, i tried that, but as said i don´t think it is cd burner software causing problems. I am having only this message:
> No CD/DVD Writer found

And, as said, the hardware is pretty new-Thinkpad R500, maybe 6 Months old...

---

