---
title: "Help With Usplash"
date: 2010-06-01
forum: General Help
---

### Post by DinoT1985 on 2010-06-01
Hi guys

I seem to have a problem with my loading screen in 10.04. I get the Ubuntu name twice on either side of the screen with screwed up colours like vivid reds and greens. Any way to fix this?

Also does Lucid Lynx still use Usplash for the loading screen?

One last note. I don't like the new loading screen. I preferred 9.10, which looked more clean and high-end with the gradients and light bar. Any way to get that back or even edit the background image of it?

Thanks :)

---

### Post by dino99 on 2010-06-01
plymouth is used instead of usplash with lucid

your problem seems to be due to graphic driver, which one is used ? with which card ?

as lucid dont need xorg.conf by default, remove it if it exist:

sudo rm -f /etc/X11/xorg.conf

you might look at "system admin log viewer" menu for errors, and .Xsession-errors into /home (unhide it with menu)

---

### Post by DinoT1985 on 2010-06-01
I'm using the updated NVIDIA accelerated graphics driver with a NVIDIA GeForce 9600M GT card. THis problem only happened about two days ago. Prior it worked well.

Trying the xorg removal now. 

Here is my xsessions log.

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-MsFhVW
GNOME_KEYRING_PID=2253
GNOME_KEYRING_CONTROL=/tmp/keyring-MsFhVW
GNOME_KEYRING_CONTROL=/tmp/keyring-MsFhVW
SSH_AUTH_SOCK=/tmp/keyring-MsFhVW/ssh

(polkit-gnome-authentication-agent-1:2287): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2287): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: adding killswitch idx 0 state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1
** (nm-applet:2285): DEBUG: old state indicates that this was not a disconnect 0
Starting gtk-window-decorator
Initializing nautilus-image-converter extension
I/O warning : failed to load external entity "/home/dino/.compiz/session/10600cd2c4fe620e48127539801193995000000020580040"
Initializing nautilus-gdu extension
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Unable to open desktop file 
.desktop for panel launcher
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
done

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
** (update-notifier:4106): DEBUG: Skipping reboot required

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Generating grub.cfg ...

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
done
Grub2 detected
Usplash not detected
Splashy not detected

(gnome-terminal:11234): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(gnome-terminal:23065): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
done

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Generating grub.cfg ...

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
done
Grub2 detected
Usplash not detected
Splashy not detected

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
cp: missing file operand
Try `cp --help' for more information.

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
/usr/share/software-center/softwarecenter/view/appview.py:737: DeprecationWarning: integer argument expected, got float
  h)
ERROR:root:error in _on_trans_finished 'Error: Package dependencies cannot be resolved
This error could be caused by requiring additional software packages which are missing or not installable. Alternatively, there could be a conflict between software packages which are not allowed to be installed at the same time.

usplash-theme-ubuntu-color'

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(gnome-terminal:19315): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(gnome-terminal:20721): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Initializing nautilus-clamscan extension
Shutting down nautilus-gdu extension
Shutting down nautilus-image-converter extension

--- Hash table keys for warning below:
--> dino
--> inode/directory
--> Dino Tassigiannis
--> l2049

(nautilus:2291): Eel-WARNING **: "unique eel_ref_str" hash table still has 4 elements at quit time (keys above)

(nautilus:2291): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
Initializing nautilus-image-converter extension
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(gnome-terminal:7451): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Initializing nautilus-clamscan extension
Shutting down nautilus-gdu extension
Shutting down nautilus-image-converter extension
Initializing nautilus-image-converter extension
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(gnome-terminal:17192): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
sys:1: GtkWarning: Icon size name 'GTK_ICON_SIZE_STATUSBAR' already exists

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(gnome-appearance-properties:18852): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:18852): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
/usr/share/themes/Night-Impression/gtk-2.0/gtkrc:237: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:178: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:331: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:338: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:352: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:374: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:376: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:400: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:406: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:445: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:451: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:528: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:561: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:563: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:582: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:583: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:617: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:618: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:658: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:660: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:683: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:685: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:717: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:718: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:732: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:733: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:752: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:754: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:783: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:786: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:802: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:818: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:841: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:882: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:889: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:908: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:915: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:954: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:956: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:1012: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:1019: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:1206: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:1209: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:1294: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:1301: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:1338: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:1340: Murrine configuration option "profile" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:1355: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Impression/gtk-2.0/gtkrc:1360: Murrine configuration option "profile" is no longer supported and will be ignored.

(polkit-gnome-authentication-agent-1:2287): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(polkit-gnome-authentication-agent-1:2287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(gnome-appearance-properties:18853): Gtk-WARNING **: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(gnome-terminal:20722): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(gnome-terminal:20745): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3337): Gdk-WARNING **: XID collision, trouble ahead
```

---

### Post by DinoT1985 on 2010-06-01
Removing xorg.conf just decreased my screen resolution and detached NVIDIA from controlling my graphics. 

I ended up recreating it with
sudo nvidia-config 
which has solved my resolution problems. 

Upon rebooting, my screen was fixed so I put it down to a corrupt xorg.conf file.

---

