---
title: "Need Help With Sudo Commands!"
date: 2010-01-07
forum: General Help
---

### Post by reiss82 on 2010-01-07
I recently installed ubuntu 9.04 onto my ps3 and it created a main user called reiss, however if i try to access the root account it requires a password which i dont have, and anytime i use the 'sudo' commands it says im not in the sudoers file, can anyone help?

Edit: This is my first time with ubuntu so im not sure what to do :(

---

### Post by michy99 on 2010-01-08
What is the output of this command?```
groups
```

---

### Post by HiImTye on 2010-01-08
are you using the administrator account you set up during install?

if so, boot in recovery mode and make sure
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

is in the bottom of sudoers
```
/etc/sudoers
```

---

### Post by reiss82 on 2010-01-08
Well any command with sudo and it says something like reiss isnt in the sudoers file, itll be reported, its the first account set up, how do i boot into recovery mode?

---

### Post by undecim on 2010-01-08
to get to recovery mode, you need to reboot and hold the shift button until you see the grub menu. There will be an option to start ubuntu in recovery mode.

---

### Post by reiss82 on 2010-01-08
Ok hold it even past the kboot?

---

### Post by reiss82 on 2010-01-08
On my ps3 it starts up with just the kboot so im not sure when im meant to press it

---

### Post by HiImTye on 2010-01-08
when you choose to start ubuntu, hold shift (I believe you have to manually choose to load a third party OS, yes?)

---

### Post by reiss82 on 2010-01-08
Nope its set to load on startup, i tried holding shift as soon as it loads but it just gets to the kboot

---

### Post by HiImTye on 2010-01-08
when grub starts to load it will say something like 'press esc for boot menu'

press esc

---

### Post by reiss82 on 2010-01-08
I checked i dont get that, all i get it that screen with the 2 penguins, and then i press enter at kboot, and then it comes up some text and loads it up

---

### Post by reiss82 on 2010-01-08
Have you tried it on ps3 before?

---

### Post by HiImTye on 2010-01-08
never owned a ps3 and even if I were to buy one, the new batch no longer supports third party OSes

the fundamentals are generally the same, however, to the PC version

what text does it say?

---

### Post by reiss82 on 2010-01-08
On startup? Just says all the hardware that has been detected like usb mouse and stuff and comes up with the kboot, and says how to get back to the ps3 menu, isnt there a way to get onto recovery mode from when im logged into my account? Or from the live cd? I used the text based one

---

### Post by reiss82 on 2010-01-08
I tried even pressing Esc or Shift at this menu but it didnt do anything, so yeah im kinda stuck

---

### Post by HiImTye on 2010-01-08
[this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=1255598") should be able to help you, as the kboot site does not have any easy to read documentation (really, I was too lazy to download and ungz the file)

---

### Post by reiss82 on 2010-01-08
Lol thanks :) not like lazyness is a bad thing :P

---

### Post by HiImTye on 2010-01-08
no problem, hope it helps :)

---

### Post by michy99 on 2010-01-08
reboot and at the kboot screen type:```
sudo -i
```
this will start a root shell.(it will NOT prompt for a password)



remount the root ("/") partition as read/write:```
mount -o remount,rw /
```



add your user to the admin group```
adduser reiss admin
```


edit the sudoers file:```
EDITOR=nano sudo -E visudo
```


and make sure it looks like this:```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL
%admin ALL=(ALL) ALL
```

to save the file and exit press Ctrl+x, y, Enter.



and press Ctrl+Alt+Del to reboot.

---

### Post by reiss82 on 2010-01-08
Yay it worked :D ty for helping both of ya

---

