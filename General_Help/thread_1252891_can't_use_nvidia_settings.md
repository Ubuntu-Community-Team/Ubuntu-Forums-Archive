---
title: "can't use nvidia settings"
date: 2009-08-29
forum: General Help
---

### Post by timayyy on 2009-08-29
I am trying to adjust my screen resolution but when i go into nvidia x-server settings I get a message like this:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I cannot figure it out. I have uninstalled the drivers and reinstalled (#173) but still nothing. my system will only run in low graphics mode. BTW I have NVIDIA fx5200 graphics card (AGP) on an HP Pavillion 750n system.

---

### Post by argos3016 on 2009-08-29
I was solved this type of problem at "bruteforce" mode, making another session. Don't do anything but I only have this idea.

---

### Post by Nero147 on 2009-08-29
did you try running 
sudo nvidia-xconfig 
from the terminal? That should set your nvidia driver in your xorg.conf

---

### Post by scouser73 on 2009-08-29
You need to access the nVidia settings as root, go to **Terminal** then copy and paste this command:  **gksudo nvidia-settings**

---

### Post by timayyy on 2009-08-29
no change, maybe I'm not restarting the server correctly. whats the best way to restart the x server?

---

### Post by bodhi.zazen on 2009-08-29
> **timayyy said:**
> no change, maybe I'm not restarting the server correctly. whats the best way to restart the x server?

Log out and back in.

If that error message persists, are you running the nvidia driver ? Which one and how did you install it ?

---

### Post by themusicalduck on 2009-08-29
Press ctrl+alt+f1.

Log in, and then type in ```
sudo /etc/init.d/gdm restart
```

EDIT: bodhi beat me to it xD

---

### Post by timayyy on 2009-08-29
it say the driver is installed. I installed driver 173.14.16 using ENVYNG.

---

### Post by timayyy on 2009-08-29
ok, so I ran this cmd:

                
             envyng --uninstall-all

rebooted. dialogue box came up that said there was already an x-server running on display 0.would you like to choose another display(or something like that) click yes and it boots to desktop in low graphics mode.

 So how is it that another server is running???

---

### Post by ibuclaw on 2009-08-29
```
grep "nv" /etc/X11/xorg.conf
```
If that outputs something, run:
```
sudo nvidia-bug-report.sh
```
And post the generated file in your next post.

Else, run the following:
```
sudo nvidia-xconfig
```
and reboot.

edit: hmm, you've already made a post update... You could probably ignore this then.

Regards
Iain

---

### Post by timayyy on 2009-08-29
here is the bug report......

Edit bodhi.zazen :

YIKES, that is way too much information to post as text.

Please save the information as a text file, say nvidia_error.txt and post it an attachment.

---

### Post by timayyy on 2009-08-29
it's too big to post as an attachment. is there a way to shrink it down?

---

### Post by bodhi.zazen on 2009-08-29
That is a lot of text =)

Break it up manually, cut and paste.

---

