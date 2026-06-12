---
title: "Screen and VirtualBox"
date: 2010-05-01
forum: General Help
---

### Post by autonomy on 2010-05-01
Hello, since upgrading to Lucid, I'm having problems with Screen and VirtualBox, and the problems seem similar as if crucial components have vanished. Here is the screen issue: [https://bugs.launchpad.net/ubuntu/+source/screen/+bug/172651](https://bugs.launchpad.net/ubuntu/+source/screen/+bug/172651) and the last three posts are me. Basically, the solutions have been temporary so far. I changed the mode and group of /var/run/screen like the OP said but have not shutdown yet, so I don't know if that's a permanent solution yet. The other two temporary solutions didn't prove to be temporary until I shutdown and came back several hours later. Screen was still working after a reboot.

The same thing is happening with VBox: after doing what VBox tells me to do, the solution was temporary, and the same problem popped up after the next boot. Here are similar problems: [https://lists.ubuntu.com/archives/universe-bugs/2009-June/105030.html](https://lists.ubuntu.com/archives/universe-bugs/2009-June/105030.html) and [http://ubuntuforums.org/archive/index.php/t-593512.html](http://ubuntuforums.org/archive/index.php/t-593512.html). I made sure I was in the vboxusers group. I added the module like the first one said, and it took me to another level of malfunction. I didn't take a screenshot or make a note of the first error message, but I've attached the second. Also, [FONT=Courier New]sudo /etc/init.d/vboxdrv setup[/FONT] did not work this time after adding the module. Like the first link said, vboxdrv didn't exist for him or her, so maybe my problem is similar. My terminal says it "Cannot unload module vboxdrv".

---

### Post by keithspg on 2010-05-02
The version of virtualbox is out of date that installs with Lucid. I am installing the Karmic variant and we will see if that works. I am sure these glitches will be fixed shortly.

Keith

---

### Post by autonomy on 2010-05-02
Yeah, VirtualBox doesn't even have a Lucid repo yet.

---

### Post by autonomy on 2010-05-02
I had no problem, today, so maybe the last things I did yesterday worked as permanent solutions.

---

### Post by autonomy on 2010-05-08
I don't know if it makes a difference or if it's just a coincidence that happens after running once, but I tried ```
sudo invoke-rc.d vboxdrv setup
``` after ```
sudo /etc/init.d/vboxdrv setup
``` and instead of doing this again ```
 * Stopping VirtualBox kernel module

 * Cannot unload module vboxdrv
```it did this ```
 * Stopping VirtualBox kernel module
 *  done.
 * Removing old VirtualBox netadp kernel module
 *  done.
 * Removing old VirtualBox netflt kernel module
 *  done.
 * Removing old VirtualBox kernel module
 *  done.
 * Recompiling VirtualBox kernel module
 *  done.
 * Starting VirtualBox kernel module
 *  done.
```

---

### Post by gerowen on 2010-05-08
I've always just went to Sun's (Now Oracle's) website and downloaded that version of Virtualbox.  The one in the repos doesn't come with the Guest Additions ISO and stuff so I just find it easier to grab the deb straight from the software developer.  Give it a shot.

---

