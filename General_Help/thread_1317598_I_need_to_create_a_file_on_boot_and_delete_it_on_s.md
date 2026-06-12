---
title: "I need to create a file on boot and delete it on shutdown"
date: 2009-11-06
forum: General Help
---

### Post by trpnblies7 on 2009-11-06
I need to create two scripts: one that creates a file with a line of text on boot *after* X starts, and one that deletes the file when I either log off, restart, or shutdown my computer.

I know the code to create the file is simple enough:

```
echo "Line of text" >> /folder/file
```

And to remove it I could use:

```
rm /folder/file
```

However, the folder that I need the file created in and deleted from is read-only, so the scripts need root permission. How would I go about creating these scripts so that they have root permission, and where would I place the one that runs on boot and the one that runs when I logoff, restart, or shutdown?

I'm still very new to scripting, so I'm having trouble with this. Thanks!

---

### Post by JillSwift on 2009-11-06
you can modify the script /etc/rc.local to call your script on boot-up. It's the last script run on boot.

For shutdown, place a link to your shutdown script in /etc/rc0.d/ name it K10[COLOR=Red]*whatever*[/COLOR] to make it run early on. (Replace "whatever" with a good memorable name).

Links in the rc0.d directory whose names start with "K" get followed and run on shutdown. the scripts are typically kept in the /etc/init.d/ directory. Good page on startup and shutdown scripts [here]("http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html").

---

### Post by undecim on 2009-11-06
There are scripts that are run every time the system changes run level. (this means starting up, turning off, reboot, going root-only mode, etc)

Any script in /etc/rcX.d/ will be run when run level X is entered.

the run levels are:

[LIST]
[*]0: Shut Down
[*]1: Single user (i.e. root only)
[*]2: Default Multi-user mode
[*]3-5: Same as 2
[*]6: Reboot
[/LIST]
So if you put your creation script in the /etc/rc2.d/ directory, it will run on boot

If you put your removal script in the rc0.d and rc6.d directories, it will run on shutdown and reboot.

---

### Post by trpnblies7 on 2009-11-06
Thank you! That worked perfectly!

---

