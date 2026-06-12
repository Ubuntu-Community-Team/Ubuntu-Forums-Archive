---
title: "Sync Google Tasks with Thunderbird"
date: 2011-11-25
forum: General Help
---

### Post by Joshimitsu on 2011-11-25
From what I know, there doesn't appear to be a seamless way to do this.  I've seen a few work-arounds that are a little cumbersome, and many suggest to stop using Google Tasks and move over to RTM.  Thing is, there doesn't seem to be an add-on for RTM either for Thunderbird.  So here's a solution I'm using that seems to work.

The idea is to open google tasks in a tab in thunderbird.

The problem I had before is that when opening a browser tab in thunderbird, the tasks would not show - something to do with javascript not being enabled in thunderbird.  The way around this is to use the mobile/android/iphone interface instead of the normal web version.

So,

1. Install Google Calendar Tab*

2. In thunderbird, Tools > Add-ons, go to your installed Add-ons under Extensions and find Google Calendar Tab.  Click preferences. Select, "Google Apps for your domain"  In the URL paste: [https://mail.google.com/tasks/android](https://mail.google.com/tasks/android)

When you click the Google Calendar Tab icon in thunderbird now, you should see your Google Tasks turn up, allowing you to edit, add and delete as you would from your browser. 

It's not perfect, but it works!

*If you already use Google Calendar Tab to sync your Google calendar, then obviously you can't use this method.  I would reccommend finding another thunderbird add-on that allows you to specify the URL of a site you want to open and then use the android interface address.  Or, use Provider for Google calendar for your calendar sync and then use the above method for your tasks.

Hope this is helpful for someone.

---

### Post by Alien.col on 2012-01-11
Good solution... I'm one of them who uses calendar tab.

What I did is that I downloaded the web application in a tab plugin, its called WAT.

I then added a bookmark for [https://mail.google.com/tasks/android](https://mail.google.com/tasks/android)

and it works as expected. I have the android tasks in a tab. Ugly but works well. :D

Thanks.

---

### Post by nebajoth on 2012-04-05
There is an assigned [bug open on the Mozilla bugzilla]("https://bugzilla.mozilla.org/show_bug.cgi?id=493389"), for adding the feature of synchronizing [Google Tasks]("http://groups.google.com/a/googleproductforums.com/forum/#!category-topic/calendar/new-ideas/KiHH_ZnEqOY") to [Lightning's]("https://addons.mozilla.org/en-US/thunderbird/addon/lightning/") analogous tasks bar.

The single developer to whom the bug has been assigned is too busy to do it. See the comments in the Mozilla Bugzilla.

This is a good substitute that will fill the need until someone picks up the torch.

Thank you, OP.

---

### Post by Panchocp on 2012-04-28
Hi, the solutions work properly.
It's so useful.

---

### Post by frouty on 2012-05-06
Hy,

Doesn't work off line.

While in a plane, try to open TH and your calendar tab, it won't open. 
So you won't get  your todo list while offline and won't be able to update
your task list while offline with this solution which work but not offline.

Laurent FRANCOIS

---

### Post by natrium on 2012-07-23
> **Joshimitsu said:**
> From what I know, there doesn't appear to be a seamless way to do this.  I've seen a few work-arounds that are a little cumbersome, and many suggest to stop using Google Tasks and move over to RTM.  Thing is, there doesn't seem to be an add-on for RTM either for Thunderbird.  So here's a solution I'm using that seems to work.

The idea is to open google tasks in a tab in thunderbird.

The problem I had before is that when opening a browser tab in thunderbird, the tasks would not show - something to do with javascript not being enabled in thunderbird.  The way around this is to use the mobile/android/iphone interface instead of the normal web version.

So,

1. Install Google Calendar Tab*

2. In thunderbird, Tools > Add-ons, go to your installed Add-ons under Extensions and find Google Calendar Tab.  Click preferences. Select, "Google Apps for your domain"  In the URL paste: [https://mail.google.com/tasks/android](https://mail.google.com/tasks/android)

When you click the Google Calendar Tab icon in thunderbird now, you should see your Google Tasks turn up, allowing you to edit, add and delete as you would from your browser. 

It's not perfect, but it works!

*If you already use Google Calendar Tab to sync your Google calendar, then obviously you can't use this method.  I would reccommend finding another thunderbird add-on that allows you to specify the URL of a site you want to open and then use the android interface address.  Or, use Provider for Google calendar for your calendar sync and then use the above method for your tasks.

Hope this is helpful for someone.



thanx! nice trick :)

natrium

---

### Post by chris.psyctc on 2012-08-26
Hm.  Using WAT doesn't work for me as the google site says I'm not allowing cookies and I can't see how to override that.  I did use the config editor and set network.cookie.alwaysAcceptSessionCookies to true and restarted TB but that didn't change it. Any ideas?  Seems tragic that it's so hard to synch TB with android, just as bad to try to synch contacts to TB addressbook.  I had no idea this would be the case.

---

### Post by chris.psyctc on 2012-08-26
Whoops.  Googled a bit more and it is easy enough to overcome the cookie problem.  On my linux version of TB that's Edit -> Preferences (in Windoze I think that's Tools -> Options) then the security tab and the web content tab inside that and just tick "Accept cookies from any site".

Having said that, the google task system seems so simple I'll stick without the synch I think as I do want a system that allows me to set due dates for tasks at least.  The one in Lightning is a pretty good compromise between simplicity and power with categories, due dates/times, start times (never use those) and a good comments field.  I'd just assumed these were a fairly common minimum data set for task lists and that synching them between public calendars would be sorted.  Ouch.

---

### Post by bobjohnbowles on 2012-10-20
The Google Tasks Sync addon (see [this link]("https://code.google.com/p/gt-tasks-sync/")) is too new to be on the Mozilla site yet, but I installed it manually into TB and it works fine.

---

### Post by dumpster25 on 2012-10-29
> **bobjohnbowles said:**
> The Google Tasks Sync addon (see [this link]("https://code.google.com/p/gt-tasks-sync/")) is too new to be on the Mozilla site yet, but I installed it manually into TB and it works fine.

Thanks for the tip. This works perfectly! :D

---

### Post by jpaul3 on 2013-01-04
> **bobjohnbowles said:**
> The Google Tasks Sync addon (see [this link]("https://code.google.com/p/gt-tasks-sync/")) is too new to be on the Mozilla site yet, but I installed it manually into TB and it works fine.

I've tried this without success.   I believed that using this link to install the add on, I would be able to use the TB task icon/tab to use the Task function.  Also, after saving the download, windows cannot install.  Is this what you have experienced?

---

