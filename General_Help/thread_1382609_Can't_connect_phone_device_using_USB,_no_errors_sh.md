---
title: "Can't connect phone device using USB, no errors shown"
date: 2010-01-16
forum: General Help
---

### Post by Svens on 2010-01-16
Hello everybody!
I am having trouble with connecting my Sony Ericsson phone with my Ubuntu 9.10 using USB. It doesn't matter how I choose to connect it - "File Transfer" and "Phone Mode" - both does not work.
The phone IS charching, when it is connected, but it doesn't shows anywhere. 
When I type "lsusb" in terminal, it does not show me my phone. When I look in "/var/log/messages" there is NO error. It does not even show the procedure of connecting and disconnecting the phone. What could be the problem?

Thank You in advance!

---

### Post by Concrete on 2010-01-16
Did you try some other USB ports on motherboard? What model of SE cell you have?

---

### Post by Svens on 2010-01-16
Thank You for your answer!
Yes, all ports I have tried. Any other device works fine. I am trying to connect Sony Ericsson k610i.
I am using HP PAVILION dv6500 PC.

---

### Post by wangsuda on 2010-01-16
I use a Sony as well. Let's see what we can do.

1. Have you tried using Bluetooth as an alternative? File transfers and internet are now easy with the new Karmic Bluetooth files. While it doesn't solve your problem, it could be a workaround.

2. Go to the icon (I can't remember what it is called) that shows your internet and network activity. Right click on it and go to the "Mobile Broadband" tab. Is your phone there? If it is, delete it. Also delete the "Auto USB" under "Wired Connections," 

3. Once you've done all that, you should be able to plug in your phone and reinstall it. If that doesn't work, then . . . 

4. Buy a new USB cable for your phone. If one of the little prongs goes out on the phone end, all sorts of evil happens.

Hope this helps. Please keep me informed.

---

### Post by Kevbert on 2010-01-16
Most Sony Ericsson phones should work with USB or failing that Bluetooth. Again what's the phone model ? Does the phone have an option to connect in phone mode or file transfer mode ?
With my K800i I find it's easier to connect, in Ubuntu, via Bluetooth, as nothing appears to say it's connected.

---

### Post by wangsuda on 2010-01-16
> **Kevbert said:**
> 
With my K800i I find it's easier to connect, in Ubuntu, via Bluetooth, as nothing appears to say it's connected.My S500i puts out all sorts of notifications! LOL

---

### Post by Svens on 2010-01-16
> **wangsuda said:**
> I use a Sony as well. Let's see what we can do.

1. Have you tried using Bluetooth as an alternative? File transfers and internet are now easy with the new Karmic Bluetooth files. While it doesn't solve your problem, it could be a workaround.

2. Go to the icon (I can't remember what it is called) that shows your internet and network activity. Right click on it and go to the "Mobile Broadband" tab. Is your phone there? If it is, delete it. Also delete the "Auto USB" under "Wired Connections," 

3. Once you've done all that, you should be able to plug in your phone and reinstall it. If that doesn't work, then . . . 

4. Buy a new USB cable for your phone. If one of the little prongs goes out on the phone end, all sorts of evil happens.

Hope this helps. Please keep me informed.

Thank You for your answer.
The reason I wanted to connect my phone with USB, is to use it further with Virtualbox (XP), so I can update my phone software, so bluetooth won't be a solution.
My phone is not shown in any of your mentioned places - not in "Mobile Broadband" or "Wired connections".

But your given option for buying a new USB cable made me take a closer look to the cable, and I think it is not necessary to look for a solution anymore - **one of the prong is broken**. So it defineatly is the reason for this problem!

**I am very sorry for taking your time in thinking for solutions!**
Thank you all for your responsiveness and have a nice day!

---

### Post by wangsuda on 2010-01-16
> **Svens said:**
> 
But your given option for buying a new USB cable made me take a closer look to the cable, and I think it is not necessary to look for a solution anymore - **one of the prong is broken**. So it defineatly is the reason for this problem!Happened to me once, as well. Glad you found the root of your problem.

---

### Post by LrdOfNightmares on 2010-02-14
Hey guys, i happen to have the same problem but my cable is alright as i can connect my phone through windows.

What can i do to connect it in ubuntu???

---

### Post by wangsuda on 2010-02-14
> **LrdOfNightmares said:**
> Hey guys, i happen to have the same problem but my cable is alright as i can connect my phone through windows.

What can i do to connect it in ubuntu???A lot depends on the make of phone and the version of Ubuntu you are using. additionally, have you ever used your phone in Ubuntu? If not, just plug and play! Ubuntu will walk you through the setup steps. If you have used your phone before and SUDDENLY it's not working, follow my suggestions in post #4.

---

### Post by LrdOfNightmares on 2010-02-14
When i plug it in nothing happens xD

I am using W595 and ubuntu 9.04

---

### Post by wangsuda on 2010-02-14
> **LrdOfNightmares said:**
> When i plug it in nothing happens xD

I am using W595 and ubuntu 9.04
Take a clean, dry cloth and clean the little pointy things on the USB cable. Additionally, clean the USB plug-in slot on the floor. If nothing still happens, then try reading your phone via Bluetooth. You should also check your connection information to see if the phone is already there. If it is, delete it and try again.

---

### Post by LrdOfNightmares on 2010-02-14
Still nothing, and nothing in the  connection information, my phone is nowhere to be found Plus i don't have a bluetooth adapter as i am using a desktop pc

---

### Post by wangsuda on 2010-02-14
> **LrdOfNightmares said:**
> Still nothing, and nothing in the  connection information, my phone is nowhere to be found Plus i don't have a bluetooth adapter as i am using a desktop pc
OK, this step is a bit risky because it involves altering the settings on your phone. Go to your general menu>Internet tab>Connectivity>USB. Activate USB internet. If you can find your account settings, delete PS 3 and PS 4 (if they are there - THIS IS THE RISKY PART!).

---

### Post by LrdOfNightmares on 2010-02-14
Why is it risky? and what next?

---

### Post by wangsuda on 2010-02-14
> **LrdOfNightmares said:**
> Why is it risky? and what next?Plug your phone in and go! The later editions of Ubuntu generally need the phone's USB active, hence turning it on in the phone settings. Deteting extra (and generally unneeded) internet accounts gives Ubuntu room to create a file for its own settings. Now if this doesn't work, the only other suggestion I have is to reset your phone using the master reset (but you will lose all your data). **_[SIZE="3"]THIS IS A LAST RESORT![/SIZE]_**

---

### Post by LrdOfNightmares on 2010-02-14
I the USB category i have these options what should i choose?

**USB:**
Usb mode.
--------------------
|usb network
|        |
| Usb network type
|        |
|      Off
|        |
| Phone as modem
|        |
| Via Computer
--------------------------------
Usb Data accounts
         |
  SEMC GPRS
         |
    Vf MMS

---

### Post by wangsuda on 2010-02-14
I use a Sony S-500, so my menu is different. Can you change the "off" to "on"? That might help. Also clicking on "Phone as modem" might work as well. Please don't delete the data accounts.

---

### Post by LrdOfNightmares on 2010-02-14
I have choosen the "Phone as modem" option but again nothing happens :/

---

### Post by wangsuda on 2010-02-15
Sorry for the delay in getting back to you - hazards of living in the third world! LOL Anyway, about your problem! I am afraid I am fresh out of suggestions. Without being able to physically lay hands on your phone and system, I can't give any more accurate (or semi-accurate) advice. Good luck, and I hope someone comes along who can help you.

---

