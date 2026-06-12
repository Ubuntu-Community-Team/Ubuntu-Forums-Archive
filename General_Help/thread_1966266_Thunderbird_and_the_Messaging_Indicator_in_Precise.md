---
title: "Thunderbird and the Messaging Indicator in Precise"
date: 2012-04-26
forum: General Help
---

### Post by ThesaurusRex on 2012-04-26
Just did a fresh install to 12.04 from 11.04, using the default Unity desktop. I don't seem to be getting anything from the Messaging indicator applet. I'm running all the default things that I installed this morning: Thunderbird 11.01 with Global Menu Bar Integration 3.2 and Messaging Menu and Unity Integration 0.9.3. In Thunderbird, I go Preferences -> When new message arrives -> Show an alert, Play Sound. But nothing happens. No sound, no bubble notification, no change in color of the Messaging indicator, but Thunderbird clearly shows new messages. I tried installing notification-daemon but that didn't do anything either, even after another restart. Any suggestions?

---

### Post by ThesaurusRex on 2012-04-27
Bump?

Is there some way that I can simply check if that Messaging indicator is working at all? Worse comes to worse, I can download the source code for the messaging indicator and/or Thunderbird and try to customize it to work for me.

Would anyone recommend a different email client? I like Thunderbird a lot for it's openness, add-ons, and customization.

---

### Post by yinnus on 2012-04-27
i had the same issue.  i installed esound and it fixed it.

---

### Post by yinnus on 2012-04-27
i should add that this fixes the sound issue but not the visual indicator...

---

### Post by ThesaurusRex on 2012-04-27
> **yinnus said:**
> i should add that this fixes the sound issue but not the visual indicator...

Just to clarify: This means you still have the issue with the visual indicator (no bubble, no change in color of the indicator)?

It seems odd that the default mail client wouldn't work properly with the messaging indicator.

---

### Post by Rodney9 on 2012-04-27
I am having the same problem with The Indicator Applet and Thunderbird in Xubuntu 12.04.

New mail will show on the indicator by going blue only sometimes, it misses showing new mail an awful lot.

I sorted out the sound problem by following this post - [http://ubuntuforums.org/showthread.php?t=1869787](http://ubuntuforums.org/showthread.php?t=1869787)

Just need to fix the Indicator now.

Any clues ? Hopefully an update soon ?

Rodney

---

### Post by ThesaurusRex on 2012-04-27
Hm. Funny thing is, it just worked after I signed up for a launchpad account to report a bug for this issue. I installed the following packages:

esound
python-notify
notification-daemon

and it started working. By working, I mean I got a popping noise, a bubble, and the indicator turned blue. I'm not sure if it was the python-notify or the esound that helped it, but I'm not sure if notification-daemon was necessary.

Not sure if bug? Really seems like more of an oversight.

Additionally, link to my post on AskUbuntu (no responses as of this message): [http://askubuntu.com/questions/125778/why-wont-thunderbird-report-notifications-to-the-indicator-applet-on-12-04/126623#126623](http://askubuntu.com/questions/125778/why-wont-thunderbird-report-notifications-to-the-indicator-applet-on-12-04/126623#126623)

---

### Post by seamuso on 2012-04-29
Similar issue .. I run thunderbird over ssh when I'm in linux on my main desktop. Main was 10.10 until a few days ago and is now 12.04, remote machine has been 12.04 since the beginning of the month.

I no longer receive the popup alerts of new messages arriving as I was in 10.10.

Is there a way to get these working again? It's causing some communication issues between myself and my clients.

---

### Post by Ghost_Mazal on 2012-04-29
My indicator is also not working. I only get the bubble message , but the notification icon doesn't changed color.

---

### Post by Rodney9 on 2012-04-29
> **ThesaurusRex said:**
> Hm. Funny thing is, it just worked after I signed up for a launchpad account to report a bug for this issue. I installed the following packages:

esound
python-notify
notification-daemon

and it started working. By working, I mean I got a popping noise, a bubble, and the indicator turned blue. I'm not sure if it was the python-notify or the esound that helped it, but I'm not sure if notification-daemon was necessary.

Not sure if bug? Really seems like more of an oversight.

Additionally, link to my post on AskUbuntu (no responses as of this message): [http://askubuntu.com/questions/125778/why-wont-thunderbird-report-notifications-to-the-indicator-applet-on-12-04/126623#126623](http://askubuntu.com/questions/125778/why-wont-thunderbird-report-notifications-to-the-indicator-applet-on-12-04/126623#126623)

I added - 

esound
python-notify
notification-daemon

But still the new mail indicator plugin fails more often the not.

Is there some other way of getting mail alerts ?

Rodney

---

### Post by ray field on 2012-05-06
it might be too soon to confirm & I don't know whether it was some new stuff added with the Thunderbird update yesterday, or my adding (or updating?) notification-daemon, but the mail indicator seems to be working correctly now.

---

### Post by ray field on 2012-05-08
spoke too soon. the message indicator is very unreliable.

---

### Post by ray field on 2012-05-08
however, you might want to check out this tutorial showing how to use Python to create one that seems to work a good bit better

[http://conjurecode.com/create-indicator-applet-for-ubuntu-unity-with-python/](http://conjurecode.com/create-indicator-applet-for-ubuntu-unity-with-python/)

(or if you're like me, just copy out the code and paste it into a new file)

---

### Post by Rodney9 on 2012-05-08
> **ray field said:**
> spoke too soon. the message indicator is very unreliable.


Yes unfortunatly you are correct, even using Thundbird 12.0.1, the indicator still misses many new emails.

Hopefully a update fix will come soon.


Rodney

---

### Post by Rodney9 on 2012-05-08
> **ray field said:**
> however, you might want to check out this tutorial showing how to use Python to create one that seems to work a good bit better

[http://conjurecode.com/create-indicator-applet-for-ubuntu-unity-with-python/](http://conjurecode.com/create-indicator-applet-for-ubuntu-unity-with-python/)

(or if you're like me, just copy out the code and paste it into a new file)

Thanks but I'm using Xubuntu 12.04 and that python script seems to be just for gmail anyway.

Rodney

---

### Post by Ghost_Mazal on 2012-05-09
> **ray field said:**
> spoke too soon. the message indicator is very unreliable.

Yep , only works when it wants to.

---

### Post by ray field on 2012-05-09
the Python scripts are also fickle

---

### Post by axelmasok on 2012-05-10
> **seamuso said:**
> Similar issue .. I run thunderbird over ssh when I'm in linux on my main desktop. Main was 10.10 until a few days ago and is now 12.04, remote machine has been 12.04 since the beginning of the month.

I no longer receive the popup alerts of new messages arriving as I was in 10.10.

Is there a way to get these working again? It's causing some communication issues between myself and my clients.

Same here.  Just let Kubuntu update itself a couple days ago (Precise 12.04) and it upgraded from 10.x to 12.0.1
(I had to manually install 10.x because of a TLS/SSL incompatibly with our mailserver).  Luckily 12.0.1 now works with our mailserver (phew) but the KDE "Message Indicator" doesn't go green anymore....

---

### Post by Rodney9 on 2012-05-13
There has been a few general updates, but none for the Indicator.

Still missing most emails. Bad for a business who lives on their emails for sales etc

Is this a known bug, if not, how do we report it ?


Rodney

---

### Post by sknnksskn on 2012-05-13
This seems to be a known bug in thunderbird. 

See [https://bugs.launchpad.net/indicator-messages/+bug/957922/comments/2](https://bugs.launchpad.net/indicator-messages/+bug/957922/comments/2) for details.

Apparently thunderbird turns the indicator icon blue only for high priority messages. The suggested work around is to create a new message filter that marks all new messages as highest priority.

There is mention of a about:config option to fix the problem, but I couldn't find out what that option is.

---

### Post by sknnksskn on 2012-05-14
It seems there's a better work around.

echo 'user_pref("extensions.messagingmenu.attentionForAll", true);' >> ~/.thunderbird/*default*/prefs.js

Or

You could also create a new boolean entry in about:config (Preferences->Advanced->General->ConfigEditor)

See [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/841116](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/841116) for details.

---

### Post by Rodney9 on 2012-05-15
Thanks for the bug confirmation, sad though, you couldn't recommend this for business, imagine how many sales you might miss.

Should be an easy way to change the priority, I've set the ```
extensions.messagingmenu.attentionForAll
``` in the about:config.

but still the Indicator fails most of the time.

Rodney

---

### Post by Rodney9 on 2012-05-15
> **sknnksskn said:**
> It seems there's a better work around.

echo 'user_pref("extensions.messagingmenu.attentionForAll", true);' >> ~/.thunderbird/*default*/prefs.js

Or

You could also create a new boolean entry in about:config (Preferences->Advanced->General->ConfigEditor)

See [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/841116](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/841116) for details.


Thanks, but that doesn't work, the indicator is still missing most of my emails.

Rodney

---

### Post by Rodney9 on 2012-05-23
Still no fix ?


Rodney

---

### Post by winecurmudgeon on 2012-07-19
I got it to work in Xubuntu 12.04, mostly, by uninstalling the global messaging integration via synaptic and enabling the global menu bar integration addon 3.2.5. The addon still works, even if Ubuntu turned it off in the application.

I get a blue mailbox on the panel indicator, and the mail indicator on the pulldown menu tells me how many messages are in my mail box.

Hope this works for the rest of you.

---

### Post by axelmasok on 2012-08-01
What are the actual package names you un-installed and installed?  My search of Synaptic shows no such packages.

---

### Post by OrangeCrate on 2012-08-01
From the guy who wrote it, here's why the indicator doesn't turn blue all of the time...

> 
Thunderbird actually does turn the icon blue already, but not for all messages. The reason for this is people complained to me in Oneiric that the icon was being turned blue far too much. In fact, for some people (including me), the icon was blue pretty much permanently as long as Thunderbird was open, and this reduces the usefulness of the messaging indicator for notification of real-time messages to pretty much zero. In fact, people just got so fed up of it that they were asking me how to disable this feature in Thunderbird entirely...


[https://bugs.launchpad.net/indicator-messages/+bug/957922/comments/2](https://bugs.launchpad.net/indicator-messages/+bug/957922/comments/2)

Personally, I for one, prefer the indicator the way he wrote it. Unless a person lives their life staring at the computer screen waiting for new messages, the blue indicator can get pretty annoying.

---

### Post by ray field on 2012-08-01
> **OrangeCrate said:**
> From the guy who wrote it, here's why the indicator doesn't turn blue all of the time...



[https://bugs.launchpad.net/indicator-messages/+bug/957922/comments/2](https://bugs.launchpad.net/indicator-messages/+bug/957922/comments/2)

Personally, I for one, prefer the indicator the way he wrote it. Unless a person lives their life staring at the computer screen waiting for new messages, the blue indicator can get pretty annoying.

that link suggests the remedy to the problem is in about:prefs. I can't confirm yet, but my guess is that 

extensions.tbindicator.showIndicator 

set to "yes" blues the indicator with *any* unread mail. so far it has for me, but I've only tested it for an hour.

---

### Post by black veils on 2012-08-02
**alternative email checkers:**

-  mail-notification (it might actually be the default)

-  unity-mail

-  coolmail

possibly more.

-  what i have used for years is a notifier addon in firefox, called **webmail notifier**. there is a simpler version for google chrome and opera, called **x-notifer**. the popup can stay there until clicked, or go away by itself. it will show over seemingly anything you are doing. just make sure the web browser is running at all times.

---

### Post by cbennett926 on 2012-10-23
Any luck on getting this figured out? I am on 12.10 now and the indicator will not turn blue, and I am not getting popups, however the sound notification is working.

---

