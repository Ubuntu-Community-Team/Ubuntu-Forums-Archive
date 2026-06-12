---
title: "Can't start the system with new kernel"
date: 2011-04-29
forum: General Help
---

### Post by pisahmet on 2011-04-29
Hi,

I have upgraded my Ub-10.10 to 11.04 yesterday. Everything works well except new kernel. When i try to boot with 2.6.38 kernel, i can't get to the desktop. Only black screen.

But when i try to boot with old kernel (2.6.35) from "Previous Linux" on GRUB, it works well without any problem.

PC Specs >> AMD Athlon X2 5200+, ASUS M2A-VM, OCZ 2 GB DDR2 800 Mhz RAM and Palit Sonic GTS 450.

---

### Post by dino99 on 2011-04-29
check that dkms is installed (with synaptic) then reinstall the latest kernel (headers & image)

sudo apt-get update
sudo apt-get install -f

if you have a xorg.conf file, remove it

sudo rm /etc/X11/xorg.conf

---

### Post by pisahmet on 2011-04-29
> **dino99 said:**
> 
if you have a xorg.conf file, remove it

sudo rm /etc/X11/xorg.conf

I did it. Now it opens but without 3D acc. :( :( :(

So Unity doesn't start :( And i tried to install prop-drivers but application didn't start. Giving this error on console:

```
pisahmet@pisahmet-maverick:~$ /usr/bin/jockey-gtk
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 418, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 461, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 81, in ui_show_main
    col_icon.set_sizing(Gtk.TreeViewColumnSizing.AUTOSIZE)
AttributeError: type object 'GtkTreeViewColumnSizing' has no attribute 'AUTOSIZE'

```

---

### Post by ben2talk on 2011-05-05
Actually, the previous poster made a serious error. You shouldn't go in removing your config files like that!

You should have done something like this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/Xorg.conf.2011-05-06
```

My defense mechanism is to edit the .bashrc file (which contains prefs for your newly opened terminals) like this:

```
gedit .bashrc
```

Then find the list of 'alias' commands and add these:

```
alias rm='mv -t ~/.local/share/Trash/files'
alias rm!='rm'
```

So if you REALLY want to delete files you need a little extra deliberate emphasis!!!

This would rename it (and render it invisible to the system) and give you the option to restore it. Renaming to the date is better, IMO, than simply 'bak' or 'removed' - but it's up to you how you 'remove' files.

This issue is affecting me also, but I don't have to go back to the 35 kernel.

For me, simply booting [COLOR="DarkRed"]**2.6.38-8-generic-pae**[/COLOR] leaves me very quickly looking at a black monitor.

Going to the older versions - booting [COLOR="SeaGreen"]**2.6.38-8-generic**[/COLOR] works fine.

Any ideas here folks?

I found a temporary solution is to switch

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

This program allows you to set the default kernel at boot time.

After booting, open SYNAPTIC and install the following:

linux-image-2.6.38-8-generic-pae
linux-generic-pae linux-headers-generic-pae 
linux-image-generic-pae 
linux-headers-2.6.38-8-generic-pae

Sorted - must have been incorrectly installed during the upgrade. Fine now.

---

