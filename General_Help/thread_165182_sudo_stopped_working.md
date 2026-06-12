---
title: "sudo stopped working"
date: 2006-04-24
forum: General Help
---

### Post by lightningdb on 2006-04-24
Hi,  I did an update to my Ubuntu 5.10 machine a couple of days ago, and since then sudo isn't working.

I could see that the sudoers file had been modified around the time of the update.  I searched the forums, and read a suggestion of booting into recovery mode and using visudo to edit the /etc/sudoers back to its original state, which I've done, but to no avail.

Here is my most recent terminal output:
> 
dave@thunder:~$ ls -al /etc/sudoers
-r--r-----  1 root root 406 2006-04-24 18:38 /etc/sudoers
dave@thunder:~$ visudo
visudo: /etc/sudoers: Permission denied
dave@thunder:~$ sudo visudo
dave@thunder:~$


As you can see, sudo  maybe does something, because after using it to "cat" sudoers, I don't get a permission denied error... but I also don't see the contents of the file.  Same with requests for superuser passwords on the desktop -- they're not rejected, but the programs also don't load/work.

Any ideas?

Many thanks, 
dave

---

### Post by doozer on 2006-04-24
I had a similar problem. My problem was due to sudo wiping my own login environment variables so that the root user environment didn't "know" which X display to use. As a test, see if you can run "sudo env" - if so, look for the variables DISPLAY and XAUTHORITY and if they are not present, or are blank, that is likely to be your problem. I fixed the problem by adding the following to /etc/sudoers (via "visudo", run as root):

Defaults        env_keep = "DISPLAY XAUTHORITY"

Hope that helps.

---

### Post by lightningdb on 2006-04-24
[QUOTE=doozer]Defaults        env_keep = "DISPLAY XAUTHORITY"[/QUOTE]

Thanks doozer, a valiant effort, but still no good.  sudo works fine under recovery mode (as root), but doesn't work in a normal session (though as mentioned the password is accepted, but nothing happens after that).

Anyone with more thoughts?  Happy to investigate further myself as well, but not sure where to start (aside from searching forums and google, and reading my books, none of which have helped so far).

Cheers,
dave

---

### Post by lightningdb on 2006-04-24
This thread pointed me in the right direction: [http://ubuntuforums.org/showthread.php?t=77614]("http://ubuntuforums.org/showthread.php?t=77614")

Essentially, it turned out my user id had been removed from the admin group.  I rebooted into recovery mode and added my user to admin with:
> gpasswd -a dave admin

On reboot, sudo was back to normal...

Also, I learned a useful file to check is /var/log/auth.log -- it has error messages that help, but obviously I needed to be in recovery mode to have the permissions to view this.

Cheers,
dave

---

### Post by mjziegle on 2006-04-24
Check to see if your username is still in the admin group in /etc/groups

-Matt

---

### Post by nanotube on 2006-04-24
[QUOTE=mjziegle]Check to see if your username is still in the admin group in /etc/groups

-Matt[/QUOTE]
that's supposed to be /etc/group

---

