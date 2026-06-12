---
title: "How to modify GRUB"
date: 2009-08-09
forum: General Help
---

### Post by ronux on 2009-08-09
Hello,

I installed UNR on a Samsung NC10. 

I would like to modify the Grub file.
I was not able to find the usual menu.lst file in Boot | Grub folder.
Instead I found something similar. The file is called grub.cfg
I tried to edit it (sudo gedit /boot/grub and so on) but it is not letting me do so.

Is there anyone that could help me to figure out how to edit the grub file and which or where is the correct file to use?
My intention is to change the time (seconds countdown) and activate the boot splash in order to get the user and password request before getting into the system.
Thanks for your help.

R.

---

### Post by Nate Shoffner on 2009-08-09
What comes up when you type into the terminal:

sudo gedit /boot/grub/menu.lst

---

### Post by drs305 on 2009-08-09
Here is a link to a post I made called Grub 2 Basics. It describes the new way Grub works and how to modify it. 
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

Here is the Ubuntu wiki on Grub 2:
[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

Both have links to other Grub 2 resources.

Specifically to your post, timeout is located in /etc/default/grub. After making the change, you must run "sudo update-grub".

---

### Post by ronux on 2009-08-09
drs305 - thanks for this info.
Yes - I see the timeout setting.

And in order to activate the splash (user and password request) it seems that there are two lines.
GRUB_CMDLINE....."quiet splash" and I should modify it removing 'quiet'.

and for

GRUB_CMDLINE....."spalsh #GRUB_DISABLE_LINUX.....=true"

I should leave alone because it has to do with The Recovery mode.

Please advise.

Many thanks.

R.

---

### Post by ronux on 2009-08-09
Nothing, an empty page. See drs305 post. Thanks.

---

### Post by ronux on 2009-08-09
drs305 - I was able to edit the timing. Removing 'quiet' did not accomplish what I was looking for.

But in UNR where is the Login Window option (see System | Administration)?
Is it possible via UI or terminal to enable or disable the Automatic Login option?

Thanks.

R.

---

### Post by drs305 on 2009-08-09
> **ronux said:**
> drs305 - I was able to edit the timing. Removing 'quiet' did not accomplish what I was looking for.

But in UNR where is the Login Window option (see System | Administration)?
Is it possible via UI or terminal to enable or disable the Automatic Login option?


I'm away from my main computer and don't use UNR. In karmic, to enable/display the Login window, I had to edit  /etc/gdm/custom.conf.
```
gksudo gedit /etc/gdm/custom.conf
```
and add the following. Perhaps it is the same in UNR but I don't know. Change the settings as you desire to enable/disable autologin.
> 
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=[COLOR="DarkRed"]username[/COLOR]
TimedLoginEnable=true
TimedLogin=[COLOR="DarkRed"]username[/COLOR]
TimedLoginDelay=10


---

### Post by ronux on 2009-08-09
drs305 - **thanks** for the info again.
It worked :)
Edited true to false for each line and I get the Login screen on my UNR.
Wondering why they removed the Login window UI from the Admin list...

Best.

R.

---

