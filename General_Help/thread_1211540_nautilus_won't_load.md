---
title: "nautilus won't load"
date: 2009-07-12
forum: General Help
---

### Post by Coder543 on 2009-07-12
On this one computer, I used a USB livecd to boot ubuntu. It worked fine, I resized one of the partitions on the computer and now it refuses to load nautilus or brasero. It claims there isn't enough memory left to show the bug report, even though almost none of the RAM is in use. On a different computer it loads fine. It mentions something about a DBus error or GLibC error. suggestions?

---

### Post by Coder543 on 2009-07-17
*bump* This would be really nice if it could be helped because this is probably the main chance i'm going to have to get this guy to start switching to ubuntu.

---

### Post by jonobr on 2009-07-17
recommend you post the system specs and the actually error your seeing,

glibc is the GNU c library and d bus stands for desktop bus which allows apps to talk to each other,
without the actual error its hard to know whats up, but Im thinking a reinstall of your dektop may work as there may be IPC issues on your initial install

---

### Post by Coder543 on 2009-07-17
But the confusing part is that this is coming from a livecd, not an installation of Ubuntu. This same livecd popped into another computer results in a happy desktop environment. I don't have the exact error at the moment though.

---

### Post by jonobr on 2009-07-17
found this in an older post,
not sure it will help your but all I had to going on was the error workds you gave,
the exact error may help

Boot with the LiveCD.
Select the "Start or Install" option
Press F6 to open the boot options
Before the "--" at the end of line, enter the following parameters (all in the same line) :
mem=192m (where 192m means 192MB of RAM - use a number lesser than your max RAM installed in your machine)
fb=false video=vga16:off
disable_dhcp=true
start_pcmcia=false


One of these worked, some of them may be defunt

---

