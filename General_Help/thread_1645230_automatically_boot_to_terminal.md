---
title: "automatically boot to terminal?"
date: 2010-12-14
forum: General Help
---

### Post by xeemo on 2010-12-14
Is there a way to bypass the log-in screen completely and just have it load to a terminal where you type "startx" to get to gnome?  I noticed you can start it with recovery mode and do that, but I just want this to be automatic.  I press power, and I want it to load to a terminal log-in.

---

### Post by Mosabama on 2010-12-14
Recovery mode is a single user mode. you wanna do that only if you have something to fix.

you can do that by changing the default run level. the default is 2 in ubuntu which is mutli user and GUI.

you can change it in /etc/init/rc-sysinit.conf
Change: env DEFAULT_RUNLEVEL value

---

### Post by QLee on 2010-12-14
> **xeemo said:**
> Is there a way to bypass the log-in screen completely and just have it load to a terminal where you type "startx" to get to gnome?  I noticed you can start it with recovery mode and do that, but I just want this to be automatic.  I press power, and I want it to load to a terminal log-in.

Have you tried removing GDM, GNOME Display Manager? I don't expect your system would start X without some display manager involved. You'll likely have to find some way to start gnome-session too, but you'll probably be able to figure that out.

---

### Post by xeemo on 2010-12-14
I ended up changing the grub settings to soft login - text, or somethingerother in the grub config.  I got the log-in I want, but the keyring is locked by default, instead of unlocked by logging in.  If someone has some input that'd be cool.

As for changing the default run-level what number would I change it to?  1?

---

### Post by sohail_linux on 2010-12-14
yes , as said above you only need to change your run lever, there are about 5-6 run levels ,e.g single usr , multi usr ,gui , txt etc , but their respective constants are changing from distribution to distribution. You can either googled the correct no for text mode or there will be already a no in comments.

---

### Post by Mosabama on 2010-12-14
as /etc/rcS.d "README" file says:

```

The scripts in this directory whose names begin with an 'S' are
executed once when booting the system, even when booting directly into
single user mode.

The scripts are all symbolic links whose targets are located in
/etc/init.d/ .

To disable a script in this directory, rename it so that it begins
with a 'K' and run 'update-rc.d script defaults' to update the order
using the script dependencies.

For more information see /etc/init.d/README.

```


so in /etc/rcS.d directory change the file name S70x11-common
to K70x11-common.
and in terminal type: update-rc.d script defaults


its actually weired that all the files in the rc "runlevel" directories are identical except runlevel 1 and 6 which is shutdown. all the others are the same, I guess the user has the option to define the run levels him self as it doesn't come in defaults as other distros.

---

### Post by Mosabama on 2010-12-14
damn I tried that and it didnt work!!!

it must be something with the Upstart thing that I cant understand.

I even REMOVED the files from the RC directories and it runs like if nothing happened !!

---

### Post by karthick87 on 2010-12-14
1. If you want to boot into text mode,then edit

```
sudo gedit /etc/default/grub
```

2. Then locate the line that states: **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**

3. Change this line to read **GRUB_CMDLINE_LINUX_DEFAULT="quiet text"**, save your changes and exit.

---

