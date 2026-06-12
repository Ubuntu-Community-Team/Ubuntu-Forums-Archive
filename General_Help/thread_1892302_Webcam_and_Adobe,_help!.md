---
title: "Webcam and Adobe, help!"
date: 2011-12-07
forum: General Help
---

### Post by atticadayz on 2011-12-07
I just bought a logitech webcam and I want to use it to stream video using a site which uses Adobe Flash. The problem is that I have a built in camera that turns on fine when i choose to stream but for the love of mercy I don't want to use that cam! Yet I can't click the settings to choose my new and better cam and I can't figure a way to disable the built in cam. I have also thought that maybe making my logitech the default cam would work but i can't find anything on that.
I am so desperate and so stressed, is there away way to fix this situation?

---

### Post by deonis on 2011-12-07
Does your external webcam actually work? Try to check this in gstreamer-properties via terminal...

---

### Post by atticadayz on 2011-12-07
Both of my webcams work. I can use Cheese and all but I just can't change from the internal cam to the external.

---

### Post by deonis on 2011-12-07
[FONT=Comic Sans MS][SIZE=2]Good!! Run "gstreamer-properties" in terminal. Go to video devices... choose your webcam from the list and close the gstreamer window. Now try to do what  you  were doing before. It should work...
 But if you want to block your device completely you'll have to add its driver to the blacklist (/etc/modprobe.d/blacklis[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]t.conf) "blacklist mywebcam" [/SIZE][/FONT]

---

### Post by atticadayz on 2011-12-07
I changed the default and I hoped it would work but Adobe flash still plays my internal cam. I tried to blacklist it but it says permission denied when I entered the code.

---

### Post by atticadayz on 2011-12-07
I forgot to mention that I'm using chrome, the host site uses adobe.

---

### Post by deonis on 2011-12-08
Your device has to have the name "uvcvideo" check this out by running lsmod in terminal. To blacklist your driver type the following in terminal:
sudo gedit /etc/modprobe.d/blacklist.conf

then add "blacklist uvcvideo" to it, save the file and reboot the computer...

cheers

denis

---

### Post by atticadayz on 2011-12-08
I did blacklist it but none the less adobe still uses it just fine. Strangely, my internal cam is called HP webcam and my external is uvcvideo... I'm still hoping to find a way to use my new camera and any more help would be greatly appreciated. 
My greatest problem is that I can't switch cameras because adobe flash is unclickable, all I want is to switch cams.

---

### Post by deonis on 2011-12-08
There is another way to remove your hardware is to use rmmod function in terminal. It works the same way as blacklist. So, just type sudo rmmod (your HP Cam here). Make sure that you're disabling the right module !!! Use lspci -k to know this for sure !!! Or you might kill something very important.

---

### Post by deonis on 2011-12-08
Another way is to disable it in BIOS

---

