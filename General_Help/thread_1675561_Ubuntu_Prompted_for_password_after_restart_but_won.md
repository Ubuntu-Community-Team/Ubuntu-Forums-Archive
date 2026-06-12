---
title: "Ubuntu Prompted for password after restart but won't log in with valid credentials"
date: 2011-01-25
forum: General Help
---

### Post by CrispCreations on 2011-01-25
Hi all,

I know, first post, apologies that it had to be with a problem, but anyway here goes....

I have Ubuntu 10.04 desktop installed (since release) and had it set up to auto login, however, after some updates, I needed to restart, and it's now prompting for a password. After choosing my username and entering the password, I'm instantly returned to the login prompt. 

There's no message about failed authentication, just dumped straight back to the prompt. Indeed, if I enter an invalid password, I do get a failed auth message. 

I'm currently on my laptop, and from here I can ssh to the box, and login with the same credentials which fail when sitting at the box and entering them. Unfortunately, I'm at a loss as to how to fix the problem though. 

Could anyone give me any pointers on how to rectify this please?

---

### Post by robert shearer on 2011-01-25
I guess you have checked all the obvious but doesn't hurt to repeat ??

Caps lock on ?
Try another key-board, preferably ps2 (eliminates flat batteries on wireless and usb port failures)
Reinstall gdm
```
sudo apt-get install gdm
```

---

### Post by CrispCreations on 2011-01-25
> **robert shearer said:**
> I guess you have checked all the obvious but doesn't hurt to repeat ??

Caps lock on ?
Try another key-board, preferably ps2 (eliminates flat batteries on wireless and usb port failures)
Reinstall gdm
```
sudo apt-get install gdm
```
Hi, thanks for the reply, 

keyboard is fine, was the first thing I checked, plugged it into the laptop I'm on and it's working. Went back to the problem box, did Ctrl-Alt-F2 and that gets me to terminal and I can log in with my username and password there too (if only it were that simple)

sudo apt-get install gdm tells me the package is up to date

Like I say, the box is set to autologin which it's done for the last 7 or 8 months without issue. It's suddenly decided to start prompting of its own accord, after a restart following some recent updates, and then refuses to login. The prompt disappears briefly, as if it's trying to login, and then reappears, with no error message that the authentication failed that you'd normally see for an incorrect password. 

Up until now, Ubuntu hasn't missed a beat, this is my first issue, and it's got me stumped. Searching the forums and Googling in general hasn't thrown up anything useful either.

---

### Post by CrispCreations on 2011-01-25
Ok, an update to this, after logging in at the terminal prompt I was able to type startx and was delivered straight into my desktop, so at least I have that back.

I still need to figure out the cause of the problem though, as I suspect I'll have the same problem at next restart (fortunately this box is on 24/7 so restarts only happen when absolutely necessary) 

Soooo, anyway, my question still stands, if anyone out there has any suggestions as to the cause, and a possible resolution, it would be much appreciated. 

Cheers

---

### Post by robert shearer on 2011-01-25
appears that the gdm configuration is borked.

You could try
```
sudo apt-get purge gdm
```
 which will remove gdm and its configuration then
```
sudo apt-get install gdm
```

Though this may lead to other problems if the purge wants to remove a lot of other files. 

[http://ubuntuforums.org/showthread.php?t=806566](http://ubuntuforums.org/showthread.php?t=806566)

---

### Post by CrispCreations on 2011-01-25
I'll do a backup right before I next have to restart and then give your suggestion a go if it happens again. 

Once again, thanks, much appreciated.

---

