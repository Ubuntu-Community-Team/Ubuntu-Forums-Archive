---
title: "Low Graphics Mode- No GUI!!"
date: 2011-07-14
forum: General Help
---

### Post by che47audio on 2011-07-14
Hi there,
 
This is the first time I've ever posted and thats because I've never had any serious problem that I've been unable to resolve by researching online. However, the problem I have at the moment is beyond my understanding and I would appreciate some help to resolve it. 
 
I was playing around with Rhythmbox trying to get my iphone 4 to sync with it, which I now realise is not yet possible. I uninstalled the libimobiledevice package from the software center. When the uninstall was complete my screen went blank/black and after several minutes of waiting to see if it would sort itself out I decided to physically restart the pc. When the pc booted up it will no longer boot into the friendly ubuntu GUI I am so used to seeing, it now goes in to low graphics mode. From here I have the option of editing x setup/configuration, restarting x (which does nothing), or booting a failsafe graphics version ( which also does nothing when you click it. I have the option go to the console/command line from which a user of my limited understanding stands no chance!! 
 
I have tried "startx", this results in a blank, black screen with the mouse cursor but nothing else. I just want the friendly GUI back that I had set up perfectly for my needs. What worries me about this is I don't understand what relevance uninstalling/removing libimobiledevice would have concerning x or anything to do with graphics.
 
Sorry if this was long winded. Any help would be appreciated.
 
Thanks
 
che47audio

---

### Post by che47audio on 2011-07-14
Wh yhas nobody viewed or replied to this? Have I posted this in the wrong place?

---

### Post by realzippy on 2011-07-14
*I uninstalled the **libimobiledevice** package from the software center....*

...guess this uninstalled eg **ubuntu-desktop** also.

Since you are able to go to the console,run:

```
sudo apt-get install ubuntu-desktop
```

and

```
sudo reboot now
```

---

### Post by che47audio on 2011-07-14
I will try this now, thanks

---

### Post by che47audio on 2011-07-15
This sorted it perfectly. Thankyou very much I'm very grateful for your help.

che47audio

---

### Post by realzippy on 2011-07-15
You are welcome.Please set thread as solved (Threadtools)...

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

