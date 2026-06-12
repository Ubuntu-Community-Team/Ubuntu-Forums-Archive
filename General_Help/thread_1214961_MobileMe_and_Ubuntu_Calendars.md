---
title: "MobileMe and Ubuntu Calendars"
date: 2009-07-16
forum: General Help
---

### Post by JustinAlf on 2009-07-16
I refuse to believe that there is no way for me to "at least" view my MobileMe calendar in either Evolution or Thunderbird.

Mobileme states that it's mail cannot be used in applications other than Outlook or Mac, however, I have imported it into both thunderbird and evolution.

There has to be a URL for CALDAV or WEBCAL that I am not able to figure out.  I need calendars on my Ubuntu machine!  Please help if you have any ideas.  Thanks.

---

### Post by JustinAlf on 2009-07-20
bump

---

### Post by Andrew_Read on 2010-12-08
Hello,

The following is an extract from a website I am building, good luck!


Calendars stored on MobileMe can be viewed through some applications which Apple does not support, you can use Evolution Calendar supplied with Ubuntu 10.10, Evolution 2.30 . Versions of Evolution supplied with earlier releases of Ubuntu will not work with MobileMe Calendars, please note that there is an issue which I have identified. Calendar viewing and editing works mostly within Evolution with one exception, if you delete and event on me.com or any other device you are using MobileMe Calendars with, Evolution will not reflect the deletion. Where you have deleted an event outside of Evolution you will have to delete that event within Evolution also, this will display an error dialogue after which the event is deleted from Evolution.

In the following example I will demonstraite how to add a MobileMe calendar to Evolution, this will me my “ Home ” calendar.

From Evolution's Calendar click the “ New Calendar... ” underneath the caledar list on the left hand side of the window.
In the “ New Calendar ” dialogue which appears enter the following: 

Type:	 CalDAV 
Name:	 What ever you like, in this example I will call it “ MobileMe - Home ” . 
Copy calendar contents locally for offline operation	 If you want! 
Mark as default calendar	 It's your choice, you probably do want this. 
URL:	 caldav://cal.me.com/principals/ 
Use SSL	 Yes 
Username:	 Your MobileMe e-mail address excluding “ @me.com ” . 

With the “ New Calendar ” dialogue filled in click the “ Browse server for a calendar ” button, you will be prompted for your MobileMe password, you will then see a list of calendars you have available from your MobileMe account, select the one you want which in this example is “ Home ” then click “ OK ”.
In the “ New Calendar ” dialogue click OK, your calendar is now available in Evolution. Follow the same steps to add your other MobileMe calendars as you wish.

---

### Post by TWO on 2011-10-26
> **Andrew_Read said:**
> Hello,

The following is an extract from a website I am building, good luck!


Calendars stored on MobileMe can be viewed through some applications which Apple does not support, you can use Evolution Calendar supplied with Ubuntu 10.10, Evolution 2.30 . Versions of Evolution supplied with earlier releases of Ubuntu will not work with MobileMe Calendars, please note that there is an issue which I have identified. Calendar viewing and editing works mostly within Evolution with one exception, if you delete and event on me.com or any other device you are using MobileMe Calendars with, Evolution will not reflect the deletion. Where you have deleted an event outside of Evolution you will have to delete that event within Evolution also, this will display an error dialogue after which the event is deleted from Evolution.

In the following example I will demonstraite how to add a MobileMe calendar to Evolution, this will me my “ Home ” calendar.

From Evolution's Calendar click the “ New Calendar... ” underneath the caledar list on the left hand side of the window.
In the “ New Calendar ” dialogue which appears enter the following: 

Type:     CalDAV 
Name:     What ever you like, in this example I will call it “ MobileMe - Home ” . 
Copy calendar contents locally for offline operation     If you want! 
Mark as default calendar     It's your choice, you probably do want this. 
URL:     caldav://cal.me.com/principals/ 
Use SSL     Yes 
Username:     Your MobileMe e-mail address excluding “ @me.com ” . 

With the “ New Calendar ” dialogue filled in click the “ Browse server for a calendar ” button, you will be prompted for your MobileMe password, you will then see a list of calendars you have available from your MobileMe account, select the one you want which in this example is “ Home ” then click “ OK ”.
In the “ New Calendar ” dialogue click OK, your calendar is now available in Evolution. Follow the same steps to add your other MobileMe calendars as you wish.

I would say that "I hate to resurrect an old thread"...but I'm not! Firstly, I thank you for this input, even though it was over a year ago that you wrote this.

However, what I am curious about, is how you managed to work out the caldav URL for mobileme. I'm wondering if you have any idea what it might be for iCloud calendar?

Thanks in advance

TWO

---

### Post by David Crockett on 2011-12-22
Has anyone worked it out for iCLOUD?    I have not been able to figure it out .   I recently migrated to iCLOUD from MobleMe since that service is going away.

The thing that really troubles me is that the iDisk is going way too.   It works better with Ubuntu 11.10 than it does on the Apple.

Cheers,
DC

---

