---
title: "Problem loading X interface"
date: 2006-05-14
forum: General Help
---

### Post by ozenmacher on 2006-05-14
Ok, so I just installed.  Now, as I am starting, it gives me an error saying something along the lines of "Error loading X interface".  It only lets me run in some text only interface now.  Can someone please help...
thanks.

---

### Post by Sutekh on 2006-05-15
What sort of video hardware do you have?

You should be able to get things running with the general fix-all **vesa** driver

Issue this command to setup the X Windows Server from the command line```
sudo dpkg-reconfigure xserver-xorg
``` - Input your apssword when prompted

 - You will be asked a long string of questions regarding your input devices; mouse/keyboard/monitor.  If you are unsure what to answer, just accept the default/suggested values.

 - the important step is when you are asked to choose the video card driver for the X server choose **vesa**

 - When the process is finished use this command to try to start the GUI again
```
sudo /etc/init.d/gdm restart
```

---

