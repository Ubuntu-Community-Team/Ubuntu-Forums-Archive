---
title: "Netbook / Server or Netbook / Desktop"
date: 2011-07-27
forum: General Help
---

### Post by Mr. Beekeeper on 2011-07-27
I'm curious to get a few opinions on this, and I might be asking a stupid question to begin with, but:

I have a netbook and a desktop computer.  I'd like to use the netbook as more of a primary computer, and use the desktop as more of a backup and archive machine.  Is there a huge advantage to putting Ubuntu Server edition on the desktop machine?  I'd like to keep a GUI on the desktop machine so I could use it as a backup computer if need be.  Is it better to just stay with the Desktop version for the desktop machine?
I'm running Ubuntu on the netbook as well.  Any cool or interesting ways to set up the two?

8-[

Cheers! & Thanks!

---

### Post by Wim Sturkenboom on 2011-07-27
If you want it as a spare desktop system, use the desktop version. To my knowledge, there are **minor** differences under the hood. I would not worry about them.

You can read up on NFS to easily share your files.

---

### Post by Mr. Beekeeper on 2011-07-27
Thanks!

---

### Post by 2F4U on 2011-07-27
There are at least two differences that I am aware of:
- server kernel
- longer support for server lts edition 

If you intend to use it as kind of server, I would suggest to install 10.04 server lts.

---

### Post by nothingspecial on 2011-07-27
I'd just leave the desktop as it is. I take it, it is more powerful than the netbook.

You could use it to do the hard work and for storage. Install openssh-server on it.

Then on the netbook, go to the global menu bar at the top of the screen. Choose file > connect to server, then in the top box choose ssh. Fill in the username and ip address of the desktop and choose a bookmark name (eg desktop). Click connect and after typing in the desktop's password, check/tick the remember forever box.

Now you netbook will be able to access the desktop from the sidebar in the nautilus file manager.

[ATTACH]198577[/ATTACH]

---

