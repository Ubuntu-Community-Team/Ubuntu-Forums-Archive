---
title: "How Do I Edit File Owned By Root?"
date: 2010-05-31
forum: General Help
---

### Post by Dynamata on 2010-05-31
I am trying to edit limits.conf, changed file permissions:

sudo chmod limits.conf -rwxrwxrwx

but got this message:

"Could not save the file /etc/security/limits.conf.
You are trying to save the file on a read-only disk. Please check&#65279; that you typed the location correctly and try again."

I followed these instructions:

"copy - paste this code into terminal

gedit $HOME/.gnome2/nautilus-scripts/Open\ as\ root

copy-paste this text into that file and push 'save'

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
    gnome-sudo "gnome-open $uri" &
done

now copy-paste this code into terminal

chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root

Now you can right click on the file you want to edit, select 'scripts' and say 'open as root' to let you modify it".

[http://ubuntuforums.org/archive/index.php/t-43598.html](http://ubuntuforums.org/archive/index.php/t-43598.html)

the right click worked but the file didn't open. :confused:

---

### Post by harrismh777 on 2010-05-31
you might try:

cd /etc/security/

gksudo gedit limits.comf

-------------------------------------

sudo vi limits.conf      also works well

---

### Post by Dynamata on 2010-05-31
No that didn't work, got the same error message, think I need to unlock the drive.

---

### Post by harrismh777 on 2010-05-31
Yes.,  once again Occam's Razor holds valid...

[http://pespmc1.vub.ac.be/occamraz.html](http://pespmc1.vub.ac.be/occamraz.html)

---

### Post by Dynamata on 2010-05-31
All I'm trying to do is get JACK audio to work so I can use Rosegarden, editing limits.conf is part of that process. Why do you need a PhD to edit a file in Linux?

---

### Post by xfearxnxloathing on 2010-05-31
sudo gedit

---

### Post by Dynamata on 2010-06-01
I logged in as root but the disk is read only, how do I make it writeable?

---

### Post by xfearxnxloathing on 2010-06-01
> **Dynamata said:**
> I logged in as root but the disk is read only, how do I make it writeable?

change the permissions once logged in as root.  rightclick go to properties>permissions

---

### Post by scouser73 on 2010-06-01
**1** - Go to **Applications** > **Accessories** & select **Terminal**, copy & paste this command: > **gksudo nautilus** that will open Terminal as root

**2** - Navigate to the folder or file or drive you wish to gain permissions on, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder or file or drive.

---

### Post by Barrucadu on 2010-06-01
If the disk is read-only, simply remount it as read-write:

```
sudo mount -o remount,rw /path/to/mountpoint
```

You can then edit the file using whatever method you choose.

---

### Post by aysiu on 2010-06-01
> **Barrucadu said:**
> If the disk is read-only, simply remount it as read-write:

```
sudo mount -o remount,rw /path/to/mountpoint
```

You can then edit the file using whatever method you choose.
This.

It sounds as if there's a problem with how the disk or partition itself is mounted, and not a permission issue with root-owned files.

---

### Post by Dynamata on 2010-06-01
Thanks, "gksudo nautilus" worked! but when I tried it on another folder nothing happened until reboot, I'll try the command line method next. Still couldn't get Jack to run, I'm following YouTube tutorials here:

[http://www.youtube.com/watch?v=w2gPqH6kNJU&feature=related](http://www.youtube.com/watch?v=w2gPqH6kNJU&feature=related) :)

P.S I had Ubuntu installed on another PC, removed the HD & transferred it to the PC I'm currently using, would that cause a problem?

---

### Post by Dynamata on 2010-06-07
Jack worked intermittently after reboot, now after upgrading to 10.04 it seems to be working Ok. 8)

---

