---
title: "Looking for Outlook, evolution or Zimbra alternative"
date: 2011-05-09
forum: General Help
---

### Post by StepNjump on 2011-05-09
Hi guys,

I am looking for an application that would run well in linux that would allow me to schedule appointments and tasks (if it does more, than great but it doesn't have to).

I need to collaborate with some other people on my tasks so I need a client that will allow me to synchronize my tasks with others' tasks.

Outlook is a great client and I was told that it works well under wine. However, I'm not sure if there are any applets out there that will allow to synchronize from within Ubuntu with those other clients running under Windoze.

I would even have no problem to switch to a new application if I had to (though I would rather stay with Outlook) but then it has to be cross platform (it has to work in Windoze too).

Zimbra looks nice but then the collaboration pack is very expensive.

Does anyone have any idea what I could do?

Thanks guys in advance,

StepNjump

---

### Post by 3 frags left on 2011-05-09
Try Thunderbird; it's form the same guys of Firefox.
[http://www.mozillamessaging.com/en-US/thunderbird/](http://www.mozillamessaging.com/en-US/thunderbird/)

Also, you want to run Microsoft Outlook or Outlook Express? If it is the former, then I have bad news for you...
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7533](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7533)
However, hope is not to be lost. You may try to install in a Windows virtual machine and then copy its files to Wine's *drive_c* folder. Don't forget to export all of its registries (there is a post concerning this at the bottom of this page I linked), Common Files and Application Data folders! Exporting odbc32.dll and odbcint.dll may also help.

---

### Post by Rasa1111 on 2011-05-09
+1 for Thunderbird! <3

---

### Post by An Sanct on 2011-05-09
Well, Thunderbird and runs in multiple worlds (Win/Linux/...). Also there are some calendar applications from Mozilla, that integrate with Thunderbird very well.

---

### Post by collisionystm on 2011-05-09
> **StepNjump said:**
> Hi guys,

I am looking for an application that would run well in linux that would allow me to schedule appointments and tasks (if it does more, than great but it doesn't have to).

I need to collaborate with some other people on my tasks so I need a client that will allow me to synchronize my tasks with others' tasks.

Outlook is a great client and I was told that it works well under wine. However, I'm not sure if there are any applets out there that will allow to synchronize from within Ubuntu with those other clients running under Windoze.

I would even have no problem to switch to a new application if I had to (though I would rather stay with Outlook) but then it has to be cross platform (it has to work in Windoze too).

Zimbra looks nice but then the collaboration pack is very expensive.

Does anyone have any idea what I could do?

Thanks guys in advance,

StepNjump

Zimbra Collab is for the Server software itself lol. 

You just want ZImbra Desktop. Its free and magical.

I use it everyday. I 'strongly dislike' Thunderbird and Evo.

[http://www.zimbra.com/products/desktop.html](http://www.zimbra.com/products/desktop.html)

---

### Post by Rasa1111 on 2011-05-09
So what can "zimbra" do that thunderbird cannot? 
I'm not seeing anything that makes me want to jump on it.
But if you can pinpoint some +'s, I might be interested... lol

 and it's 107 MB's?  lol
Say what.... O_o  :rolleyes:

Not a fan of bloatware.

---

### Post by collisionystm on 2011-05-09
Well.... Do you use gmail? We have google apps mail at work. It automatically syncs calendar and contacts without any additional add ons. Less settings to tweak to make it friendly to someone coming from outlook. It looks better and more familiar to outlook. Your choice which way you want to go... I am not a salesman for the product, its just my personal choice.

---

### Post by Rasa1111 on 2011-05-09
No I stay away from gmail. 
GMX all the way. 

Yeah I was gonna say.. looks more like a windows app/outlook than anything.
and 107 MB's is whacky imho. 

Thanks for explaining tho.

---

### Post by StepNjump on 2011-05-09
Thanks you guys. I appreciate all your quick replies!

I will try them both (Thunderbird and Zimbra). I am disappointed though that none of them allow for categories and sub-categories. This could be nice for future versions.

Are you guys sure that I can actually collaborate with others using Thunderbird?

Also, I guess Zimbra is bigger in size because it seems to be doing much more than tasks scheduling. It seems to be a big collaboration suite.

Pete

---

### Post by StepNjump on 2011-05-09
You use Zimbra under which distro of Ubuntu? Kubuntu, Xubuntu? And which version? 10.10? Have you tried it under 11.04?

> **collisionystm said:**
> Zimbra Collab is for the Server software itself lol. 

You just want ZImbra Desktop. Its free and magical.

I use it everyday. I 'strongly dislike' Thunderbird and Evo.

[http://www.zimbra.com/products/desktop.html](http://www.zimbra.com/products/desktop.html)

---

### Post by StepNjump on 2011-05-09
Ok I installed Zimbra. Here are my comments.
Though the interface looks really nice and tidy, these guys cannot think it seems that some of us are not mouse users! I hate having to use my mouse to navigate around!!! It takes way too long!
I want to be only tabbing around. In outlook, i can just do as following: never have to touch the mouse:

ctrl-n (for new task)
this is a test task tab
1d (that`s to schedule a task for tomorrow, what a novel idea!)
alt-g (to go straight to the categories)
per (to scroll down to my category called personnal)
ctrl-enter to save

That`s so simple! Why is it nowadays we are forced to use our mice that much? We don`t even have the time now to breathe, yet alone fool around with computers. Make it simple people!!! please!

Ok, I will try thunderbird now.
Too bad evolution doesn`t work in windows because from what I remember, it was pretty simple on this app.

---

### Post by layers on 2011-05-09
I like Thunderbird. I am not exactly sure what the difference is, but, yeah, you can do everything without a mouse (I though it was only me).

Also, if you are installing different version of buntu, all you need is to copy the folder in ~/.thunderbird, and the new thunderbird will have all the mail from the old one - no need to downloading everything again.

---

### Post by StepNjump on 2011-05-09
Yep! Sometimes I think it`s just me also! Who has time to get back to a mouse even for a few seconds, it takes too long!


Ok, I downloaded Thunderbird and cannot see anything in there about tasks. Am I supposed to download an add-on? Also, there doesn't seem to be any field where I can specify different categories, other than creating folders. Is that true?

Also, please let me know, is it possible to share the tasks that I write on my offline computer to share with my girlfriend once I synchronize with the server?

Thanks

> **layers said:**
> I like Thunderbird. I am not exactly sure what the difference is, but, yeah, you can do everything without a mouse (I though it was only me).

Also, if you are installing different version of buntu, all you need is to copy the folder in ~/.thunderbird, and the new thunderbird will have all the mail from the old one - no need to downloading everything again.

---

### Post by StepNjump on 2011-05-09
In a way, I'm glad I'm not the only one! ;) 
:confused:

> **StepNjump said:**
> Yep! Sometimes I think it`s just me also! Who has time to get back to a mouse even for a few seconds, it takes too long!


Ok, I downloaded Thunderbird and cannot see anything in there about tasks. Am I supposed to download an add-on? Also, there doesn't seem to be any field where I can specify different categories, other than creating folders. Is that true?

Also, please let me know, is it possible to share the tasks that I write on my offline computer to share with my girlfriend once I synchronize with the server?

Thanks

---

### Post by StepNjump on 2011-05-09
At last guys, I found something relatively good. Do any of you know Toodledo and Taskunifier?

---

### Post by CptSnork on 2011-07-05
Sorry for chiming in so late on this thread but I have a similar problem. Zimbra looks great and I use Thunderbird which is awesome as well! 

BUT:


[LIST]
[*]What if you already have an email server (let's say cyrus)?
[*]You want to share your calendar?
[*]You want to a web interface for your email + calendar?
[*]And it has to work with ldap/AD?
[/LIST]
Anything out there that runs on top of a variety or email servers and has a nice web gui for email+calendar sharing?

---

### Post by SeijiSensei on 2011-07-05
You need to install [Lightning]("http://www.mozilla.org/projects/calendar/lightning/") to get the calendaring and similar functions in Thunderbird.

---

### Post by perspectoff on 2011-07-05
I like DAViCal for the group calendar server.

+1 for Thunderbird (with the Lightning add-on as the group calendar client).

Lightning (for Thunderbird) is only 32-bit, though. If you are using 64-bit, I recommend Sunbird (which is really the same as Lightning, but in a standalone client).

DAViCal:

[http://ubuntuguide.org/wiki/Ubuntu:Natty#DAViCal_Calendar_Server](http://ubuntuguide.org/wiki/Ubuntu:Natty#DAViCal_Calendar_Server)

or

[http://www.kubuntuguide.info/index.php/Natty#DAViCal_Calendar_Server](http://www.kubuntuguide.info/index.php/Natty#DAViCal_Calendar_Server)

Thunderbird with Lightning:

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Lightning_calendar_extension](http://ubuntuguide.org/wiki/Ubuntu:Natty#Lightning_calendar_extension)

or

[http://www.kubuntuguide.info/index.php/Natty#Lightning_calendar_extension](http://www.kubuntuguide.info/index.php/Natty#Lightning_calendar_extension)

Sunbird:

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Mozilla_Sunbird_.28Calendar.29](http://ubuntuguide.org/wiki/Ubuntu:Natty#Mozilla_Sunbird_.28Calendar.29)

or

[http://www.kubuntuguide.info/index.php/Natty#Mozilla_Sunbird_.28Calendar.29](http://www.kubuntuguide.info/index.php/Natty#Mozilla_Sunbird_.28Calendar.29)

For a full-featured, mature groupware system, it is hard to beat Zimbra. It takes a powerful server, though. It is Java-based and very sluggish.

---

### Post by uRock on 2011-07-05
> **perspectoff said:**
> I like DAViCal for the group calendar server.

+1 for Thunderbird (with the Lightning add-on as the group calendar client).

Lightning (for Thunderbird) is only 32-bit, though. If you are using 64-bit, I recommend Sunbird (which is really the same as Lightning, but in a standalone client).
I have 64bit T-Bird with Lightning.

To install the Thunderbird PPA,```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
```
To upgrade your working Thunderbird to the latest and greatest,```
sudo apt-get update && sudo apt-get upgrade
```
To install the latest stable version if Thunderbird is not already installed,```
sudo apt-get install thunderbird
```

---

