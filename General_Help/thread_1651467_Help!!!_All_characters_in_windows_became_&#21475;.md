---
title: "Help!!! All characters in windows became &#21475;"
date: 2010-12-23
forum: General Help
---

### Post by unsown on 2010-12-23
Just now, after I open my computer, all of sudden, all the characters in windows and menus became little rectangles. What shall I do?

---

### Post by ronnielsen1 on 2010-12-23
Is this a new install or has it been OK? Where dis you get your disk? Have you changed fonts or anything recently?

---

### Post by unsown on 2010-12-23
I've used it for several weeks and have successfully updated to 10.10 from 10.04. No big issue appeared until just now. I did not install anything since last boot up. And the image was downloaded from Ubuntu website

> **ronnielsen1 said:**
> Is this a new install or has it been OK? Where dis you get your disk?

---

### Post by unsown on 2010-12-23
It happens in windows UI, chromium tabs, menus, but not in web pages

---

### Post by theasprint on 2010-12-23
Hi,

Yup, same problem also. Characters turning into boxes.

But my problem only appears in Chinese fonts, and in Windows.
I don't have Ubuntu for now. (though i still can solve problems)

I think its the rendering for fonts that has problems sometimes.
You may want to restart your PC if you think its irritating.

---

### Post by ronnielsen1 on 2010-12-23
The only web sites I see that are similar talk about fonts but they're not much help

---

### Post by unsown on 2010-12-23
Of course I tried restarting the computer.

---

### Post by owiknowi on 2010-12-23
think the problem has to do with the system fonts settings (character encoding).
those must have been changed, probably not by you, and need to be reset to the default character encoding.

try the installation cd and choose 'repair a broken system'
first try the original 10.04 cd but probably you'll need the 10.10 cd now since you've updated?

or reboot to a prompt and from there...
unfortunately i don't know which command will do this for you.

if i'll find it i'll let you asap know.

---

### Post by owiknowi on 2010-12-23
found this:
[http://www.linuxquestions.org/questions/ubuntu-63/change-default-character-encoding-323706/](http://www.linuxquestions.org/questions/ubuntu-63/change-default-character-encoding-323706/)  (second answer).

hope it works for you.

---

### Post by unsown on 2010-12-23
No luck.
My ubuntu is English version. After ran the codes provided in that post: 
sudo dpkg-reconfigure locales
, I got following, and nothing else. And I've also restarted the system:
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.

> **owiknowi said:**
> found this:
[http://www.linuxquestions.org/questions/ubuntu-63/change-default-character-encoding-323706/](http://www.linuxquestions.org/questions/ubuntu-63/change-default-character-encoding-323706/)  (second answer).

hope it works for you.

---

### Post by unsown on 2010-12-23
The problem only happens in UI of the system. All the fonts displayed correctly in browser, including Chinese.

---

### Post by ronnielsen1 on 2010-12-23
> It happens in windows UI, chromium tabs, menus, but not in web pages

> The problem only happens in UI of the system.

What are you calling windows ui?

---

### Post by unsown on 2010-12-23
OMG. I found the solution. Just need to reinstall ttf-ubuntu-font-family by executing two command lines below (actually the first one solved my problem already):

sudo apt-get remove ttf-ubuntu-font-family
sudo apt-get install ttf-ubuntu-font-family

---

### Post by matt_symes on 2010-12-23
DOH. Too late

---

### Post by owiknowi on 2010-12-23
> **unsown said:**
> OMG. I found the solution. Just need to reinstall ttf-ubuntu-font-family by executing two command lines below (actually the first one solved my problem already):

sudo apt-get remove ttf-ubuntu-font-family
sudo apt-get install ttf-ubuntu-font-family

good to see you've got everything working again.

however it is an interesting problem: how did it happen?
if it's an update bug it may be good to also let the developers know?

---

### Post by unsown on 2010-12-25
I'm not sure what cause this problem. I feel no special things happened around the time it happened. But I do let Ubuntu update every time it notifies me.

> **owiknowi said:**
> good to see you've got everything working again.

however it is an interesting problem: how did it happen?
if it's an update bug it may be good to also let the developers know?

---

