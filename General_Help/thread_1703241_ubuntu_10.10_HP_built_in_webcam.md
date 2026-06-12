---
title: "ubuntu 10.10 HP built in webcam"
date: 2011-03-09
forum: General Help
---

### Post by sanad1995 on 2011-03-09
Hey guys, my built in webcam isnt functioning properly anymore. It was working before :( 

im using ubuntu 10.10 
laptop: HP Pavillion dv9000
Status: IM dessppeerraattee lol 

Any help would be appreciated :]

THANKS!!
-Sanad1995):P

---

### Post by sanad1995 on 2011-03-09
Bump ;[?

---

### Post by no2498 on 2011-03-10
open a terminal type gstreamer-properties click enter
click video try v4l and v4l2
click the bottom test button for each 1

i hope it come on

install xawtv from your package manager
i loads a cam grabber
try the cam in xawtv

---

### Post by beatskobe on 2011-03-10
[http://www.dreamteammoney.com/index.php?showtopic=118457&st=0&gopid=1721191&#entry1721191](http://www.dreamteammoney.com/index.php?showtopic=118457&st=0&gopid=1721191&#entry1721191)

---

### Post by sanad1995 on 2011-03-11
Thanks for the help, but it isn't working D:! Is it a hardware issue?

---

### Post by coldraven on 2011-03-11
My friends webcam on a new Asus laptop was so dark it looked like it wasn't working in Skype.
I installed guvcview from the Software Centre adjusted the brightness, quit guvcview and now Skype is OK. Make sure no other program is trying to use the webcam when you run guvcview.
Give it a try and let us know if it helped.

---

### Post by sanad1995 on 2011-03-13
Hey guys, just wanted to thank you for giving your time to help me out. Greatly appreciated :] 

I installed  guvcview and when I tried to open it, a pop up opened saying..

 guvcview error:
unable to open device

Please make sure the camera is connected
and that the correct driver is installed. 
D:!

---

### Post by no2498 on 2011-03-13
check with the maker of the computer to see if you need to press any keys to turn the cam on
some lap tops need to push the fn+f2 at the same time

---

### Post by sanad1995 on 2011-03-14
yeah, i just searched for an hour or so and haven't found anything :/ My web cam was working then stopped. So i restored my computer and it still doesnt work :/ Thanks tho!

---

### Post by sanad1995 on 2011-03-14
Is the only other solution a hardware issue? If it is could you guys let me know if 
[http://cgi.ebay.com/Logitech-QuickCam-Chat-V2-USB-Video-Webcam-Web-Camera-/370353285943?pt=PCA_Video_Conferencing_Webcams&hash=item563ac6ab37#ht_2150wt_1141](http://cgi.ebay.com/Logitech-QuickCam-Chat-V2-USB-Video-Webcam-Web-Camera-/370353285943?pt=PCA_Video_Conferencing_Webcams&hash=item563ac6ab37#ht_2150wt_1141)

this web cam is compatible with ubuntu 10.10? 
Thank you in advance!

---

### Post by sanad1995 on 2011-03-14
Or what about this one :$?
 [http://cgi.ebay.com/Real-30-0-Mega-Pixel-30-0M-6-LED-USB-PC-Webcam-w-Mic-/220539300593?pt=PCA_Video_Conferencing_Webcams&hash=item33592aaaf1#ht_3186wt_1141](http://cgi.ebay.com/Real-30-0-Mega-Pixel-30-0M-6-LED-USB-PC-Webcam-w-Mic-/220539300593?pt=PCA_Video_Conferencing_Webcams&hash=item33592aaaf1#ht_3186wt_1141)

---

### Post by no2498 on 2011-03-14
? did you try xawtv yet

---

### Post by sanad1995 on 2011-03-14
yes i have, every time i click on it it doesn't open though :/ so i assume its because my camera is being recognized. 
My camera was working on 10.04, is it worth downgrading? I haven't seen any major differences between the 2 firmwares.

---

### Post by sanad1995 on 2011-03-16
leettsss bump this baby~

---

### Post by no2498 on 2011-03-17
open a terminal type webcam click enter
did it load a cam grabber

also type lsusb click enter
do you see the cam in the list

---

### Post by vintagedaddyo on 2011-05-22
Perhaps this may help you.

I had client that had HP Pavilion dv9000:

> Bus 001 Device 003: ID 05ca:1810 Ricoh Co., Ltd Pavilion Webcam [R5U870]

Couldn't get the clients cam to work on Ubuntu 11.04 upgrade but this worked for me:

1. ```
sudo add-apt-repository ppa:r5u87x-loader/ppa
```
2. ```
sudo apt-get update
```
3. ```
sudo apt-get install r5u87x
```
4. ```
sudo /usr/share/r5u87x/r5u87x-download-firmware.sh
```


~good luck!

---

