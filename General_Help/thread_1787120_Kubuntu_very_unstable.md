---
title: "Kubuntu very unstable"
date: 2011-06-20
forum: General Help
---

### Post by Ric_NYC on 2011-06-20
After 30 minutes of use, Kubuntu starts to show gray squares and rectangles... something like this:

[[IMG]http://img857.imageshack.us/img857/9784/kubuntu.png[/IMG]](http://img857.imageshack.us/i/kubuntu.png/)



It becomes totally unresponsive and I have to use Ctrl + alt + backspace to re-start the computer.

What do you think is causing it?

---

### Post by enimeizoo on 2011-06-20
Maybe try to run top to try to see what process is making your system unresponsive. 
What is your kubuntu version?

---

### Post by Ric_NYC on 2011-06-20
Kubuntu 11.04.

---

### Post by enimeizoo on 2011-06-20
OK, but what about the top command before the system crashes? (it could be a memory leak)
Another thing to try is to see if it is located to the panel, or if desktop widgets also get this problem. Just add, let's say, a system tray on the desktop and see if the problem happens to it.
You can also try to create a new user and see if it happens under that user too.

By the way, what is your video card? And what driver are you using?

---

### Post by Ric_NYC on 2011-06-20
> **enimeizoo said:**
> OK, but what about the top command before the system crashes? (it could be a memory leak)
Another thing to try is to see if it is located to the panel, or if desktop widgets also get this problem. Just add, let's say, a system tray on the desktop and see if the problem happens to it.
You can also try to create a new user and see if it happens under that user too.

**By the way, what is your video card? And what driver are you using?**

Intel® Graphics Media Accelerator 900.

---

### Post by sffvba[e0rt on 2011-06-20
Switch of Blur in your System Settings -> Desktop Effects and see if it goes better...


404

---

### Post by Ric_NYC on 2011-06-21
> **not found said:**
> [B]Switch of Blur in your System Settings -> Desktop Effects and see if it goes better...
[/B]

404



All desktop effects disabled. No change.

---

### Post by sffvba[e0rt on 2011-06-21
> **Ric_NYC said:**
> All desktop effects disabled. No change.

Very strange... have you tried updating to KDE 4.6.4? - [http://www.kubuntu.org/news/kde-release-464](http://www.kubuntu.org/news/kde-release-464)

I know that this isn't the ideal solution but hey, who knows :)


404

---

### Post by Ric_NYC on 2011-06-21
> **not found said:**
> Very strange... have you tried updating to KDE 4.6.4? - [http://www.kubuntu.org/news/kde-release-464](http://www.kubuntu.org/news/kde-release-464)

I know that this isn't the ideal solution but hey, who knows :)


404


That's the version I have installed: 

**Platform Version 4.6.4 (4.6.4)**

---

### Post by sffvba[e0rt on 2011-06-21
It is times like these I wished I understood Linux a bit more because then we could have started to look through log files to see what was running when this happens... But as I am not there yet I will concede defeat for now and give a real expert a chance to answer...


404

---

### Post by Ric_NYC on 2011-06-21
> **not found said:**
> It is times like these I wished I understood Linux a bit more because then we could have started to look through log files to see what was running when this happens... But as I am not there yet I will concede defeat for now and give a real expert a chance to answer...


404


Thanks for your help.

---

### Post by Ric_NYC on 2011-07-06
**Update**:

I found what was the source of the problem: Google Chrome.


I've been using Firefox instead of Chrome and I had no more crashes.


Somebody fix it, please... I like Chrome a lot, but I cannot use it because it makes the system too unstable.

Thanks.

I hope this helps other users.

---

### Post by ankspo71 on 2011-07-07
Hi,
I am having no problems using Chromium on a daily basis, but I decided to install Google Chrome after reading your post to see if I would have the same problem as you. I do... Google Chrome locked up my system completely in about 2 minutes after starting it. Chromium still works fine.

So my advice is to try uninstalling Google Chrome and install Chromium (chromium-browser) instead. They are the same browsers but Chromium is opensource. You can find and install chromium-browser in kpackagekit and Synaptic Package Manager, etc.
Hope this helps.

---

### Post by Ric_NYC on 2011-08-05
> **ankspo71 said:**
> Hi,
I am having no problems using Chromium on a daily basis, but I decided to install Google Chrome after reading your post to see if I would have the same problem as you. I do... Google Chrome locked up my system completely in about 2 minutes after starting it. Chromium still works fine.

So my advice is to try uninstalling Google Chrome and install Chromium (chromium-browser) instead. They are the same browsers but Chromium is opensource. You can find and install chromium-browser in kpackagekit and Synaptic Package Manager, etc.
Hope this helps.


I tried Chromium for a day... and it crashed the system too.

Back to Firefox.


Thanks!

---

