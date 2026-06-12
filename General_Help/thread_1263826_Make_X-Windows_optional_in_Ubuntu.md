---
title: "Make X-Windows optional in Ubuntu?"
date: 2009-09-11
forum: General Help
---

### Post by flicman on 2009-09-11
I installed Ubuntu Server, then installed the Xubuntu package (with the -no-recommended-options switch) in the hopes that I could use the GUI solely in case I needed it.  Now, however, the GUI boots automatically, and I can't figure out how to bring back my non-GUI boot.

Ideally, I'd like a normal Ubuntu Server load, then start X11 with 'startx' in the situation where I'd like it.

Is this possible?  Google hasn't been my friend on this one, sadly.

---

### Post by NoaHall on 2009-09-11
Try editing /etc/init.d/x11-common

---

### Post by flicman on 2009-09-11
Thanks for the pointer - is there something I should be looking for, specifically in x11-common? I have it up, but nothing is jumping out at me.

Thanks again.

---

### Post by NoaHall on 2009-09-11
Wait, wrong dir. Let me just check, need to restart, in Arch right now.

---

### Post by NoaHall on 2009-09-11
Right, two possible ways - boot into grub, press "e" on the kernel you wish to load, then just add a "3" before quiet. Or run "/sbin/init 3" from the terminal. Good luck

---

### Post by flicman on 2009-09-11
So I pretty much can't boot Ubuntu if there's a GUI installed and NOT boot into that GUI?  Running "$sudo /sbin/init 3" didn't do anything on my current install, and I don't want to have to be sitting at the terminal everytime I want to make sure I boot into a non-GUI enviornment.

I'm sure there's a way to do it, and I'm surprised that it's so difficult to find information on.  Maybe editing menu.lst to add the "level 3" switch to the main boot proceedure would work.

---

### Post by mcduck on 2009-09-11
> **flicman said:**
> I installed Ubuntu Server, then installed the Xubuntu package (with the -no-recommended-options switch) in the hopes that I could use the GUI solely in case I needed it.  Now, however, the GUI boots automatically, and I can't figure out how to bring back my non-GUI boot.

Ideally, I'd like a normal Ubuntu Server load, then start X11 with 'startx' in the situation where I'd like it.

Is this possible?  Google hasn't been my friend on this one, sadly.

Remove the desktop manager (GDM, KDM or whatever came with the Xubuntu package). If you had installed just XFCE instead of the whole Xubuntu  package you wouldn't have this problem.

---

### Post by flicman on 2009-09-11
ah-ha.

$sudo apt-get remove gdm 

seems to do the trick that I'm looking for, with the exception of the fact that I'm still getting a graphic at boot time.  I've seen that there are ways to change this, so the graphics don't show up, but if there's a way to uninstall or remove the files altogether, I'd rather do that.

Any advice on that one?

---

### Post by nikhilbhardwaj on 2009-09-11
try booting to a lower runlevel like runlevel 2
or better still remove the links from the /etc/init.d/rc{your runlevel}/
of the apps you don't want started automatically

---

### Post by mcduck on 2009-09-11
> **flicman said:**
> ah-ha.

$sudo apt-get remove gdm 

seems to do the trick that I'm looking for, with the exception of the fact that I'm still getting a graphic at boot time.  I've seen that there are ways to change this, so the graphics don't show up, but if there's a way to uninstall or remove the files altogether, I'd rather do that.

Any advice on that one?

So you mean you want to remove the boot splash as well? Just edit /boot/grub/menu.lst and remove the "splash" from the kernel's boot options (and from the default options-section).

I doubt that it's really even possible to remove the Usplash completely from your system, at least unless you start compiling your own kernels and building your own boot scripts, but at that point you probably should be running Gentoo or LFS, not Ubuntu. Anyway doing that wouldn't really give you any benefits unless you are very, very low on disk space.

---

### Post by flicman on 2009-09-11
This worked perfectly, thanks!

---

### Post by bodhi.zazen on 2009-09-11
> **nikhilbhardwaj said:**
> try booting to a lower runlevel like runlevel 2
or better still remove the links from the /etc/init.d/rc{your runlevel}/
of the apps you don't want started automatically

[nikhilbhardwaj]("http://ubuntuforums.org/member.php?u=842654") : Thank you for trying to help, but Ubuntu uses upstart and runlevesl 2,3,4, and 5 have all been the same for a long long time, at least as far back as I can recall.

---

