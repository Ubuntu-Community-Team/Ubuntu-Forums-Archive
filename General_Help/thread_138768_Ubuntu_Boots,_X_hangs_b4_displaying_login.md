---
title: "Ubuntu Boots, X hangs b4 displaying login"
date: 2006-03-02
forum: General Help
---

### Post by nic886 on 2006-03-02
i have installed Ubuntu 5.10 Breezy Badger and it boots fine until the moment of login screen comes, at which point X does not seem to start but when i go CTRL+ALT+F1 and login in CLI mode and type startx it says display already running on :0.0. Any suggestions would be appreciated as ubuntu sounds like a good distro :-k

---

### Post by Q4U on 2006-03-02
I am a bit of a noob, and use kubuntu rather than ubuntu, so I might be of limited help. However, I guess it is an X configuration problem.

Questions:

Are your monitor and video card recognised correctly (look at the output of: lspci run from the terminal)?

Can you please post the X configuration file output (cat /etc/X11/xorg.conf, but check, the name might be not perfectly correct), the X logs (tail /var/log/Xorg0.log) and the kernel logs (tail /var/log/kern.log)?

Was there any error message during the installation? Look at the various files in /var/log/installer - such as those called syslog, messages, and status - for signs of errors and misconfiguration.

As I said I might not be able to help but if you post this stuff someone with the right knowledge might be able/willing to help.

Q4U

---

### Post by BradChandler on 2006-03-02
What type of video card do you have? What does the screen look like when you say X does not start, do you ever see the X mouse cursor? I have a nvidia 7800 GT and X would not work until I installed the nvidia drivers and edited my X config file. It would get to the point where the kde login comes up, but wouldn't display right or let me log in. Starting up in "safe mode" or whatever it's called allowed me to install the drivers and get things working.

---

### Post by Q4U on 2006-03-02
My card works fine, thanks. Cool to see you got it working. :)

---

