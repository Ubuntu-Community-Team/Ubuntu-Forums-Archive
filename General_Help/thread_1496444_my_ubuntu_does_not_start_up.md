---
title: "my ubuntu does not start up"
date: 2010-05-29
forum: General Help
---

### Post by miromony on 2010-05-29
My ubuntu does not start up and give me a message contains the following options:

Run ubuntu in low graphical mode
Reconfigure graphics
Troubleshooting
Exite to login screen

and by default the first option is selected
I tried each but without result

How I could retrieve my ubuntu to work?

Thanks

---

### Post by DagMan on 2010-05-29
Hopefully this will do it:

Try hitting the key combo CTRL+ALT+F1 and getting to a text based login screen.
Type your username and password.
Type as follows and that's a capital X in the first line below this one.
[B]cd  /etc/X11
sudo mv  xorg.conf  xorg.conf-old[/b]
and reboot by typing this
**sudo reboot**

If that worked, then that's good, but you may want to start a thread on how to know if you need a graphics driver, and if so, which one do you install.  You can include a link to this thread.

If that didn't work, you can again press CTRl-ALT-F1 and type your username and password then
[B]cd  /etc/X11
sudo  mv  xorg.conf-old  xorg.conf[/B]
and you're right back where you started and you can come back for better advice.

---

### Post by miromony on 2010-05-30
> **DagMan said:**
> 
Try hitting the key combo CTRL+ALT+F1 and getting to a text based login screen.
Type your username and password.
Type as follows and that's a capital X in the first line below this one.
[B]cd  /etc/X11
sudo mv  xorg.conf  xorg.conf-old[/B]
and reboot by typing this
**sudo reboot**


I entered to a text based login screen by hitting F8 but not by "the key combo CTRL+ALT+F1"
I followed these instructions but it gets me the following message:
mv: cannot stat 'xorg.conf' : no such file or directory

 but the **X11** folder contains:
Xwrapper.config
XvMCConfig
xorg.conf.failsafe

---

