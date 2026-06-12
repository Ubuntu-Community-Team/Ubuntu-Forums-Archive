---
title: "VirtualBox Geust Additions 9.10 Error"
date: 2009-10-17
forum: General Help
---

### Post by EGadZooks on 2009-10-17
Hello
I run 9.04.  I have installed 9.10 beta into a virtual box and am attempting to install the Guest Additions.

It clears the
"Building the VirtualBox Guest Additions kernel module..."
then moves to the
"Building the shared folder support kernel module..."
at which point it says "unable to build the kernel module, see log file /var/vboxadd-install.log for more details"

I did some google searches and a few days ago someone posted the exact log into a pastebin found here: [http://pastebin.ca/1611896](http://pastebin.ca/1611896)

but at the end is the error here

```
#
/tmp/vbox.1/utils.c: In function ‘sf_path_from_dentry’:
#
/tmp/vbox.1/utils.c:362: error: implicit declaration of function ‘utf8_wctomb’
#
/tmp/vbox.1/utils.c: In function ‘sf_nlscpy’:
#
/tmp/vbox.1/utils.c:420: error: implicit declaration of function ‘utf8_mbtowc’
#
make[2]: *** [/tmp/vbox.1/utils.o] Error 1
#
make[1]: *** [_module_/tmp/vbox.1] Error 2
#
make: *** [vboxvfs] Error 2

```

Thank you :)

---

### Post by EGadZooks on 2009-10-17
On restart of the 9.10 beta in the virtual box it looks like the guest additions are functioning, but not the shared folder capabilities.

---

