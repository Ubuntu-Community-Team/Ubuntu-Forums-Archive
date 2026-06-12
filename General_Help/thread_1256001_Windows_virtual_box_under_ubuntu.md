---
title: "Windows virtual box under ubuntu?"
date: 2009-09-02
forum: General Help
---

### Post by beak02 on 2009-09-02
Hi,

I'm running ubuntu and, as a music student, am required to have a copy of Sibelius on my laptop.  After much fighting with WINE I concluded that it wasn't going to work but I came up with the idea of installing it on a virtual machine.

This worked well until I try to get files on and off of the virtual machine.  I've installed guest additions and I still can't get Virtual-windows to recognise USBs.  I've also tried shared folders but can't find anything.

I know this isn't strictly and Ubuntu question but can someone please help or point me in the right direction of help.  Would be much appreciated!

Luke

---

### Post by P4man on 2009-09-02
Create a shared folder in VB setup. Then in windows, open a terminal (yes indeed :) ) and type:

```
net use x: \\vboxsvr\share
```

where "share" is the name of the share you configured earlier.

that will give you an X: drive which is a shared folder.

Alternatively you can browse network neighborhood and type in 
```
\\vboxsvr\share
```

To use USB devices in VB, you need the closed source edition, not the OSE one available in the official repo's.

---

### Post by argail1980 on 2009-09-02
Hi,

to get Files to and from a virtual machine you can setup a shared folder. 

1. Create a folder in your home directory (i.e. /home/<some user name>/windows).
2. Start the VBox control interface, choose "Shared folders" from the list on the left, add your new folder there and give it a share name i.e. "shared"
3. In Windows you can add a network drive with "//vboxsrv/shared" for the name of the share.

USB should work although I remember that in older versions one had to activate that separately in the config menu. Now I could not find the option anymore.

EDIT: D'oh!... only second place

---

