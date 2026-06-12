---
title: "Evo;ution - auto download setting?"
date: 2011-02-06
forum: General Help
---

### Post by MikePerryUK on 2011-02-06
Hi

I'm fairly new to Ubuntu and like evolution, except that I can't find how to set it to automatically download emails at set intervals - as is the norm in Outlook.  Is there a setting for this?
Thanks
Mike P

---

### Post by [Snc] on 2011-02-06
I don't use evolution mail, but this is what i googled up...

go to
preferences > receive
and set the time interval for automatic mail fetching...

---

### Post by MikePerryUK on 2011-02-06
Hi 

Sadly the page you found is incorrect.  There is no Preferences>Receive option on the dialog.  Nowhere can I find any setting for enabling automatic collection/receipt of emails - and I've been looking for the past three weeks!

Any solution that does not involve program code will be welcomed.

Thanks

MikeP

---

### Post by [Snc] on 2011-02-06
Well, which version of evolution are you using then?

---

### Post by [Snc] on 2011-02-06
These is from the evolution 2.30 faq....

> Receiving Options:
     Decide if you want to check for mail automatically and how often, as well as setting other message retrieval options.

```
[http://library.gnome.org/users/evolution/stable/config-prefs-mail-identity.html.en](http://library.gnome.org/users/evolution/stable/config-prefs-mail-identity.html.en)
```

[IMG]http://library.gnome.org/users/evolution/stable/figures/evo_gwreceive_a.png.en[/IMG]

also same info here:
[http://library.gnome.org/users/evolution/stable/usage-mainwindow-starting.html.en#more-mail-options](http://library.gnome.org/users/evolution/stable/usage-mainwindow-starting.html.en#more-mail-options)
[]("http://library.gnome.org/users/evolution/stable/config-prefs-mail-identity.html.en")

---

### Post by Zill on 2011-02-06
1  Click on menu Edit, Preferences
2  Click on Mail Accounts
3  Select your chosen account
4  Click "Edit" button (on right hand side)
5  Click on "Receiving Options" tab
6  Select "Check for new messages"
7  Set your desired time in minutes
8  Click "OK" button to close dialog
9  Repeat from 3) above for any other accounts
10 Close Preferences screen

---

### Post by MikePerryUK on 2011-02-06
I am using version 2.30.3.  Nowhere is there any dialog you show!  
Are you perhaps saying it is an 'add-on'?  If so, why is it not there in the first place and why is it not available as an addition that can be installed automatically from the Synaptic Package Manager?

Most new users do not want to fiddle about with code on a command line, so there should be more consideration given to user interactions and usability.  What you are showing is hardly inspiring to new users especially those who dislike (or have never tried) using a command line.

---

### Post by MikePerryUK on 2011-02-06
@Zill
Great, that should solve it for me.  Shame it's a bit 'hidden' as most users would not want to edit their mail account!  
Thanks.  I've selected the button (it was unchecked) and set the interval as I require, so I'll soon know if it works as hoped.
Thanks
Mike P

---

### Post by Zill on 2011-02-06
Mike:  I am glad you have now fixed the problem.  However, I am concerned that you do not seem to realise that [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm") and so you can't really expect things to work in the same way.  Lots of us have been using Linux for years as a sole operating system and find the Windows way of doing things quite alien!

You should also realise that, unlike Windows, Linux apps are largely developed and supported by volunteers who do their best to produce good apps.  On this basis, there *is* much "consideration given to user interactions and usability" but, at the end of the day, developers work on the things *they* want to.  As users, we cannot demand that "someone else" makes things easier for us!

Your earlier post stated that "Any solution that does not involve program code will be welcomed".  FWIW, Linux users are not expected to write "program code".  I suspect you are referring to the use of the short terminal commands scattered throughout these forums.  The advantage of using these short commands is obvious when you see the length of my post simply showing how to enable a simple option in Evolution.  This necessitated click-by-click instructions which are very tedious to describe.  Installing a program using a GUI would also be very cumbersome to describe but the same result is far quicker to show with a single line using terminal commands eg.
```
sudo apt-get install myprogram
```
Learning a few Linux terminal commands makes life far simpler and is well worth it.  However, there is often a GUI option if you want it.  Linux is all about choice.  Enjoy :-)

---

### Post by [Snc] on 2011-02-06
Another thing to know... 

Sadly, because of malware and hacking attempts, you should not lower the time between intervals to less then 10min or so (*get the recommended time from you email provider*), if you just set it to 1 minute, you could be banned for 24h (it happened to me once :{) and the worst part is, you probably will not even be notified ...

PS. Sorry, i couldn't be more directly helpful, i have limited experience with evolution ;)

---

