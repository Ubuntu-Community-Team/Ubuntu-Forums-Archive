---
title: "terrible pixely strip in xubuntu"
date: 2006-05-10
forum: General Help
---

### Post by tx360modena on 2006-05-10
i am a complete linux newbie and on my first attempt at installation, i got this major strip across my screen that makes xubuntu usage ridiculously irritating.  i've attached some photos..(sorry for the size)..what can i do to fix this?!!  i'm considering installing ubuntu instead of xubuntu but i'm not sure if this will help.....](*,)

---

### Post by Nano Geek on 2006-05-10
Why don't you try Ubuntu and tell us what happens; by the way: I think you can take a picture of the desktop by pressing **Print** on your keybord.

---

### Post by Sutekh on 2006-05-10
What video hardware do you have?  ATI/NVIDIA/On-baord?

Crazy artifacts like that (which are probably the craziest I have seen) are usually due to video support.  If we know your video hardware, we can probably fix the issue.

Xubuntu/Ubuntu/Kubuntu all the same in terms of hardware support.

---

### Post by tx360modena on 2006-05-10
ahhh....I completely forgot to mention that..i have an old compaq laptop with ATI mobility 128 AGP 2X.

---

### Post by Sutekh on 2006-05-10
Alright, here's what I think you should do.

You should try changing the video driver from the current one to the fix-all/generic driver, **vesa**


 - To do this use this command from a Terminal window (Applications -> Accessories)
```
sudo dpkg-reconfigure xserver-xorg
```
 - Use your password when prompted

- You will be asked a string of questions regarding the input devices (keyboard, mouse and monitor) on your PC.

- If you are unsure what to answer, just use the default/suggested options.

- When you get to the question about which driver you wish to use for the X Windows server. Choose **vesa**

 - When the reconfiguring is finished, press Alt + Ctrl + Backspace, to restart the GUI.  Hopefully it will get rid of that craziness.



 - Then if you wish, you can look into installing the proprietry ATI drivers for Linux.  You can try either this HOWTO

[Ubuntu Document Storage Facility - Install ATI Driver](http://doc.gwos.org/index.php/Install_ATI_driver)

or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)

[Ubuntu Forums - Easy Ubuntu v2.2](http://ubuntuforums.org/showthread.php?t=64629)

---

