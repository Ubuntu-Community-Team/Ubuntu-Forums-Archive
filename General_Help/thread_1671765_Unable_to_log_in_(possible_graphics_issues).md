---
title: "Unable to log in (possible graphics issues)"
date: 2011-01-20
forum: General Help
---

### Post by djhastings on 2011-01-20
When I start Ubuntu, it gets to the login screen just fine. After I enter my password, the desktop starts loading- I can see my email program starting- and then it jumps back to the login screen.

I have a fresh install of Ubuntu 10.10. Shortly after I installed it (about a week ago) I noticed this login problem, but whenever it occurred I was able to log in on the second or third try. Now I can't get in at all.

I can log in normally if I select Recovery Mode from the grub menu and then start in failsafe graphics mode, or if I select "safe mode" at the login screen. So I assume the problem is graphics-related, but (being fairly new to Linux) I don't know how to go about troubleshooting and fixing the problem.

Any help would be appreciated.

-DJ

---

### Post by djhastings on 2011-02-18
UPDATE: After booting into recovery mode and selecting failsafe graphics mode, a message pops up warning that Ubuntu is in low-graphics mode and then a list of options. Until today, I always chose the option to run in low-graphics mode for this session only. Today I tried the "reconfigure" option. I got another menu of options, but no matter which I select clicking "OK" doesn't seem to do anything.

---

### Post by sikander3786 on 2011-02-18
Welcome to the forums and sorry for the late reply :-)

We can try reconfiguring the graphics. Choose drop to root shell from recovery menu and then,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Note capital 'X' for X11.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

Let us know how that goes.

---

### Post by djhastings on 2011-02-18
Thanks for replying!

When I went to rename xorg.conf I discovered that there *was* no  xorg.conf file. There was an xorg.conf.failsafe, however. (Does this  mean I've never started Ubuntu in normal graphics mode? I thought I had,  but could be remembering wrong.)

I ran dpkg-reconfigure, but got no response, and the problem seems to be unchanged.


Incidentally, I was never asked for my password (either before going to root shell, or when using sudo). Is that normal?

---

### Post by VCoolio on 2011-02-18
> **djhastings said:**
> When I went to rename xorg.conf I discovered that there *was* no  xorg.conf file. There was an xorg.conf.failsafe, however. (Does this  mean I've never started Ubuntu in normal graphics mode? I thought I had,  but could be remembering wrong.)

I ran dpkg-reconfigure, but got no response, and the problem seems to be unchanged.


Incidentally, I was never asked for my password (either before going to root shell, or when using sudo). Is that normal?

There is no more xorg.conf by default; x does obey it though if you create it and add options. But xorg does most things automatically now.
Also the non-password thing is normal.

Try the normal boot, login, let it fail, then on login-screen hit ctrl+alt+f1 to drop to console, log in there (you won't see the password stars while you enter it), then run 'dmesg' to see some messages and run 'nano /var/run/Xorg.0.log' to read x log, see if this has something useful in it on why login failed. Also you can do 'sudo service gdm stop' to stop current x activity, then run 'startx' (it will probably fail again) and read the output (you may have to ctrl-alt-f1 again to get back to same console).

---

### Post by djhastings on 2011-03-17
> **VCoolio said:**
> Try the normal boot, login, let it fail, then on login-screen hit ctrl+alt+f1 to drop to console, log in there (you won't see the password stars while you enter it), then run 'dmesg' to see some messages and run 'nano /var/run/Xorg.0.log' to read x log, see if this has something useful in it on why login failed. Also you can do 'sudo service gdm stop' to stop current x activity, then run 'startx' (it will probably fail again) and read the output (you may have to ctrl-alt-f1 again to get back to same console).
Sorry for the delay in getting back on this. When I tried to do ctrl+alt+f1, instead of a console I got what looked like a corrupted version of my desktop screen. I tried logging in and typing commands blind, but it didn't seem to do anything. I could still use ctrl+alt+f7 to get back to the desktop, though.

On a hunch, I tried unplugging my KVM switch and plugging the monitor directly into the PC, and the problems disappeared. I've been planning to remove the Windows machine (and hence the need for a KVM switch) anyway, so this is an acceptable solution for now. :)

Thank you both for the help.

---

