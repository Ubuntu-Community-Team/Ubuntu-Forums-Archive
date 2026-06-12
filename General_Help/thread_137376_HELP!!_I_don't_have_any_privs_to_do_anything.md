---
title: "HELP!! I don't have any privs to do anything"
date: 2006-02-27
forum: General Help
---

### Post by kayakrob on 2006-02-27
Hi, I'm an extreme nubie to both UBUNTU and Linux. I've managed to successfully install a dual boot system. I can log in and browse the web with firefox, play some of the games, change my background image etc, but I can't perform ANY administration tasks. I cannot run the update manager from the upper right hand corner of the screen. It tells me there are 52 updates. I click it, am asked for my pw, but nothing happens. I cannot run synaptic from the system menu either.
I cannot run the user group manager. I've tried to sudo from a terminal window, but still nothing. I cannot access the login screen setup.

I looked at the system logs and see 
localhost sudo rob : command not allowed ; TTY=unknown ; PWD=/home/rob ; USER=root ; COMMAND=validate

but, I can su to root from a command line. 

Am I missing something here?
Thanks,
Rob:-k

---

### Post by aysiu on 2006-02-27
[QUOTE=kayakrob]I've tried to sudo from a terminal window, but still nothing.[/QUOTE] When you say "nothing," do you mean it looks like this?

```
rob@ubuntu:~$ sudo apt-get update
rob@ubuntu:~$
```

---

### Post by kayakrob on 2006-02-27
It looks like this:
rob@ubuntu-linux:~$ sudo apt-get update
Password:
rob@ubuntu-linux:~$

---

### Post by taurus on 2006-02-27
Did you enter a password, the same one that you use to log into your account?

---

### Post by Kevinator on 2006-02-27
Also, are you logging in with the same account that you created during installation?

---

### Post by benblur4 on 2006-02-27
just type the password that you made during installation.
Also. sometimes it apears that you are not typing but you realy are.
Instead of showing "XXXXX" when you type the password it just shows "     " (nothing).

---

### Post by aysiu on 2006-02-27
I had this happen to me a few days ago when I was trying to help someone out and I was playing around with adding and deleting users from the command-line. I don't know what I did, but it ended up like what's happening to you.

If I tried to launch a graphical root app, it would say "su cannot be launched," and if I tried to sudo anything, it would just bump to the next line in the terminal.

I checked the /etc/sudoers file, and it was fine and had the correct permissions. When I tried to boot into recovery mode, it prompted me for a root password even though I didn't have one.

Eventually I reinstalled. The last time I play around with the command-line and *adduser*.

---

### Post by kayakrob on 2006-02-27
Yes I am entering the same password for the user I created (user rob, not root).
This is in fact the second time I installed. I had the same problem on my initial install, and thought that I must have done something wrong, but, it is still happening.

Rob

---

### Post by kayakrob on 2006-02-28
Anyone?

---

### Post by mackinax on 2006-02-28
When I installed it didn't add my user name into the sudoers file (nor to the sudo group). I had to boot in recovery mode (to login as root) and add my username entry using "visudo".

[sudoers manual]("http://www.courtesan.com/sudo/man/sudoers.html")

---

### Post by nobar on 2006-02-28
The symptoms that you are describing sound like they might be related to a common problem that people have when installing in "expert mode" (although I noticed that you claimed to be a "extreme newbie").  For some reason, when installing in expert mode, sudo doesn't always end up working as expected.  This affects all the graphical password requests as well.  I think that this should be classified as a bug.

Note: Ubuntu is designed to not require an active root acount -- all administration can be performed by the primary user using sudo or graphical sudo.  That fact that you were able to "su to root" makes me think that you have configured a root user, probably through the "expert mode" installation.

Here are two similar threads:
   [http://ubuntuforums.org/archive/index.php/t-75324.html](http://ubuntuforums.org/archive/index.php/t-75324.html)
   [http://www.ubuntuforums.org/showthread.php?t=77614](http://www.ubuntuforums.org/showthread.php?t=77614)

---

### Post by timczer on 2006-02-28
Is sudo not working at all?  Or is it just the menu items that need root privileges?  I had just recently installed dapper on an old laptop and that problem, and needed to install gksu.

---

### Post by tinker312 on 2006-02-28
Hi,

Perhaps open up Synaptic and make sure sudo is installed. If it is, then reinstall it. 

Yours . . . 
John

---

### Post by kayakrob on 2006-03-02
:D Thank you all. I did in fact use expert mode, so that I could keep my windows installation. I was told that the default mode would wipe out windows. I did create a root user. I checked the sudoers file and my default user was not listed. I added it and presto, admin functions started to work. Now to the fun part. Time to learn linux.
Thanks,
Rob\\:D/

---

