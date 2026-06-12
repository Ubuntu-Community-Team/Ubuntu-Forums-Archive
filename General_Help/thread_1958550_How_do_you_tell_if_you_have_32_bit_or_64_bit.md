---
title: "How do you tell if you have 32 bit or 64 bit?"
date: 2012-04-14
forum: General Help
---

### Post by rickyhart91 on 2012-04-14
I want to install Google Chrome for Ubuntu, but I don't know whether I have the 32 bit or 64 bit version.

---

### Post by haqking on 2012-04-14
> **rickyhart91 said:**
> I want to install Google Chrome for Ubuntu, but I don't know whether I have the 32 bit or 64 bit version.

```
uname -m
```

if it says i386 or i686 then is 32 bit

if it says x64 then its 64 bit

---

### Post by na5h on 2012-04-14
You could also just use the Software Center to install the open-source version, Chromium.

---

### Post by rickyhart91 on 2012-04-14
> **na5h said:**
> You could also just use the Software Center to install the open-source version, Chromium.
I heard from the comments on Chromium that it crashes on 11.10 a lot more than Chrome does.

Also, I have a problem with installing files. I installed the 32 bit version of Chrome and saved it to the Downloads folder. After it downloaded, I clicked it, but the Software Center said that it couldn't open it.

---

### Post by raja.genupula on 2012-04-14
> **rickyhart91 said:**
> I heard from the comments on Chromium that it crashes on 11.10 a lot more than Chrome does.

Also, I have a problem with installing files. I installed the 32 bit version of Chrome and saved it to the Downloads folder. After it downloaded, I clicked it, but the Software Center said that it couldn't open it.

1 . I am using chromium in my 11.10 , to be frankly i have never faced any problem with that

2. cd to the directory where you have placed from the terminal and try to execute with this command , if you got any errors report us back . 

```
sudo dpkg -i filename.deb
```

---

### Post by rickyhart91 on 2012-04-14
[FONT=monospace]Is this right?
[/FONT]sudo dpkg -i google-chrome-stable_current_i386.deb

---

### Post by raja.genupula on 2012-04-14
> **rickyhart91 said:**
> [FONT=monospace]Is this right?
[/FONT]sudo dpkg -i google-chrome-stable_current_i386.deb

yeah its right .

---

### Post by haqking on 2012-04-14
> **rickyhart91 said:**
> [FONT=monospace]Is this right?
[/FONT]sudo dpkg -i google-chrome-stable_current_i386.deb

yes if thats the name of the deb.

or right click on it and choose install with gdebi if you have it.

---

### Post by rickyhart91 on 2012-04-14
dpkg: error: dpkg status database is locked by another process

---

### Post by haqking on 2012-04-14
> **rickyhart91 said:**
> dpkg: error: dpkg status database is locked by another process

means you have software centre or another package manager open such as synaptic.

---

### Post by rickyhart91 on 2012-04-14
I figured out what I was doing wrong, I didn't know I had to right click and click Ubuntu Software Center from the dropdown (I though you just had to double click it)

---

### Post by Yellow Pasque on 2012-04-14
I guess your issue is resolved? Please mark thread 'solved'.

---

### Post by dcstar on 2012-04-15
> **rickyhart91 said:**
> I want to install Google Chrome for Ubuntu, but I don't know whether I have the 32 bit or 64 bit version.

In 12.04 you simply look at the System Details or the Gnome system Monitor and it specifically tells you if the system is 32 or 64-bit.

Not sure if this change is now in 11.10.

---

