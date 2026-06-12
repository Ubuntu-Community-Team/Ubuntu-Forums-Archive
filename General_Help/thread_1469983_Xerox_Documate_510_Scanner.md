---
title: "Xerox Documate 510 Scanner"
date: 2010-05-02
forum: General Help
---

### Post by LesleyScherer on 2010-05-02
I've got a Xerox Documate 510 Scanner, which I love.  It only works, if I run 'sudo xsane,' but it works perfectly when I do that.

It seems to me, since xsane is obviously able to run the scanner - there ought to be something I can do to make it work without 'sudo.'

Can anyone help?

---

### Post by desertdog on 2010-06-23
The following is from [HTML]https://help.ubuntu.com/community/CompileSaneFromSource[/HTML] also see [HTML]https://help.ubuntu.com/community/SettingScannerPermissions[/HTML]

> Permissions

If you can scan as root, but not as user, you have a permissions issue. Current Ubuntu releases use udev to set permisions. To edit udev:

sudo gedit /lib/udev/rules.d/40-libsane.rules

and add the following two lines(change the scanner name and usb product id and vendor id to match your scanner):

# Canon CanoScan Lide 100
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1904", ENV{libsane_matched}="yes"

Save the file, exit gedit and Scan Away. 

Your scanner vendor id is 04a7. your product id is either 047c or 0446. run```
sane-find-scanner 
or 
lsusb
```
to find out for sure.

Also, your scanner is listed as unsupported by the sane website. So if you get it working, send a message to the sane-devel mailing list at [HTML]http://lists.alioth.debian.org/mailman/listinfo/sane-devel[/HTML]

Good luck

---

### Post by LesleyScherer on 2010-07-11
Thanks so much for the tips.  I think we are on the right track, but there is still a hitch.  I checked the device ID and it is 047c, so I edited the file, per your instructions and saved it.  

Now, when I try to run xsane, I get an error: "Failed to create file: Permission Denied"

When I close this dialog, xsane continues and does not find any scanner. 

Obviously you are correct, and this is a permissions issue.  I'll try to run it down, but I would appreciate any further input you might have. 

Also, assuming I get this working - is there a fix for Simple Scan as well?

---

### Post by LesleyScherer on 2010-07-11
Ok, now this is getting interesting...

I took a guess, based on the file permission denial dialog and changed the permissions on the file you suggested I edit - so that anyone can read/write or run it as a program.  I also turned the scanner off, then on again.

Now, both Xsane and Simple-Scan run perfectly as one user (normal.)  When I try to run Xsane as my master user (not sudo though) I get the file permission dialogue error, but afterwards the scanner is found and the program runs normally.  Then when I quit the program, the same dialogue appears three more times, before it will quit.  Simple-Scan runs fine as any user...

I realize there must be some caveats to letting any user read/write that file, but any security/system liabilities have got to be way less than running xsane as root...

It would be nice to clean up those dialogues though - any ideas anyone?

---

