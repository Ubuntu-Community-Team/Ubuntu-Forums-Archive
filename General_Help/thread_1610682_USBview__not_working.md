---
title: "USBview  not working"
date: 2010-11-01
forum: General Help
---

### Post by burdebc on 2010-11-01
I recently posted this line of code into /etc/fstab in an effort to get /proc/bus/usb to mount "usbdevfs /proc/bus/usb usbdevfs defaults 0 0".  Now I am getting an error message during boot that reads "an error occurred while mounting /proc/bus/usb ...".  At this error message I press "S" to skip and Ubuntu boots normally.  And predictably when I try to use USBview I get the following error message:

              Can not open the file /proc/bus/usb/devices
              Verify that you have USB compiled into your
              kernel, have the USB core modules loaded, 
              and have the usbdevfs filesystem mounted.

I know enough to know that the code I mentioned earlier means I have made some success in getting the system to mount /proc/bus/usb, but I have no idea why it is failing.  I am trying to use the info from USBview to write a udev rule so that my USB TV tuner is named Video0 so that I can use TV time or Myth TV.  Any help in solving my immediate problem or helping me realize my end goal will be greatly appreciated (just keep in mind I am a complete noob).

---

### Post by burdebc on 2010-11-01
Just to check I commented out the code "usbdevfs /proc/bus/usb usbdevfs defaults 0 0" and the error message about mounting /proc/bus/usb is gone.  Of course USBview is still giving me the same error message, so this is a temporary bandage.

---

### Post by HiImTye on 2010-11-01
try running it as root and seeing if you have any more success


edit: nevermind skipped past the fstab part

---

### Post by burdebc on 2010-11-06
I just solved my own problem when I ran into a post  that is seemingly unrelated, but it works.  I just entered the following  two commands and USBview worked.

sudo mount --bind /dev/bus /proc/bus
sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices

here is a link to the post:
[http://ubuntuforums.org/showthread.p...does+not+exist]("http://ubuntuforums.org/showthread.php?t=1493771&highlight=mount+point+%2Fproc%2Fbus%2Fusb+does+not+exist")

---

### Post by geertsky on 2011-10-11
you could have also changed the location where is looked for usbdevfs.
Instead of /proc/bus/usb you can point usbview to /dev/bus/usb...


Regards,

---

### Post by wesmorgan1 on 2012-02-15
Porting usbview-1.1 to Ubuntu 11.10/GNOME 2.32.1/kernel 3.0.0-16-generic

1) Modify usbtree.c as follows:

Replace line 398:[INDENT]strcpy (devicesFile, "/proc/bus/usb/devices");
[/INDENT]with:[INDENT]strcpy (devicesFile, "/sys/kernel/debug/usb/devices");

[/INDENT]2) Follow the normal build procedure (run configure, then make, then make install if all looks good).

3) You'll have to run it with gksudo, because you need root privilege to read /sys/kernel/debug/usb/devices...

That's all!

I like this better because you don't have to do the symbolic linking described above...

---

