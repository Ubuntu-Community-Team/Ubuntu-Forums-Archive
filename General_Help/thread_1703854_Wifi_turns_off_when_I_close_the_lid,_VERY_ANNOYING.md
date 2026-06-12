---
title: "Wifi turns off when I close the lid, VERY ANNOYING"
date: 2011-03-09
forum: General Help
---

### Post by asoccer345 on 2011-03-09
My wifi turns off whenever I close the lid or even if the screen times out. This has never happened on Windows, wifi was always on and I DIDNT have to re connect it after I closed the lid or the screen timed out! This has been bothering me forever, and I am adding this to a list of reasons to go back to Windows. Please Help, or that may become a near reality.

---

### Post by asoccer345 on 2011-03-09
Nobody? Really? Well, this is annoying, and another downer to Linux. No support at all.

---

### Post by wojox on 2011-03-09
> **asoccer345 said:**
> Nobody? Really? Well, this is annoying, and another downer to Linux. No support at all.

Any forum etiquette uses twenty-four hours before you bump a post. 

It's a little hard to help you without any info such as drivers and card.

---

### Post by asoccer345 on 2011-03-09
No ideas what driver or card. I have an Acer laptop? Aspire 3680. I doubt it really matters. Also, maybe I woudn't have to bump a post if people would actually reply.

---

### Post by saioke on 2011-03-09
> **asoccer345 said:**
> No ideas what driver or card. I have an Acer laptop? Aspire 3680. I doubt it really matters. Also, maybe I woudn't have to bump a post if people would actually reply.

You bumped your post within the first hour of posting. You didn't even give people enough time to respond. There's other people posting at this forum looking for problems as well so don't assume no one knows what your problem should be.

Anyway, drivers are very important. Many drivers particularly newer hardware may or may not work properly with Ubuntu. You should of researched what not just your network drivers were but everything else. However, I do not think inappropriate drivers is your issue since your WiFi seems to work until you're not using it, but then again certain drivers can cause problems like this. I wouldn't know of the cause, but someone out there is bound to have this same problem and knows of a fix. Just be patient. Sorry I couldn't be more helpful.

Anyway, perhaps you can take a look at this and follow instructions. I don't know if it'll be any good to you, but eh you never know...

> [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by mmsmc on 2011-03-09
go to ubuntu software manager and install sysinfo

---

### Post by WinterMadness on 2011-03-09
Do you have to enter a password when you open the lid?

If so, that may be the problem. Just disable that. Also, It may be going to sleep when you close it.

EDIT:

You shouldnt act like this forum is the customer support line to ubuntu. Nobody here cares if you decide to take your ball and go home. This is a community, and like any community you have to show respect, even if you have negative things to say.

---

### Post by asoccer345 on 2011-03-10
Yes, I have to enter a password whenever I close the lid. How do I disable that? Also, you say this is not the customer support line to Ubuntu. What is then? I heard that if you need help go to ubuntu forums. This is not a very good experience so far.

---

### Post by rubylaser on 2011-03-10
I think for your aggressive, rude attitude all the way through this post you've gotten good responses so far.  Do you get instant responses when you post to a Windows forum?...no you don't.  If you want instant help, pay for support from Canonical, [http://www.canonical.com/consumer-services/support]("http://www.canonical.com/consumer-services/support")

If you're willing to courtousely wait for people to try to help you with your problem out of the kindness of their heart's, this is the right place for you.  Also, you may try Google.  It can help with almost anything...
[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ubuntu+disable+sleep+on+laptop+close]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ubuntu+disable+sleep+on+laptop+close")

First result...
[http://www.addictivetips.com/ubuntu-linux-tips/disable-auto-sleep-to-prevent-laptop-from-sleeping-in-ubuntu/]("http://www.addictivetips.com/ubuntu-linux-tips/disable-auto-sleep-to-prevent-laptop-from-sleeping-in-ubuntu/")

---

### Post by WinterMadness on 2011-03-10
> **asoccer345 said:**
> Yes, I have to enter a password whenever I close the lid. How do I disable that? Also, you say this is not the customer support line to Ubuntu. What is then? I heard that if you need help go to ubuntu forums. This is not a very good experience so far.

Actually judging by the responses youve gotten, this is actually a good experience, you had a lot of people wanting to help you, despite you acting like a child towards them. We arent working for the ubuntu team, we arent getting paid. We are people who are hobbyists, we are here because we like ubuntu. We arent here to serve you, we are here to help you if we choose to. Thats how it works when you talk to people.

If you want professional help, you can pay Canonical.

I am not on a laptop at the moment, and it will be a while before I can get back one to find this out for myself, but I believe you can goto system->preferences->power management
and here you can determine what happens when the lid is closed

You can also look around yourself if thats not it.

---

### Post by asoccer345 on 2011-03-10
I'm sorry for acting rude. I'm just very frustrated. I still want it to make me log in, but I see no reason for it to turn off the WiFi as well. In system preferences it just lets me blank screen, which doesn't require me to give my password. Suspend does, but turns off the WiFi. I'm really sorry. :(

---

### Post by WinterMadness on 2011-03-10
[http://www.callum-macdonald.com/2008/06/11/ubuntu-lock-screen-on-laptop-close-lid/](http://www.callum-macdonald.com/2008/06/11/ubuntu-lock-screen-on-laptop-close-lid/)

which makes you use gconf

which is done by hitting alt+f2 and typing gconf-editor

click in this order
apps
gnome-power-manager
lock

on the right hand side now in the name section the first one should be:
blank_screen

check it, and lemme know how that works out for ya

---

### Post by asoccer345 on 2011-03-16
I'm sorry, I'm used to windows and I really don't want to have to do some complicated stuff. Surely there is a GUI way of just making the wifi not turn off when you close the display.

---

### Post by Chronon on 2011-03-17
WinterMadness gave you instructions on starting the configuration GUI and what to do so that it just blanks the screen when you close the lid.

---

### Post by mrspacklecrisp on 2011-03-17
Asus T101MT Tablet Netbook.

Since y'all are all here anyway, does anyone know if there's a setting which would allow me to leave the wireless on while the rest sleeps? Any help is appreciated.

---

### Post by Diego318 on 2012-04-10
Yeah Im having this same problem guys  

unchecking the "lock sceen on resume" does not fix the issue, wifi is disable after i close and then open the lid.  Im on an HP but i dont think its a hardware issue...

ALSO, im on KDE

---

### Post by Diego318 on 2012-04-10
OK I fixed this by going to System Settings then Hardware then Power Management, and then i clicked on the tab that says "Power Profiles" inside you can set what you want the computer to do when the lid is closed: Do Nothing, Hibernate, Sleep, Lock Screen, or Turn Off Screen.  Mine was initially set on Sleep so i tried Hibernate and that still shut the wifi off.  Once i set it on Lock Screen the wifi stayed on after closing and opening the lid.  Somehow this is different from the "Lock Screen on Resume" check box that's on the Global Settings tab.

Again, I'm on Kubuntu so im not sure how this works on Gnome

:guitar:

---

### Post by oldos2er on 2012-04-10
Closed, necromancy.

---

