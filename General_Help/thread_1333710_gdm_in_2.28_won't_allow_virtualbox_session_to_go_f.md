---
title: "gdm in 2.28 won't allow virtualbox session to go fullscreen"
date: 2009-11-21
forum: General Help
---

### Post by dmazzone on 2009-11-21
My netbook (Eeepc 1000heb) running 9.10 is setup to run VirtualBox as a GDM session. I set this up by putting a specialized .desktop file in ```
/usr/share/xsessions/
``` This always worked great until 9.10. Now it will still run  but putting the vm to full screen barely takes up half the screen. 

This doesn't seem to be a common setup and I can't find anyone else complaining about this. Anyone else out there have this problem or know a work around?

---

### Post by binojpb on 2009-12-01
You are not alone.  I too have the same problem.

---

### Post by Sefianix on 2010-04-06
I, too, am having the same problem.  This sucks b/c it worked so nicely before.

---

### Post by echeadle on 2010-04-17
If I understand the problem correctly, try this:

sudo Xorg -configure

It will create a xorg.conf.new file in your home directory. Under the Section "Screen" you will find subsections labled "Display" Depending on the Depth your display is using, or add to all, Add a line that looks like:  Modes "1024x768_60.00"

This assumes you are usuing a flatpanel display. If you are still using a crt make sure the refresh rates match what you set the monitor to.

Log out and log back in. Launch System>Preferences>Dislay  and you should now see the higher resolution.

I installed the Vbox tools, I don't know if it depends on installing them or not, but this worked and now I can actually use it.

I tried editing the file by hand, I copied and pasted things I found in the forum. I finally saw an article on the Fedora website that pointed me to the Xorg command.  

Hope this helps

---

### Post by echeadle on 2010-04-17
Sorry forgot one step. You need to copy the xorg.conf.new file to /etc/X11/xorg.conf  then logout and then back in.

---

