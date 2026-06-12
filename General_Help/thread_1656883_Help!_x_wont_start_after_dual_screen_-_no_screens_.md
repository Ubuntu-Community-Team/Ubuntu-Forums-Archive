---
title: "Help! x wont start after dual screen - no screens found"
date: 2010-12-31
forum: General Help
---

### Post by Mesqueeb on 2010-12-31
Hi!
After installing a second screen and trying dual screens, i never backedup the x11 xorg.config file and recklessy overwrote my settings through that nvidia panel...
Now to find that x wont start :
(EE) no devices detected
Fatal server error:
No screens found

I have no idea how i'd be able to share my xorg.config file with you guys, I am using my ipod now...
Anyone knows anything? I tried reconfiguring and didn't work..
How do i share my file so you guys can find the flaw? Or how do i find the flaw myself?

-Mesqueeb

---

### Post by imcecil on 2010-12-31
which version of ubuntu are you using?
with the newer versions the xserver will often configure itself you could try backing up the config then restarting the server?

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo rm /etc/X11/xorg.conf
sudo restart gdm

if you still can't get to the graphical then you could try links a text web browser
and post the output through that

apt-get install links2

---

### Post by Mesqueeb on 2010-12-31
Congratulations!!!!
Rm did the trick!!!! What does it do?
TANKS SOMACH!!!!!xD


Now i have 2 screens which are actually only 1...
What should I follow to correctly setup dual screens?

---

### Post by imcecil on 2010-12-31
since your using the proprietary nvidia drivers I think going through the nvidia panel was the correct method.
Try checking that the proprietary nvidia drivers are installed and it is nvidia not nv being loaded when you turn on the dual display.
if all still fails which it probably will try posting that xorg.conf that nvidia panel generates here, somebody might have and idea.

if you try to change the display settings through preferences->display and your using the proprietary driver it should tell you to use the nvidia panel which is an easy test

also which version of ubuntu are you using

---

### Post by Mesqueeb on 2010-12-31
It worked!!!! Since I went on ahead to the propriety drivers I suddenly noticed the wrong driver being enabled!
After correcting, rebooting, and trying dual screen, everything is fine now!
Thanks so much!

(ps: ubuntu 10.10 it was xP, sorry for the delay, haha)

---

### Post by Mesqueeb on 2010-12-31
Hey! But I have one last question! With enabling xinerama i can't adjust the contrast of 1 of my screens seperately! But my old screen suddenly got major low-contrast... it's like grey xP

Are there commands to manually editing one of the two screens' contrast? Thanks!

Oh and happy New Year!

---

