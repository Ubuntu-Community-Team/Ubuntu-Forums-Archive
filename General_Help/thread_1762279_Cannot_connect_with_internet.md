---
title: "Cannot connect with internet"
date: 2011-05-19
forum: General Help
---

### Post by lakshmen on 2011-05-19
hi, i am new to ubuntu software. I have downloaded the version 10.10 and started the system but can't connect to the internet. I am using wireless and not sure how to connect to the wireless.

---

### Post by Sonicrulz12 on 2011-05-19
on the top panel you should see a wi-fi icon right click it and enable wireless
:)
 P.S. Did It work?

---

### Post by lakshmen on 2011-05-19
i saw it but it ask me to configure VPN, which i was not sure how to do....

---

### Post by Sonicrulz12 on 2011-05-19
You Should Look go to this link its about VPN and how to set it up [https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

---

### Post by Martin_sensei on 2011-05-19
> **lakshmen said:**
> i saw it but it ask me to configure VPN, which i was not sure how to do....

Are you sure you clicked on the right part?  You should see a list of Access Points when clicking on the network icon.  If you know what your Router is called, it should appear there, then clicking on it should prompt you for your network password.

---

### Post by lakshmen on 2011-05-19
just to ask which is a good website to download ubuntu 10.10? or where do u download ubuntu 10.10?

---

### Post by wildmanne39 on 2011-05-19
> **lakshmen said:**
> hi, i am new to ubuntu software. I have downloaded the version 10.10 and started the system but can't connect to the internet. I am using wireless and not sure how to connect to the wireless.

Hi, to help we need some information. open a terminal by ctrl+alt+t and type
sudo lshw -c network
then type 
nm-tool
Then type
lspci
then type
lsmod
then type
ifconfig

Each one of these commands will be done one at a time, after you type the first one copy and paste it here by clicking new reply then above the window you type in click on # and put the information in between the 2 code boxes ```

```,then run each one and copy and paste the same way all in this window with each one having there own set of code tags.

---

### Post by wildmanne39 on 2011-05-19
> **lakshmen said:**
> just to ask which is a good website to download ubuntu 10.10? or where do u download ubuntu 10.10?

Hi, go to ubuntu.com

---

### Post by rybaxs on 2011-05-19
I think you need a driver for your wifi. that's what I did. And after the wifi again is broken after few days and months using. just re-install the driver again then it works.

---

### Post by lakshmen on 2011-05-19
just a side qn: how do u run both windows and ubuntu the same time??

---

### Post by lakshmen on 2011-05-19
> **rybaxs said:**
> I think you need a driver for your wifi. that's what I did. And after the wifi again is broken after few days and months using. just re-install the driver again then it works.
 where to get the driver?

---

### Post by wildmanne39 on 2011-05-19
> **lakshmen said:**
> where to get the driver?
Hi, first we need to know the information I asked for in post 7 so we can help you get the drivers and get them installed.

---

### Post by wildmanne39 on 2011-05-19
> **lakshmen said:**
> just a side qn: how do u run both windows and ubuntu the same time??

Hi, you do it by putting windows in a virtual environment like virtualbox and then you can run both at the same time if your computer has enough resources.

---

### Post by lakshmen on 2011-05-19
Hey thanks guys for help... but now i cant download stuff like software sources..

---

### Post by wildmanne39 on 2011-05-19
> **lakshmen said:**
> Hey thanks guys for help... but now i cant download stuff like software sources..

Hi, is that on a wire connection? sense wireless has not been working. If so what error messages are you getting.

---

### Post by Sonicrulz12 on 2011-05-19
[Removed by User]

---

