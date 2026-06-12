---
title: "Grub Keeps halting boot"
date: 2009-11-12
forum: General Help
---

### Post by sccrstvn93 on 2009-11-12
The grub menu continues to appear when I boot regardless of the edits I make to the file /etc/default/grub. Grub has no timeout and waits until I click enter to select an os. And I am running update-grub after making the changes. I am using 9.10 with grub v2. When I first installed ubuntu, grub worked normally, the menu never appeared and it quietly booted into ubuntu, the only os on my computer. Any ideas on how to fix this?

---

### Post by sccrstvn93 on 2009-11-13
bump

---

### Post by dearingj on 2009-11-13
1) Just to be clear, are you using 'sudo' when you edit the file and when you run update-grub?

2) What lines exactly are you changing when you edit the file?

---

### Post by ranch hand on 2009-11-13
How about giving us something to work with here.

Like posting your /etc/default/grub file.

---

### Post by sccrstvn93 on 2009-11-16
Yes, I am using sudo. Here is my /etc/default/grub file:


```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by ranch hand on 2009-11-16
That really ought to be working.

I would;
```

sudo update-grub

```
and do it every time you boot up if it is not working.

That command is due to be phased out.  They left that as an option because it was used in grub-legacy.

So, you may want to try;
```

sudo grub-mkconfig

```
which is due to replace it when we get 1.97 (we are running 1,97beta4).

---

### Post by louieb on 2009-11-16
Just a wild guess. 

Check your keyboard. I have read that GRUB2 will display the menu if the left shift is press. And it will also display the menu if it can't tell if it can't find the state of the left shift key.  

Have not played with GRUB2 much - so I'll take it that as ranch hand says - the grub configuration is all right.

---

### Post by drs305 on 2009-11-16
As louieb suggested, the menu is designed to display for a depressed SHIFT key or if it can determine the status of the SHIFT key. It also will display a menu and await input if it cannot determine which menuentry to boot. Take a look at the terminal as update-grub runs and see if it detects any errors.

I have one system with only Ubuntu which originally had problems hiding the menu on boot. Although I no longer need this "hack", I added the following to the end of /etc/grub.d/00_header and it hid the menu (with GRUB_TIMEOUT and GRUB_HIDDEN_TIMEOUT both equal to 0 in /etc/default/grub).

> 
### BEGIN Hidden Menu Test ###
cat << EOF
if [ \${timeout} != -1 ]; then
if sleep --verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
set timeout=${GRUB_HIDDEN_TIMEOUT}
fi
fi
EOF
### END Hidden Menu Test ###

Run "sudo update-grub" after saving /etc/grub.d/00_header

---

### Post by sccrstvn93 on 2009-11-16
Thanks for the help. The problem remains when using: sudo grub-mkconfig

Editing the header file does not fix the problem. The computer is a laptop and the problem remains with or without an external keyboard attached. Any other ideas.

---

### Post by thebinaryman on 2009-11-27
Same problem here on my mother's machine.

Here's my story. Fresh 9.10 install. Everything wonderful. In an effort to optimize things, I held the shift key at boot to edit the boot line in grub2 to run a couple other parameters to accomplish a unrelated goal. Ever since holding the shift key at ONE boot, now the system waits at the menu every time, and NEVER auto boots anything. A enter-press is required each time to boot the system.

I've tried everything aforementioned in this thread, and have one morsel to add.

After doing what drs305 suggests (to no success), I used the "e" key to edit the boot line inside grub2. I changed the top option from a "1" to a "0", (sorry I forget what it's called and don't wish to reboot). This change granted me ONE successful restart as planned, but still no permanent fix as subsequent boots still stall at the menu.

What I'm getting at here, is that everything was wonderful, until using the SHIFT key ONCE. All boots afterward halt as if I'm holding the shift key. Tried re-installing grub, no success. This keyboard is fine too. It's as if pressing shift has triggered a permanent configuration change.

Would appreciate any suggestions. I've been googling the last two hours over this silly problem that has no apparent reason. If I have no solution by tomorrow or Sunday I'll probably re-install the OS and all software and files (a waste of my day), as I see no other option.

Thanks.

---

### Post by thebinaryman on 2009-11-27
FYI I reverted to an earlier version of grub per these instructions:

(number 11) [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

At least everything works expectedly, albeit with an old grub. Is there any reason I shouldn't run this older version of grub? Will it still update automatically when new kernels are installed via ubuntu updates? Thanks.

---

### Post by RishiRamraj on 2009-12-08
Same problem here. I was able to get around it with:
[http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg150065.html](http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg150065.html)

In summary, I added the following to /etc/grub.d/40_custom:
```

if [ ${recordfail} = 1 ]; then
  set timeout=3
else
  set timeout=0
fi

```Then I ran grub-mkconfig and checked /boot/grub/grub.cfg to make sure that the changes were written to disk and restarted.

My guess as to what's going on is that recordfail will be set to 1 when a problem is detected (like no keyboard). Grub then checks recordfail and halts the boot process regardless of the configurations you specify.

I tried commenting out this code from /etc/grub.d/00_header and it had no effect:
```

cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF

```

---

