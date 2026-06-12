---
title: "Cancel automatic backup script"
date: 2010-04-14
forum: General Help
---

### Post by eZainny on 2010-04-14
Hi Everyone,

Linux/Ubuntu noob here so please be gentle :)

So I own an Ubuntu server (7.10 - "gutsy") which was previously used for my small business. All setup and maintenance of this server was done by an admin who has since moved on and I can't get in touch with.

As part of the setup, this admin has somehow setup the server such that whenever I plug in an external HDD (USB) it automatically runs a backup script which copies over a whole bunch of stuff to this drive.

I want to cancel/delete this script as this is no longer necessary. Can anyone give me any pointers as to how I could track down where this script is and how to remove it?

I can ssh and vnc in to the server as admin, but I'm a real real Linux noob so the more detailed your help, the better :)

Thanks!

---

### Post by eZainny on 2010-04-14
Hi All,

So I've been doing some investigation in to this and it seems that most people say that the way you would go about implementing this is in the /etc/udev/rules.d directory ( eg. [http://www.kevinblake.co.uk/auto-running-commands-when-plugging-in-usb-drives-with-udev-in-linux/732/](http://www.kevinblake.co.uk/auto-running-commands-when-plugging-in-usb-drives-with-udev-in-linux/732/) ) however none of the files in there jump out as me as having to do with running a backup script (but I'm not sure what's the best way to search for this either?)

Can anyone give me any pointers for how I could track this down?

---

### Post by 98cwitr on 2010-04-14
if you find the process using the ps -A command and then do a find command on the process you could do a pskill on it and then delete it if need be.

---

