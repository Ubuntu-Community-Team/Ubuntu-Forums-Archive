---
title: "Display terminal commands"
date: 2009-09-22
forum: General Help
---

### Post by Ammon Van Meter on 2009-09-22
Recently, I have been itching to use Ubuntu again. However, I have lost my list of commands formy terminal. I have checked the For absolute for beginners thread and it's been archived or closed(?). Any rate, I would like to know the terminal command for the display properties.

The command went something like

sudo display -gtk.

It had -gtk in it, but I forgot the command. 

I am running a laptop 1.5 with 1 GB RAM and a VIA unichrome display.

---

### Post by twan_van_der_poel on 2009-09-22
Hi Ammon,

perhaps you mean "pvdisplay" ?

Let me know if it worked out.

Regards,

Twan van der Poel

---

### Post by geirha on 2009-09-22
Or «gnome-display-properties» (withOUT sudo), the one you open from System -> Preferences -> Display ?

---

### Post by NoaHall on 2009-09-22
gksudo gconf-editor

---

### Post by raymondh on 2009-09-22
for future reference .... and welcome back.

[http://oreilly.com/linux/command-directory/](http://oreilly.com/linux/command-directory/)

---

### Post by kerry_s on 2009-09-22
> **Ammon Van Meter said:**
> Recently, I have been itching to use Ubuntu again. However, I have lost my list of commands formy terminal. I have checked the For absolute for beginners thread and it's been archived or closed(?). Any rate, I would like to know the terminal command for the display properties.

The command went something like

sudo display -gtk.

It had -gtk in it, but I forgot the command. 

I am running a laptop 1.5 with 1 GB RAM and a VIA unichrome display.


```
sudo su
X -configure
nano /root/xorg.conf.new
cat /root/xorg.conf.new > /etc/X11/xorg.conf
```

---

### Post by Ammon Van Meter on 2009-09-22
I have found it, thank you guys for the help.

The code was
gksu displayconfig-gtk

Thank you for your help and time.

---

### Post by ItalOz on 2010-05-23
> **geirha said:**
> Or «gnome-display-properties» (withOUT sudo), the one you open from System -> Preferences -> Display ?

Thanks to the forums, there is always somebody out there, this was just what I needed!

---

