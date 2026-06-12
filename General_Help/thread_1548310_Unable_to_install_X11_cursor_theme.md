---
title: "Unable to install X11 cursor theme"
date: 2010-08-08
forum: General Help
---

### Post by Heliooos on 2010-08-08
Hi,
I know it sounds silly but I am unable to install this mouse theme:

especially the Vast version from [this link]("http://dl.dropbox.com/u/6066212/ComixCursors-Vast-0.5.0.tar.bz2&usg=AFQjCNEseZRKzDoPrnWECIIxjJAH1LQ9nQ")

First I used my commonly used method which worked in most distros I ever used - simply unpacked with archiver and put the folders to /usr/share/icons with root nautilus.

However I did not see the cursor in gnome theme settings so tried second one possibility, which worked in Debian - I packed one of the unpacked folder to tar.gz and drag it onto theme settings - first it looked promisingly but then I got message like "Cannot drag folder over the folder" (translated from Czech).

I found that the cursor is also unpacked to home/.icons/ and following recommendation of one forum, I also installed Gcursor. Gcursor sees the theme, but is not able to select it and running it via terminal shows me this:
```
petra@HP550:/home/psychopetra/Plocha$ gcursor

(gcursor:3629): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gcursor:3629): libglade-WARNING **: could not find signal handler 'entry_selected'.

(gcursor:3629): libglade-WARNING **: could not find signal handler 'open_theme_dir'.

(gcursor:3629): libglade-WARNING **: could not find signal handler 'size_changed'.

(gcursor:3629): libglade-WARNING **: could not find signal handler 'extract_theme'.
petra@HP550:/home/psychopetra/Plocha$ 

```

Any ideas? My sister is visually impaired and needs this big cursor theme. [Here]("http://www.limitland.de/comixcursors.html") are some screenshots of her old laptop running Xfce with this huge cursor.

thanks much

PS: my PC specifications are: 
Ubuntu Lucid Lynx (Vinux 3.0)
HP 550 laptop
Celeron-M 550 2.00GHz &#8226; 1024MB &#8226; 160GB &#8226; DVD+/-RW DL &#8226; Intel GMA X3100
(IGP) max. 384MB shared memory &#8226; 3x USB 2.0/Modem/LAN/WLAN 802.11bg &#8226;
ExpressCard slot &#8226; SD card slot &#8226; 15.4" WXGA glare TFT (1280x800) &#8226;
FreeDOS &#8226; Li-Ion battery (6 cells) &#8226; 2.50kg

---

