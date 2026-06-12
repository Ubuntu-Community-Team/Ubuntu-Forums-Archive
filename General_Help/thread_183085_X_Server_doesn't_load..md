---
title: "X Server doesn't load."
date: 2006-05-27
forum: General Help
---

### Post by Feldoon on 2006-05-27
Right, I've configured my laptop so it dual boots with WinXP and Ubuntu. They both pick up fine.

However, when Ubuntu tries loading the GUI, there's apparently an X Server error and it fails to load the GUI.

My graphics card is (as far as I can work out) a "ATI RADEON XPRESS 200M Series" (can't find any more info than that).

I was just wondering what I'd have to do to configure Ubuntu so it loads the GUI correctly.

---

### Post by Feldoon on 2006-05-27
Anybody?

---

### Post by PriceChild on 2006-05-27
Have you ever been able to load up the ubuntu gui before?

---

### Post by Feldoon on 2006-05-27
Not on this laptop, no.

---

### Post by Sutekh on 2006-05-27
Unfortunately ATI cards, often are the cause of video problems.  The free 
(as in freedom) driver that Ubuntu uses, is often not up to the task.

When the error dumps you to a command line, log in with your usernam and password.

You can use this command to change the video drivers temporarily to the **vesa** drivers, which seem to be a general fix-all driver.
```
sudo dpkg-reconfigure xserver-xorg
``` - when prompted for a password, use your users password. 

- this command will reconfigure the X server (the GUI), you will be asked a long string of questions regarding the input devices of your laptop; your keyboard, mouse/touchpad and monitor. If you don't know what you should answer to these questions go with the default/suggested ones.
 
  - the important step is when you are asked to choose the video card driver for the X server choose **vesa**
 
  - once you are done use this command
 ```
sudo /etc/init.d/gdm restart
```  - this will restart the GNOME Display Manager, and start the GUI.



  If you get the graphical interface working with the **vesa** drivers, you could look into installing the Official ATI drivers, through one of these means.  
 
 You can try either this HOWTO
  
  [Ubuntu Document Storage Facility - Install ATI Driver]("http://doc.gwos.org/index.php/Install_ATI_driver")
  
 or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)
  
  [Ubuntu Forums - Easy Ubuntu v2.2]("http://ubuntuforums.org/showthread.php?t=64629")
 [URL="http://www.ubuntuforums.org/showthread.php?t=75074"]
[/URL]

---

