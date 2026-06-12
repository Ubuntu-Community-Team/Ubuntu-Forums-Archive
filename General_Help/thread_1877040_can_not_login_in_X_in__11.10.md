---
title: "can not login in X in  11.10"
date: 2011-11-07
forum: General Help
---

### Post by ansiktsburk on 2011-11-07
I've installed a fresh 11.10 (I'm re-using my /home partition though) but something is seriously broken.
I try to log in in X (it works to login in the console, CTRL+ALT+F1) but I'm imediatly thrown out (it switches to the console and writes some gibberish, and then back to X)

I give the command (sorry for translations)
# jockey-text --list

xorg:fglrx_updates - ATI/AMDs proprietary driver FGLRX (updates after release (Proprietary, Inactivated, Not used)
xorg:fglrx - Proprietary  FGLRX-driver för ATI/AMD (Proprietary, Inactivated, Not used)

# lspci 
1:00.0 VGA compatible controller: ATI Technologies Inc Device 95c2

I really do not know what to do to try to make it more stable. Any suggestions? 

It has been very buggy but I THINK I have tried the binary drivers (enabled with jockey-text -e ) and at one time I managed to login, but was kicked out at a random moment, and then it kept failing when logging in.

---

### Post by BillyBoa on 2011-11-07
The truth is when you install a new OS (11.10 finally is significantly different from 11.04) is better to make a _fresh _install, means format /home as well.

---

### Post by ansiktsburk on 2011-11-07
> **BillyBoa said:**
> The truth is when you install a new OS (11.10 finally is significantly different from 11.04) is better to make a _fresh _install, means format /home as well.

When I first started to use *nix I was very happy with the fact that you could save /home from version to version.

But anyway, why would that matter now? / partition is wiped and I fail to login to X? Do I have some kind of X config file that makes things break? As I've said, I've managed to login once, and was able to start firefox, etc, and then later on got kicked out!

Any ideas on how to debug?

---

### Post by ansiktsburk on 2011-11-07
In Xorg.0.log I see


[  2812.256] 
Backtrace:
[  2812.257] 0: /usr/bin/X (xorg_backtrace+0x26) [0x460566]
[  2812.257] 1: /usr/bin/X (0x400000+0x64b7a) [0x464b7a]
[  2812.257] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f38fa0d1000+0x10060) [0x7f38fa0e1060]
[  2812.257] 3: /lib/x86_64-linux-gnu/libc.so.6 (__select+0x13) [0x7f38f90c68f3]
[  2812.257] 4: /usr/bin/X (WaitForSomething+0x19b) [0x45dffb]
[  2812.257] 5: /usr/bin/X (0x400000+0x2f912) [0x42f912]
[  2812.257] 6: /usr/bin/X (0x400000+0x232fe) [0x4232fe]
[  2812.257] 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f38f900d30d]
[  2812.257] 8: /usr/bin/X (0x400000+0x235ed) [0x4235ed]
[  2812.257] 
Caught signal 3 (Quit). Server aborting
[  2812.257] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  2812.257] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2812.257] 
[  2812.296] (II) Power Button: Close
[  2812.296] (II) UnloadModule: "evdev"
[  2812.296] (II) Unloading evdev

and it seems that is running the fglrx module. What??? I thought I disabled that.

Now I'm really confused. Any ideas?

---

### Post by 3rdalbum on 2011-11-07
> **BillyBoa said:**
> The truth is when you install a new OS (11.10 finally is significantly different from 11.04) is better to make a _fresh _install, means format /home as well.

It's really not true, and I suspect it's got nothing to do with the OP's problem.

@ansik: You can get to the login screen, right? What happens if you click on the little cog next to your username and choose "Unity 2D" as the session? Can you log in now?

Some other things to try: Add a new user account, see if you can log in with that. Also, if you're unsure whether fglrx is actually running or not, just try blacklisting it; add the line

```
blacklist fglrx
```

to the bottom of the /etc/modprobe.d/blacklist.conf file.

---

### Post by ansiktsburk on 2011-11-07
> **3rdalbum said:**
> It's really not true, and I suspect it's got nothing to do with the OP's problem.

@ansik: You can get to the login screen, right? What happens if you click on the little cog next to your username and choose "Unity 2D" as the session? Can you log in now?

Some other things to try: Add a new user account, see if you can log in with that. Also, if you're unsure whether fglrx is actually running or not, just try blacklisting it; add the line

```
blacklist fglrx
```to the bottom of the /etc/modprobe.d/blacklist.conf file.

THank you for your suggestions.
I've tried Unity 2D with the same result. No login. Screen switches to console, print a little gibberish, returns to X.

No success with other user account. 

Tried to blacklist module but gets this (after reboot)

# tail -n1  /etc/modprobe.d/blacklist.conf ; lsmod |grep fglrx
blacklist fglrx
fglrx                2929009  40

What???
I'm amazed... and it still don't work.

---

### Post by ansiktsburk on 2011-11-08
I have rebooted and it still seems to me that X is crashing, or something. Any ideas on what to  try next?

---

### Post by Orange_and_Green on 2011-11-08
Hi everyone,

this happened to me as well the first time I tried to upgrade to oneiric and keep my home folder as I had always been doing in the past. My "workaround" was to press ctrl+alt+f1 at the login screen, login in text mode, rename my home folder, e.g:

```
sudo mv /home/orange /home/orange_backup
```

(of course, replace "orange" with your username)

then reinstall, thus having the installer recreate a working /home/orange folder, and then manually copy all my important data from the backup folder to the new main one (taking care not to copy any hidden files except for those that I need for my program settings, such as ~/.mozilla-thunderbird)


Btw, after all of this I created a backup copy of all said hidden files to restore my desktop as I broke unity (and other stuff) several times while fiddling around in ccsm

Hope this helps :)


Edit: also have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1859528") (particularly page 2 and 3)

---

### Post by ansiktsburk on 2011-11-08
Thanks for your suggestion. but unfortunatly it does not help to use a new fresh homedir.
Also, I can't find any particular posting in the thread that could help me.

---

### Post by ansiktsburk on 2011-11-09
Now I found this in lightdm/x-0.log

```
==> lightdm/x-0.log <==
(EE) Failed to load module "fglrx" (module does not exist, 0)
(II) [KMS] Kernel modesetting enabled.
```

What? Why is it trying to load that? I thought I've removed the binary driver.
Any ideas on how to make it use the open source driver?

---

