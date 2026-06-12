---
title: "WHY sudo for shutdown"
date: 2010-06-29
forum: General Help
---

### Post by Esthellin on 2010-06-29
I don't care about all the different ways to make the shutdown command executable without using sudo.

I want to know WHY you need sudo in the first place. And also why a user can click on a gnome-panel icon marked 'Shutdown', and they don't have to put in sudo before the computer shuts down, but it requires sudo from a terminal.

---

### Post by Seanlol on 2010-06-29
"sudo" executes the following command as root.

The only user who can shut down a linux system is root. That's why the "sudo" is needed before the shutdown command. I assume that the shut down button simply executes the "sudo shutdown now" command.

---

### Post by Serpher on 2010-06-29
Shutting down is a task that requires root privileged for a good reason. It's been grandfathered down from when UNIX was pretty much just for servers and you didn't want any user remotely shutting down the server, however it holds value now if you have something like more than one user logged in and you don't want a user to be able to shut down your computer if you have the physical computer in a place where any user can't get to it.

Another reason why you have to have root access is shutting down your computer is actually just changing the runlevel init uses to 0, or 6 if you're restarting. init is the script that starts and stops services and processes etc etc. It's the first thing run when linux starts, and you wouldn't just want to let anybody be touching your runlevels allowing the whole system to go into single user mode where everybody is root and able to do everything. The shutdown command just basically calls the command init 0 or 6 and puts a timer on it. If you want to test this try typing 'sudo init 0'. By default you'll be on runlevel 5, and Ubuntu doesn't have 2-3 configured but it's not to hard to configure with the program 'chkconfig'.

---

### Post by Esthellin on 2010-07-03
Thanks for the replys.
That would make sense. You wouldn't want a user logging into the server via ssh then shutting down the server. A user doesn't shut down the computer when they have finished, they log out. Jus realised that :P.
And even though you can forward X to the server so you can use graphical programs, you can't access the shutdown button or panels.

It also makes sense why there doesn't exist a way to shutdown the compuer without administrator access. Although:

Isn't there a script that runs when you press the power button on the computer? I had a look in the acpi or proc folder, and I saw a few scripts that have to do with pressing different computer keys. I tried running these but they required sudo aswell. How could something require sudo if run directly, but pressing the physical button that calls the script doesn't require sudo?

---

### Post by Yarui on 2010-07-03
> **Seanlol said:**
> "sudo" executes the following command as root.

The only user who can shut down a linux system is root. That's why the "sudo" is needed before the shutdown command. I assume that the shut down button simply executes the "sudo shutdown now" command.
If that were the case you would have to type your password every time you shut down, the shutdown applet probably uses an entirely different method of shutting down.  I think the user has to be in a group that gives them the privelege of shutting down, but that may be only in specific distros.  Even if you are in that group, though, you can't execute reboot or shutdown in terminal for some reason.

---

### Post by The Cog on 2010-07-03
I'm pretty sure that only root can shut down the system.

As for the power button (or Ctrl-Alt-Delete in a tty), these are detected by the operating system, by processes running as root.

As for shutdown on the gnome menu, I _presume_ that a message is sent from the gui back to the gdm process. The gdm process is the one that runs as root, prompts for a login username and password and launches the desktop under the correct user-id. I presume that gdm sees the message from the user GUI and then does the shutdown.

---

### Post by Yarui on 2010-07-03
> **The Cog said:**
> I'm pretty sure that only root can shut down the system.

As for the power button (or Ctrl-Alt-Delete in a tty), these are detected by the operating system, by processes running as root.

As for shutdown on the gnome menu, I _presume_ that a message is sent from the gui back to the gdm process. The gdm process is the one that runs as root, prompts for a login username and password and launches the desktop under the correct user-id. I presume that gdm sees the message from the user GUI and then does the shutdown.
This sounds fairly believable.  Kind of along the same lines I was thinking, but with a little more thought put into it.

---

### Post by philinux on 2010-07-03
[http://old.nabble.com/how-can-non-admin-users-shutdown-from-CLI--td25674386.html](http://old.nabble.com/how-can-non-admin-users-shutdown-from-CLI--td25674386.html)

---

### Post by Yarui on 2010-07-03
> **philinux said:**
> [http://old.nabble.com/how-can-non-admin-users-shutdown-from-CLI--td25674386.html](http://old.nabble.com/how-can-non-admin-users-shutdown-from-CLI--td25674386.html)
Very interesting.  So it's a function that is specifically executed by gdm like Cog suggested.

---

### Post by khelben1979 on 2010-07-03
Does not **ctrl + alt + delete** reboot Ubuntu as well? On my Debian Lenny system I only need to press that and the system can reboot from a normal user.

---

### Post by CharlesA on 2010-07-03
Works on my server, but only if I am running at the console and not via ssh. :P

I don't use it often, since sudo reboot from ssh is quicker/cleaner.

---

### Post by Esthellin on 2010-07-04
Thankyou all for the replies. I have always wondered about this question, and it has finally been answered :D

---

