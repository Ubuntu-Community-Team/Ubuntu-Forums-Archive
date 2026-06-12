---
title: "Can't install VirtualBox - Running Kubuntu 9.10"
date: 2010-04-02
forum: General Help
---

### Post by ShadowsOfSilver on 2010-04-02
Hello there. I have Kubuntu 9.10, and run "sudo apt-get install virtualbox" in the terminal, but all I get is:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package virtualbox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package virtualbox has no installation candidate

```

Why is this is happening? :(

---

### Post by Scunizi on 2010-04-02
You could try "apt-cache search virtualbox" and see what turns up.. Most likely it will be virtualbox-ose.  However if you want the latest version and one with usb support then download the ubuntu .deb from virtualbox.org.  #vbox is a great source of information on IRC.. keep in mind that most that hang out there are typically in a european time zone.

---

### Post by ShadowsOfSilver on 2010-04-02
Yup, it showed up as ose. Thank you for the help! Yeah, I'm probably gonna download the new version - my internet adapter is a USB one. Thanks!

---

### Post by Scunizi on 2010-04-02
You should mark this thread as "Solved".. You're welcome!

---

