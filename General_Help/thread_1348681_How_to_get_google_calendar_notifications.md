---
title: "How to get google calendar notifications?"
date: 2009-12-07
forum: General Help
---

### Post by sexyclient2 on 2009-12-07
I'm looking for a lightweight app to get notifications from my google calendar.  It's not important that I edit the notifications at all or that it integrates with "contacts" and especially not "mail" (so no bloated evolution or sunbird, please) instead just calendar notifications...

Is there an app that I don't know about that checks google calendar for events and then notifies me of these events? Preferably it should use a persistent window with snooze (kinda like gnomedo's remindme plugin) or something rather than the transient osd notifications that last for only a few seconds then disappear without regard for whether I've received the notification.  This is linux, the customizable OS, after all so is there a way that I can make this happen?

[B]update:
[/B]After using google calendar's email alert to get emails of event notifications, then applying the label "Calendar" to all mail that came from "calendar-notifications@gmail.com" I can use the resulting atom feed ([https://mail.google.com/a/mydomain.com/feed/atom/Calendar](https://mail.google.com/a/mydomain.com/feed/atom/Calendar) - for my apps domain) to get feed notifications of my events. 

Now, though, I need a lightweight rss notifier with persistent notifications -- a surprisingly daunting task.  RSSOwl notifies me just right (the notification stays there until I get rid of it,) but is too bloated.  Nothing else has worked yet.  If I could get something that sits in the tray and gives me an OSD notification every minute or so, that would be perfect.  Anyone have any suggestions?

---

### Post by sexyclient2 on 2009-12-07
anyone?

---

### Post by wsims2 on 2009-12-07
What kind of notification are you looking for? 

Why not use SMS or email to let you know about events? 

I sync my google calender with windows mobile and active sync. 

[http://www.google.com/mobile/products/sync.html#p=default](http://www.google.com/mobile/products/sync.html#p=default)

---

### Post by pqwoerituytrueiwoq on 2009-12-07
mail notification

---

### Post by sexyclient2 on 2009-12-07
> **wsims2 said:**
> What kind of notification are you looking for? 

Why not use SMS or email to let you know about events? 

I sync my google calender with windows mobile and active sync. 

[http://www.google.com/mobile/products/sync.html#p=default](http://www.google.com/mobile/products/sync.html#p=default)

I'm not that close to my mobile phone, so texting isn't a very viable option.  Email notifications are good, but they aren't persistent.  I don't check my inbox regularly enough, and often leave unread messages in there.  Also I prioritize my appointments much higher than regular emails, so I'd like to keep them distinct.

I'm really looking for something that gives me persistent notifications until I acknowledge that I have taken notice of the notification as opposed to the standard passive notification where I get the notification on my computer but don't necessarily get to take notice of it.

---

### Post by sexyclient2 on 2009-12-07
OK, so I've applied generous amounts of ingenuity to this problem and have come up with the following:

I use email notifications (no way around it, apparently) in gmail, apply the label "calendar" to all mail from "calendar-notifications@google.com" and then use the (very convenient) ability of generating an atom feed for all mail with this label, and use a lightweight atom/rss notifier to alert me of the event!

The problem I've now run into is that I've found NO suitable feed notifiers that are lightweight and provide the desired effect!!  RSSOwl's notification is as close to perfection as I've encountered thus far, (though info in the notification isn't as concise as I'd like it, the notification stays there until I remove it,) but it's way too slow and eats up almost as much memory as firefox!!  

I'm now looking for an atom feed notifier that can provide persistent notifications, and then everything will be perfect.

---

### Post by sexyclient2 on 2009-12-08
suggestions?

---

### Post by kkharinarayanan on 2010-12-30
well it is not a neat trick.
you said you get all the calender mails labeled right. 
so just use any email watcher like gmail watcher to watch that particular label

---

