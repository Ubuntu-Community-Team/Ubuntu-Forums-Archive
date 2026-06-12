---
title: "help! how do i boot into command line mode?"
date: 2010-03-14
forum: General Help
---

### Post by Beowulf.1000 on 2010-03-14
EDIT:  **sudo /etc/init.d/gdm stop **   worked, not sure why it did not before. Sorry for the whining!

I need to boot Ubuntu into a non-x, command line mode. So I can install an nvidia driver for my new GeForce GTX 260 (I had a GeForce 7900 running on my Ubuntu system using the synaptic open source 185 driver for nvidia, but there is no driver except the one I downloaded just now from nvidia's site for the GTX 260 card). That requires there be no X session running, not even in a separate domain so to speak. There is no rescue mode in Grub2. Recover mode in Grub still boots an X session (Gnome). Alt+F1 appears to be a clean command line terminal but even that does not work because the nvidia driver installer script sees through that ruse and knows there is an active Gnome session. I tried sudo /etc/init.d/gdm stop and that did not work. I tried ctr+alt+backspace and that did nothing.

What can I do? I tell you some days linux is just too frustrating, about to just toss the baby with the bath water and go back to Winblows. Bought a new graphics card today, and here I am stuck not being able to even install the driver from a command line prompt, geesh.
 :0/

---

### Post by Chronon on 2010-03-14
[http://ubuntuforums.org/showthread.php?t=304325](http://ubuntuforums.org/showthread.php?t=304325)

---

### Post by steve19137 on 2010-03-14
when grub begins to load, hit esacpe. choose the second to top one. it will be about  a recovery mode. when that loads, choose the continue booting. it will lead you to a terminal login. use your username and password, and you have booted into terminal!

---

### Post by d3v1150m471c on 2010-03-14
boot into recovery mode then start normal or drop to root shell prompt. You'd think going to normal mode would load normally but it's always taken me to a big black terminal screen.

---

