---
title: "How to start X in chroot"
date: 2012-03-29
forum: General Help
---

### Post by maniaso on 2012-03-29
Hello,

I have installed ubuntu 11.10 and it´s starting in text mode in my machine.

I created the folder work/chroot and run a debootstrap to install the ubuntu inside chroot folder, I also installed gnome on it(chroot).
I run the commands below in order to me be able to work on the ubuntu in chroot environment.
sudo mount --bind /dev/ edit/dev sudo chroot chroot mount -t proc none /proc mount -t sysfs none /sys mount -t devpts none /dev/pts
export HOME=/root export LC_ALL=C
When I´m inside chroot and try to start X(startx) the display stay dark and gnome does not start...
I´d like to start gnome from chroot without export display... is there any way to do that?
I want to start the full gnome in order to personalize it.

Thanks in advanced.

---

### Post by Paddy Landau on 2012-03-30
I really don't know how to answer your question, but I have read that X should not be started that way. I could be wrong, though.

I would suggest that you start a new thread to solve your problem (Ubuntu starts in text mode) rather than trying to start X in chroot.

---

### Post by maniaso on 2012-03-30
Actually, I'd like to start ubuntu in text mode because I want to start X from chroot environment. I want to customize it in order to generate an livecd.

---

### Post by raja.genupula on 2012-03-30
[http://askubuntu.com/questions/22498/how-to-auto-boot-into-text-mode](http://askubuntu.com/questions/22498/how-to-auto-boot-into-text-mode)

---

