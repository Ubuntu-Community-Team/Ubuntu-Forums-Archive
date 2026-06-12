---
title: "Evolution - Notification without the application running"
date: 2010-03-25
forum: General Help
---

### Post by thenailedone on 2010-03-25
Hello,

Running the Lynx and I have set up Evolution to download my Gmail e-mails but now I have a question.

When Evolution is running I get the notifications when e-mail come in and the little envelope at the top becomes "lit" to indicate I have new mail.  What I want to know is how can I get notified without having the application "open", still having the notifications etc. but without having the application window open (like when you "close" Rhythmbox but it is still running at the top even though the windows is closed)?

Is this possible?

---

### Post by coolcaseley67 on 2010-03-25
Hi 
 
-you can not , but use gmail notify :
[http://gmail-notify.sourceforge.net/download.php](http://gmail-notify.sourceforge.net/download.php) ! .
 
- turn on pop in gmail .
hope it helps

---

### Post by kerry_s on 2010-03-25
use "mail-notification-evolution" it's in the repo.

don't forget, you need to add "mail-notification" to the session startup so it starts when you log in.

---

### Post by thenailedone on 2010-03-25
> **kerry_s said:**
> use "mail-notification-evolution" it's in the repo.

don't forget, you need to add "mail-notification" to the session startup so it starts when you log in.

Thanks for the comments thus far...

Ok, installed mail-notification-evolution but now when I close Evolution I get an ugly flashing icon on my system tray saying that my "Inbox" cannot be found... as soon as I run Evolution again it is gone... so that didn't work...

---

### Post by kerry_s on 2010-03-25
> **thenailedone said:**
> Thanks for the comments thus far...

Ok, installed mail-notification-evolution but now when I close Evolution I get an ugly flashing icon on my system tray saying that my "Inbox" cannot be found... as soon as I run Evolution again it is gone... so that didn't work...

just set it up to check the mail directly, in the settings have it open evolution when clicked.

---

### Post by coolcaseley67 on 2010-03-25
hi
 
good way to do it i was not to sure it their was a plug in ! i will use that plug now thanks :p

---

### Post by thenailedone on 2010-03-25
> **kerry_s said:**
> **just set it up to check the mail directly**, in the settings have it open evolution when clicked.

Please excuse my ignorance, but how exactly do I set it up to check the mail directly (been going through the settings and I am not seeing it)...

---

### Post by kerry_s on 2010-03-25
> **thenailedone said:**
> Please excuse my ignorance, but how exactly do I set it up to check the mail directly (been going through the settings and I am not seeing it)...

you set up evolution to pop your mail right? use those same pop settings in mail-notification.

---

### Post by thenailedone on 2010-03-25
> **kerry_s said:**
> you set up evolution to pop your mail right? use those same pop settings in mail-notification.

You are right, this is one solution to my problem, got it working now, but it isn't 100% what I am requiring.  Now when I get a new mail I have a new icon appear showing me that I have mail and a little window pop up notifying me, yet the top right corner of Ubuntu Lucid Lynx already has a mail icon linked to Evolution... I want that one to light up, and the normal notification bubble to tell me I have mail (like what would happen if I had Evolution open when the mail arrives)...  The only temporary way I have found to do this which sucks is to keep Evolution open and on another desktop out of sight (but that is kind of lame)...

Typically Empathy is working correctly... I can close the main chat window but if someone comes online and sends me a chat message I am informed by the bubble at the top and the mail icon lights up... I want Evolution the same...

*EDIT:  Ok I have now got the notification pop-up to use the normal notification system and not it's own pop-up... still need it to use the already available notification icon...*

---

### Post by kerry_s on 2010-03-26
i don't know, it's been a while since i used "mail-notification", i use "checkgmail" on mine, running lubuntu(lxde). i can also leave sylpheed minimized as a icon, but don't. i haven't come across anything yet that does what you want, so i suggest you make a feature request for evolution.

---

### Post by thenailedone on 2010-03-26
> **kerry_s said:**
> i don't know, it's been a while since i used "mail-notification", i use "checkgmail" on mine, running lubuntu(lxde). i can also leave sylpheed minimized as a icon, but don't. i haven't come across anything yet that does what you want, so i suggest you make a feature request for evolution.

Well seeing the strides that have been made with Lucid Lynx and the layout of the icons on the task bar etc. I am holding thumbs that come April 29 this will be in place (would not make sense IMO if it didn't)... :D

---

### Post by kerry_s on 2010-03-26
> **thenailedone said:**
> Well seeing the strides that have been made with Lucid Lynx and the layout of the icons on the task bar etc. I am holding thumbs that come April 29 this will be in place (would not make sense IMO if it didn't)... :D

all the more important to make the request, they can't fix what they don't think of.

---

### Post by thenailedone on 2010-03-26
> **kerry_s said:**
> all the more important to make the request, they can't fix what they don't think of.

Ok, I hear you and bow down to your superior intellect ;) ... now to figure out how to do this... brb :popcorn:

*EDIT:... nope that didn't work... have gone to several places in the Ubuntu universe but none of them seem the place to request this feature... :( will keep looking...*

***EDIT: Nope, I suck... how can I request a feature for Lucid Lynx? :cry:***

---

### Post by coolcaseley67 on 2010-03-26
Hi 

- go here to make request for  it [https://launchpad.net/mail-notification ]("https://launchpad.net/mail-notification")
- You could you gmail-notifier until they fix , I've tested it and it works .

Hope it helps

---

### Post by thenailedone on 2010-03-26
> **coolcaseley67 said:**
> Hi 

- go here to make request for  it [https://launchpad.net/mail-notification ]("https://launchpad.net/mail-notification")
- You could you gmail-notifier until they fix , I've tested it and it works .

Hope it helps

I don't think that mail-notification is the solution... Evolution should make use of the existing mail icon... I should add a wish that Evolution is changed, not mail-notification...

---

### Post by coolcaseley67 on 2010-03-26
ok  

go to : [http://projects.gnome.org/evolution/](http://projects.gnome.org/evolution/) and [https://launchpad.net/evolution](https://launchpad.net/evolution)

---

### Post by thenailedone on 2010-03-26
> **coolcaseley67 said:**
> ok  

go to : [http://projects.gnome.org/evolution/](http://projects.gnome.org/evolution/) and [https://launchpad.net/evolution](https://launchpad.net/evolution)

Ok, filed a bug report (or at least, confirmed a bug)... seems Evolution quits when we choose to just close the window... if it works normally there would be no problem...

Thanks for all the assistance...

---

### Post by coolcaseley67 on 2010-03-26
no probs :KS i leaned some thing D

---

