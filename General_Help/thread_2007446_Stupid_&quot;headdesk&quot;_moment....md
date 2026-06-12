---
title: "Stupid &quot;headdesk&quot; moment..."
date: 2012-06-20
forum: General Help
---

### Post by solitaire on 2012-06-20
Feeling very stupid right now!!!
OK How do is sort the following problem...

Trying to make a boot-able USB stick with UNetBootin.
So i start it in superuser mode
Click the little elipses to find the ISO...

I'm using the trackpad of my laptop, so while clicking through the folders I accidentally Clicked/dragged the /lib/ folder in to /home/

Now basically i've got a trashed system!
"Terminal" does not start
No programs start!
Can only use what programs are currently running

SO... In a "file selection" window is it possible to Move things up a folder level so i can fix this sort of thing without resorting to looking for a boot-able USB stick.??

---

### Post by HarryTorry on 2012-06-20
If you have a different machine, you could probably make a symlink in /, that points to /home/lib/ (and call this symlink lib).
This is presuming that you can mount a usb or network drive without the use of /lib/.


Then open a terminal after that, ```
sudo mv /home/lib/ /
```

---

### Post by solitaire on 2012-06-20
Tried that! could not get anything to work

Spent 10 mins running around looking for a bootable CD or UDB with any version of ubuntu on it!

When it happened i was making a boot-able USB to reinstall my main machine.

Thankfully I found an old 10.04 boot CD and was able to boot my laptop with that and just move the folder back...

---

### Post by HarryTorry on 2012-06-20
I'm tempted to reproduce the issue, to see a way of fixing it without the use of a pre-existing boot medium to fix it!

---

### Post by solitaire on 2012-06-20
Was surprised I could actually FUBAR the system in a file selection window! lol

If you are EVER brave enough to do it. Let me know if you find a way to sort it ^_^

---

### Post by HarryTorry on 2012-06-20
I would just do it on a new install :P
(I don't currently have anything capable of running a VM without me wanting to tear my eyes out)

---

### Post by kanikilu on 2012-06-20
I actually reproduced this on my 11.10 VM, and as far as I can tell, it's not something you can fix in-place. Nothing works, no mounting, no sudo, mv, or even ls. Recovery mode also doesn't work. Had to do as the OP and use a Live CD (iso in my case), mount the partition and manually move lib back.

You'd be pretty much borked if you didn't have a backup if you deleted, rather than moved lib.

I think this is really bad design by Unetbootin, either don't allow you to do anything but select an ISO file in the dialog window, or somehow allow it to be run without root/sudo...

---

### Post by HarryTorry on 2012-06-20
Is there not a way to have a file dialogue that only graphically displays the files/directories, without giving any actual control?
Then from there, once the file is 'selected' the commands take place based on the actual location of the iso?

Even if it involves a bit of cheating;
Getting the list of directories/files, then creating a graphical output that has nothing to do with the actual filesystem. 
Then once the file is selected, the root/sudo commands take place?

---

