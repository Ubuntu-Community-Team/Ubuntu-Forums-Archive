---
title: "Completely Crapped Out On Me..."
date: 2011-04-02
forum: General Help
---

### Post by Funklink on 2011-04-02
Here's my background I am going to share: I have a Dell Vostro 1400 Intel Core 2 Duo originally running Windows Vista, that is until about a week ago. I installled Ubuntu 10.10(?) I think it was. In fact, I loved it so much I installed it on my other Dell Inspiron (I have had no problems with that one, it's running the netbook remix though.) 

However, I had a problem emerge last night when I restarted. When I boot up (before it asks me to log in) I get two error messages. Once I clicked "Okay." I logged in and everything seemed normal. I soon noticed that it often glitched and the screen went blank for a few seconds and came back. Also, I was not able to connect to wireless networks. Actually, the wireless icon is no longer on the top panel on my desktop as it was originally when I had first booted the OS. I have since tried "Adding" a "Notification Area" to the panel and it had no success. 

I then connected via ethernet cable as I did when I had first gotten Ubuntu and had to install  drivers for Broadcom wireless etc. 

I then discovered that I cannot install packages/programs from the Ubuntu Software Center. I simply click "Install" and nothing happens. I don't get an error nor do I have to enter a password. So I could not have possibly had the change to enter a wrong password. 

What is wrong with my computer/OS? How can I fix it? At this point I was thinking of switching to a different Linux based operating system but I wanted to get some advice from others. ( I was just thinking of switching because I can over write it) However, now I cannot even download a program to burn an .iso to a live DVD/CD to boot from to install a new one. Any ideas?

---

### Post by matt_symes on 2011-04-02
Hi

> **Funklink said:**
> Here's my background I am going to share: I have a Dell Vostro 1400 Intel Core 2 Duo originally running Windows Vista, that is until about a week ago. I installled Ubuntu 10.10(?) I think it was. In fact, I loved it so much I installed it on my other Dell Inspiron (I have had no problems with that one, it's running the netbook remix though.)

Glad you like it.

> 
However, I had a problem emerge last night when I restarted. When I boot up (before it asks me to log in) I get two error messages. Once I clicked "Okay." I logged in and everything seemed normal. I soon noticed that it often glitched and the screen went blank for a few seconds and came back. Also, I was not able to connect to wireless networks. Actually, the wireless icon is no longer on the top panel on my desktop as it was originally when I had first booted the OS. I have since tried "Adding" a "Notification Area" to the panel and it had no success. 

Can you remember the error messages ?

Check network settings from ...

System->Preferences->Network connections

> 
I then connected via ethernet cable as I did when I had first gotten Ubuntu and had to install  drivers for Broadcom wireless etc. 

I then discovered that I cannot install packages/programs from the Ubuntu Software Center. I simply click "Install" and nothing happens. I don't get an error nor do I have to enter a password. So I could not have possibly had the change to enter a wrong password. 

Open a terminal and type.

```
sudo apt-get update
```

Enter your password. It will not be echoed to the screen. Post results back here between code tags. This will make it more readable.

> 
What is wrong with my computer/OS? How can I fix it? At this point I was thinking of switching to a different Linux based operating system but I wanted to get some advice from others. ( I was just thinking of switching because I can over write it) However, now I cannot even download a program to burn an .iso to a live DVD/CD to boot from to install a new one. Any ideas?

If you need to download things and cannot get network connection you can use a LiveCD/USB and download that way (if can get a connection). Using that you can save to the hard drive after you have mounted it.

Kind regards

---

### Post by Joe of loath on 2011-04-02
To continue on from the post above, if apt-get update works fine, try sudo apt-get upgrade and then reboot.

If you feel like switching, Ubuntu has a cd-burning tool built in. Just download the .iso and double click it to burn it.

---

### Post by nickleboyblue on 2011-04-02
...If absolute worst comes to absolute worst, you might consider trying Ubuntu 10.04, which is the long-term support edition of Ubuntu.  Sometimes, newer features mess things up to begin with, and it takes time to smooth out the bugs. If you are on an extremely mission-critical machine though, the long-term support edition is your best bet, because it has had quite some time to iron out the kinks.  That is, unless you can't live without the features of the latest releases.

---

