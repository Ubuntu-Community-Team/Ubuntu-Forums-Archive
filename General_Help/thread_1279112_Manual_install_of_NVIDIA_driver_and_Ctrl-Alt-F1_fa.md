---
title: "Manual install of NVIDIA driver and Ctrl-Alt-F1 fails"
date: 2009-09-30
forum: General Help
---

### Post by Kdar on 2009-09-30
Hello.
I am using Ubuntu 9.04 and want to install newest NVIDIA driver, 185.18.xx

However, when I trying to exit X, by clicking Ctrl-Alt-F1 I just see a black screen (No console line, nothing at all, almost like monitor is off). When I click Ctrl-Alt-F7, it returns me successully back to X session.

I also tried other Ctrl-Alt-F2-6 and none of them worked.

What can I do? How can I fix it?
PS. I am using MSI GX620 (laptop).

---

### Post by karlson on 2009-09-30
> **Kdar said:**
> Hello.
I am using Ubuntu 9.04 and want to install newest NVIDIA driver, 185.18.xx

However, when I trying to exit X, by clicking Ctrl-Alt-F1 I just see a black screen (No console line, nothing at all, almost like monitor is off). When I click Ctrl-Alt-F7, it returns me successully back to X session.

I also tried other Ctrl-Alt-F2-6 and none of them worked.

What can I do? How can I fix it?
PS. I am using MSI GX620 (laptop).

If you are booting straight into X get a shell and do /etc/init.d/gdm stop or if using KDE /etc/init.d/kdm stop.

If you can't get a shell reboot get a grub prompt and boot into single user mode.

---

### Post by Kdar on 2009-09-30
I can't go to console mode by Ctrl-Alt-F1-6.

How would I do it at grub? By booting in recovery mode or?

And does anyone know why I get black, black screen when I try to go to Ctrl-Alt-F1 or 2 or 3.... or 6?
It always worked for me before (well, not on this computer, this is new).

---

### Post by karlson on 2009-09-30
> **Kdar said:**
> I can't go to console mode by Ctrl-Alt-F1-6.

How would I do it at grub? By booting in recovery mode or?

And does anyone know why I get black, black screen when I try to go to Ctrl-Alt-F1 or 2 or 3.... or 6?
It always worked for me before (well, not on this computer, this is new).

Why would you need to go to console to open a shell?  You can do it from X.

From Grub you can simple boot into a single user mode.

---

### Post by Giblet5 on 2009-09-30
What's in your /etc/event.d/tty1 file?

Mine: ```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1
```

---

### Post by Kdar on 2009-09-30
Mine is same like yours.

Also, I tried to install Nvidia driver using recovery mode and it told me to better do it from tty3 (run level 3) not tty1.

And what is single mode? Is it same like recovery mode?

---

### Post by Giblet5 on 2009-09-30
> **Kdar said:**
> Mine is same like yours.

Also, I tried to install Nvidia driver using recovery mode and it told me to better do it from tty3 (run level 3) not tty1.

And what is single mode? Is it same like recovery mode?

"tty3" is not synonymous with "run level 3", tty3 is the third console (Ctrl-Alt-F3, when that actually works).

Single-user mode (accessible from Recovery Mode) is run-level 1.

You can change run levels from any shell via ```
sudo telinit 1
``` but I DO NOT RECOMMEND YOU TRY because the text console clearly isn't working.

What's the output of this: ```
ps -ef | grep getty
```

---

### Post by Kdar on 2009-09-30
Sorry, it probably was Run Level 3.

Here is my output:
```
root      2381     1  0 14:41 tty4     00:00:00 /sbin/getty 38400 tty4
root      2382     1  0 14:41 tty5     00:00:00 /sbin/getty 38400 tty5
root      2389     1  0 14:41 tty2     00:00:00 /sbin/getty 38400 tty2
root      2390     1  0 14:41 tty3     00:00:00 /sbin/getty 38400 tty3
root      2391     1  0 14:41 tty6     00:00:00 /sbin/getty 38400 tty6
root      3265     1  0 14:41 tty1     00:00:00 /sbin/getty 38400 tty1
armen     5070  5042  0 14:45 pts/0    00:00:00 grep getty

```

---

### Post by Giblet5 on 2009-09-30
You should definitely have a text console then...

At the risk of asking you to repeat yourself, did this start happening immediately after you manually installed the nvidia driver? Could it have been doing this already and you only noticed it after the manual install?

What happens if you hit Ctrl-Alt-F1, then blind type in your user name, hit enter, type in your password, then hit enter, then type
```
echo > well_that_worked
``` and then flip back to the gui and look for that file?

---

### Post by Kdar on 2009-09-30
thank you for your help!

I did what you asked me. I clicked Ctrl-Alt-F1 (and actually F4 as well) and when I typed my ID and password and later that echo command. Then I went back to Ctrl-Alt-F7, I saw that it created a empty file in my home directory (named "well_that_worked").

This is new computer, new laptop, so I never had to use anything like this before.

---

### Post by Kdar on 2009-09-30
I just noted something interesting.

I tried to disable my Nvidia driver from "Hardware Devices" and then rebooted.

After it finished rebooting, I clicked Ctrl-Alt-F1 and it worked!!! But.
Every 2-4 seconds I get this error message:
```
end-request: I/O error, dev sr0, sector 0
Buffer I/O error on device sr0, logical block 0
Buffer I/O error on device sr0, logical block 1
```

---

### Post by Giblet5 on 2009-09-30
Cool! I suspect that something is wrong with the "console-setup" package, the console fonts it provides or the console mapping.

You might be able to fix it all with ```
sudo dpkg-reconfigure console-setup
```

(requires reboot...)

---

### Post by Giblet5 on 2009-09-30
> **Kdar said:**
> I just noted something interesting.

I tried to disable my Nvidia driver from "Hardware Devices" and then rebooted.

After it finished rebooting, I clicked Ctrl-Alt-F1 and it worked!!! But.
Every 2-4 seconds I get this error message:
```
end-request: I/O error, dev sr0, sector 0
Buffer I/O error on device sr0, logical block 0
Buffer I/O error on device sr0, logical block 1
```


For future painlessness, you don't have to reboot to change nvidia driver stuff...

```
sudo /etc/init.d/gdm restart
```

is all you need.

The Buffer I/O error is probably just a bad/blank CD in the first optical drive and it's unrelated to this.

---

### Post by Kdar on 2009-09-30
I was able to install newest Nvidia drivers and now I can go to Ctrl-Alt-F1-6 without any problems.

Thank you for all your help!

---

### Post by Giblet5 on 2009-09-30
"Excellent!"
-Mr. Burns

---

### Post by Giblet5 on 2009-09-30
Marked fixed. Or tried to...

---

