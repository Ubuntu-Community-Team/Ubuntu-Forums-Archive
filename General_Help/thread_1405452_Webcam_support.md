---
title: "Webcam support"
date: 2010-02-12
forum: General Help
---

### Post by EliBei on 2010-02-12
Hi guys,

I would like to thank everyone in advance for their support.

I have been using Ubuntu karmic since a couple of weeks now. It is not my sole operating system, I have it as a dual boot along with Windows Vista, which remains the main OS of my laptop. 

I have to admit that Ubuntu worked better than I expected, installing it was easy, and all hardware worked properly, I had no trouble to connect to the internet and to add printers and so on. 

However, I ran into several problems from the beginning, like listening to certain music formats, but that was easily solved, and then came the biggest obstacle I am still facing which is making the webcam work with msn. I made sure that the webcam is actually working by using cheese and it does. 

I tried the empathy, but it wasn't supporting the webcam, until I found a user who recommended certain commands which allowed at least empathy to display the cam and mic icons in front of contacts, but the webcam still didn't work. aMSN is indicating that I am behind a router firewall, although I checked the router settings and the firewall is disabled. Emesene which has a very nice interface displays the cam icon and if i invited or get invited to view webcam, nothing happens. I tried the the KDE messenger Kopete but again, there's no icon or command I can access to activate a video chat. 

By the way, empathy is displaying the webcam option only for windows live messenger and not for yahoo.

I should note however, that using Skype I was able to establish a video chat and the picture was quite clear and net. If only users switch to Skype which on windows has a much better support for video chatting even on low speed connections.

So any suggestions to be able to connect via webcam to WLM contacts?

Final note, I do admit that Ubuntu is easier that windows in some aspects, but I wish if they made even more simplified, because frankly resorting to the command terminal isn't easy and intuitive and requires a steep learning curve. I am not complaining or anything, but that's a suggestion.

Regards

---

### Post by Satoru-san on 2010-02-12
Welcome to the forums :)

As far as drivers go you can thank this man

[http://www.theinquirer.net/inquirer/news/1047633/one-writes-linux-drivers-235-usb-webcams](http://www.theinquirer.net/inquirer/news/1047633/one-writes-linux-drivers-235-usb-webcams)

He wrote 235 webcam drivers for linux because his daughter needed it. Great story.

As far as programs that use webcam, you can do this...

```
apt-cache search webcam
```
AFAIK skype is able to support webcams in linux. I would give that a try.

Cheers.:KS

---

### Post by EliBei on 2010-02-13
Thanks for your reply,

I have used skype and it works correctly with full webcam support. However, since most people don't use skype, I cannot force them to download and install it. What I would like is to be able to use webcam with msn contacts using Empathy, Emesene, or aMSN. So far none of them are working. 
As I said, aMSN is indicating that I am behind a router firewall, although my router firewall is saying that it is disabled. 
Emesene shows the webcam icon, however, if i send a webcam invitation nothing happens and likewise, if someone sends me nothing happens. In the webcam preferences, Emesene detected my webcam Chicony USB 2 camera, and when I click on the name the camera's blue light goes on and I can see my self. However, as soon as I close the preferences dialog, the camera shuts down. 
Empathy,...well I researched it and some users indicated that one should run some commands, which I did, and now u can see besides each contact a the cam icon, However, I still haven't managed to establish a webcam connection with any. And I cannot receive the webcam invitation they send.

So any idea how to solve this.

Best regards

---

