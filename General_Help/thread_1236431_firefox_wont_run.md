---
title: "firefox wont run?"
date: 2009-08-10
forum: General Help
---

### Post by Lord foff on 2009-08-10
I have no idea why, but my firefox web browser wont run. When i try to run it i get a message saying "Firefox is already running, but is not responding. To open a new window, you must first close the existing firefox process, or restart your system." 
I have tried restarting my system and that doesn't help and i havn't got a firefox running at all, help me please?

---

### Post by credobyte on 2009-08-10
In terminal:
```
mozilla-firefox
```

Show us what you get as an output ( errors? ).

---

### Post by Lord foff on 2009-08-10
I rebooted and it ran a routine check of /dev/sbd3.
"*file system check failed.                   [FAIL]
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the system manually.
*A  maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: command: command not found
bash: the: command not found
bash: dircolours: command not found
bash: command: command not found
bash: the: command not found
root@ben-desktop:~# " 

I imagine this isn't meant to happen... :S

---

### Post by credobyte on 2009-08-10
What does this command say ?
```
echo $PATH

```

---

### Post by Lord foff on 2009-08-10
/sbin:/bin
root@ben-desktop~#

---

### Post by credobyte on 2009-08-10
```
export PATH=$PATH:/bin:/usr/local/bin
```

Let us know if it helps.

---

### Post by Lord foff on 2009-08-10
Didn't do anything, just went to another command input.

root@ben-desktop~# export PATH=$PATH:/bin:/usr/local/bin
root@ben-desktop~#

---

### Post by credobyte on 2009-08-10
> **Lord foff said:**
> Didn't do anything, just went to another command input.

Restart PC and try running Firefox, etc. - previous command imported the two main directories where bash/shell commands are stored.

---

### Post by Lord foff on 2009-08-10
Rebooted, went to the exact same screen as in the previous posts. (post 3)

---

### Post by archanadevi on 2009-08-10
Hi,

I too got this problem. But if i close the existing firefox, i can open it. Again i wont get that error problem.

what version you are using?
[URL="http://www.pathwayhgv.co.uk"]
LGV Training[/URL]

---

### Post by Lord foff on 2009-08-10
Well, i'm on dual boot, and the options i get are:

Ubuntu 8.04.3 LTS, Kernel 2.6.24-16-generic
Ubuntu 8.04.3 LTS, Kernel 2.6.24-16-generic (recovery mode)
Other operating systems:
Microsoft Windows XP Home Edition

And it was the fact that i hadn't opened firefox previous to the error message.

---

### Post by Clownpie on 2009-08-10
It looks like your current problem has nothing to do with your Firefox problem.

For your current problem you should try:> fsck -r to try and repair your /dev/sbd3

If that works then once you are all booted I'd expect your Firefox problem to go away.  I believe the reason Firefox wouldn't open before is there was a lock on Firefox(for some reason).  The way you would have fixed this is to just remove the file ~/.mozilla/firefox/*.default/.parentlock

---

### Post by Lord foff on 2009-08-10
Took clownpie's advice, and it came up with:

fsck 1.40.8 (13-mar-2008)
e2fsck 1.40.8 (13-mar-2008
/dev/sbd1 is mounted.
WARNING!!!  Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.
Do you realy want to continue (y/n)?

Do i say yes?

---

### Post by Clownpie on 2009-08-10
Hrmm.  Well, I'm no expert on fsck, but you should for sure search the forums for this.  It is completely unrelated to your firefox problem.  Sorry I can't be of more help right now.

---

### Post by Lord foff on 2009-08-10
Thanks for trying anyway


What's the worst that can happen if i say yes , i have an instillation disk ...

---

### Post by Lord foff on 2009-08-10
/dev/sbd1: recovering journal
fsck.ext3:group descriptors look bad... trying backup blocks...
resize inode not valid. recreate<y>? yes

/dev/sdb1 was not cleanly unmounted, check forced.
pass 1: checking inodes blocks, and sizes
reserve inode 3 (<The ACL data anode>) Has invalid mode. clear<y>? yes

reserved inode 4 (<The ACL data inode>) has invalid mode. clear<y>? yes

reserved inode 6 (<The undelete directory inode>) has invalid mode. clear<y>? yes

Inode 8, i_blocks is 0, should be 262416. fix<y>? yes

reserved inode 9 (< reserved inode 9>) has invalid mode. clear<y>? yes

reserved inode 10 (<reserved inode 10>) has invalid mode. clear<y>? yes

deleted inode 100705 has zero dtime. fix<y>? yes.

(lots of text which scrolled too fast)

clone multiply-claimed blocks<y>? yes.
... to be honest, from here i just held the y button...

---

### Post by Lord foff on 2009-08-10
after it had "fixed" everyhting,

/dev/sdb1:  ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb1:  ***** REBOOT LINUX *****
root@ben-desktop:~# reboot

---

### Post by Lord foff on 2009-08-10
When i entered my username and password, a message popped up:

Your home directory is listed as: '/home/ben' But it does not appear to exist. Do you wish to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.

I clicked yes and got:

User's $home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $home directory must be owned by user and not writable by others.

I clicked ok and got:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions if you can fix this problem

I click on and it goes back to the login screen

Tried loging in with failsafe gnome, does the same thing pretty much, i shall just reinstall it... I'll keep you updated.

---

