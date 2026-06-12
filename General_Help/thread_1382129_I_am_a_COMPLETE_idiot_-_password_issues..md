---
title: "I am a COMPLETE idiot - password issues."
date: 2010-01-15
forum: General Help
---

### Post by oclementine on 2010-01-15
Hi everyone,

I've been happily using Ubuntu for about a year now, and until just recently have never experienced any trouble.

I had changed an expired login password before, but this most recent time when I began getting prompts at login that my password would expire in X number of days, I put off doing it.  I put it off changing it until it was expired.  

I don't remember how the process went the first time I changed it, but I do know that it was an automatic prompt and was essentially fool-proof.  This time, however, I didn't get any such pop-up prompt.

I changed it with sudo pswd, and then set it so that I'd skip the login page. 

I remember (or rather, THINK I remember) what I set the password to being, but I have basically locked myself out.  I can access the desktop and internet and do everything I need to do for school, etc., so it's not an urgent crisis.  But I'm unable to get in and perform administrative tasks - can't update the system, get into Synaptic, etc.  

I've tried every password I've pretty much ever used in my entire life, and everything I could have feasibly chosen for a password.  It's all in vain.  I don't know what the EFF I entered when I changed it, but it's clearly not what I meant to enter.

What can I do?

---

### Post by deveric on 2010-01-15
sudo passwd resets the root password, not your user password. You should be able to log in as root with the password you set at sudo passwd. From the X login screen, you can do CTRL + ALT + F1 and log in as root, then once logged in, do passwd username, where the username is your normal log on. This will reset that password for your user. After, do ALT + F7 to go back to the X Logon screen

---

### Post by Cavsfan on 2010-01-15
you could enable SU and login that way to change your user password. 
Then disable SU (suggested)

sudo passwd root

Use at your own risk!

Re-disabling your root account

sudo usermod -p '!' root

---

### Post by d3v1150m471c on 2010-01-15
"4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot."

I really do hate making this more known than it is...but...i do hope this helps.

---

### Post by Cavsfan on 2010-01-15
After you have logged is as SU:
You should be able to go to System > Administration > User and groups
To change your regular login password.
If this works I would disable the SU account as I mentioned.

No one advocates logging in this way, but it looks like you have to to be able to set a new password for
yourself.

Hope this helps!

---

### Post by oclementine on 2010-01-27
Hey everyone, 

Used d3v11's instructions - worked!

Thanks very much!  

There was an issue while I was in the root shell though, it displayed the user as being root@(none), as in, at no location.  Honestly don't really know anything about this root shell business - I use the ordinary UNIX terminal and that's about as deep as I'm comfortable with right now.  Anyway, changed the password and had a hard time shutting down and rebooting.  It refused the connection, presumably because it didn't know which location I was at.  Fortunately I had someone to help me.  Went into kernel panic (presumably because of the location issue) and I damn near soiled myself.  Did a hard shut down and waited.  All was fine upon reboot.  WHEW.

---

### Post by Leppie on 2010-01-27
there are many tut's on the net with these instructions to reset a "lost" password...
using a search engine isn't really as hard as it seems...

---

### Post by Leppie on 2010-01-27
> **Cavsfan said:**
> you could enable SU and login that way to change your user password. 
Then disable SU (suggested)

sudo passwd root

Use at your own risk!

Re-disabling your root account

sudo usermod -p '!' root
it's a bit difficult to sudo when you've lost access or your password...

---

### Post by Cavsfan on 2010-02-02
> **Leppie said:**
> it's a bit difficult to sudo when you've lost access or your password...

Very true! I should have stayed out of this one...

---

