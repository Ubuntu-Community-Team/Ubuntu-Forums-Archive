---
title: "Missing Desktop"
date: 2009-10-30
forum: General Help
---

### Post by Pitster on 2009-10-30
The other week whilst using Synaptic to remove Evolution (I prefer Thunderbird) I must have gone too far and now when booting into Ubuntu I only het a black screen and mouse pointer.  I have tried using Failsafe Gnome to rectify the problem but it doesn't, and boots into the command line.

I have tried to install Gnome using the command line but haven't managed to fix anything and so any advice and help would be much appreciated.  

Thanks

---

### Post by fooman on 2009-10-30
i know that when uninstalling certain parts of evolution,  it also wants to uninstall ubuntu-desktop along with a bunch of other packages.

if you can get to the command line again,  try this:

```
sudo apt-get install ubuntu-desktop
```see if that helps.

---

### Post by Pitster on 2009-10-30
Thanks for your reply.  That looked like it was going to work, but then stopped installing packages and told me I needed updates and to run apt-get updates.

However, the updates did not work as it was unable to resolve security.ubuntu.com.  Or something like that.  I'm having to boot in and out between Ubuntu and Vista partitions to get back on line to write on this thread!

---

### Post by fooman on 2009-10-30
try rebooting and when you get to the grub menu....choose recovery mode.

when you get to the recovery mode options....choose "root shell with networking" (not sure of exact wording....but it is similar)

when you get to the command line prompt again....try:

```
sudo apt-get update
```

and then:

```
sudo apt-get install ubuntu-desktop
```

hope that works for you.

---

### Post by Pitster on 2009-10-30
Thanks again, but a similar thing happened.  Unable to resolve gb.archive.ubuntu.com

---

