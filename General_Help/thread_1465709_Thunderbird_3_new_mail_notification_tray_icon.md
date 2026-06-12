---
title: "Thunderbird 3 new mail notification tray icon"
date: 2010-04-29
forum: General Help
---

### Post by empty_spaces on 2010-04-29
I'm using Ubuntu Lucid 64bit.
Thunderbird 2 had an add-on for new mail icon notification in the tray, but I haven't yet found a working replacement for Thunderbird 3.
Anybody have this working yet?

---

### Post by poliltimmy on 2010-04-29
I use alltray. It should be in the software center.

---

### Post by empty_spaces on 2010-04-29
> **poliltimmy said:**
> I use alltray. It should be in the software center.

Thanks for the suggestion. So if I use Alltray to display a tray icon for Thunderbird, will it display a new mail icon in the tray whenever new mail arrives?

---

### Post by poliltimmy on 2010-04-29
well....it worked in 9.10. I have not gotten any mail since my update an hour ago. So I do not know if the notification will pop up yet.

---

### Post by empty_spaces on 2010-04-29
> **poliltimmy said:**
> well....it worked in 9.10. I have not gotten any mail since my update an hour ago. So I do not know if the notification will pop up yet.

Just want to make sure we are not talking about 2 different things here.
The pop-up notifications are not what I'm looking for. I'm looking for a persistent tray icon that changes to indicate new mail.

Here is an image I found online that should clarify further

---

### Post by MavericNL on 2010-04-30
I am having the same trouble. In TB2 there was an addon to do this. This Addon doesn't work with TB3

---

### Post by sigurnjak on 2010-04-30
Try firetray extension. That is what i use .

---

### Post by IanMcBride on 2010-04-30
If you use Firetray with TBird 3, I'm pretty sure you have to use the 'firetray-0.2.5_dev.xpi' download.

I tried the 0.2.3 version initially and it completely hosed up my TBird.  I Google searched the issue and fount the development version, which so far has worked.

---

### Post by empty_spaces on 2010-04-30
> **sigurnjak said:**
> Try firetray extension. That is what i use .

Are you using firetray with Thunderbird 3 _and_ 64bit Lucid ?

Because I tried firetray 0.2.3 (stable) first and Thunderbird 3 kept crashing.
After some research, I then tried the development version (firetray 0.2.5_dev), and I was able to see the tray icon for Thunderbird 3, but no icon change when new mail arrived (Although the firetray preferences do have settings for new mail, they don't seem to work).

---

### Post by sigurnjak on 2010-04-30
Sorry dude ! 32bit  here:(

---

### Post by kolinab on 2010-05-01
Thanks for this information on FireTray. I tried alltray and didn't like the fact that I lost my new mail notification icon in the system tray. 

Too bad the old moztraybiff doesn't work with TB3 - I still liked its simplicity best.

I also found MinimizeToTray Plus . . . [https://addons.mozilla.org/en-US/firefox/addon/2831](https://addons.mozilla.org/en-US/firefox/addon/2831). I like how it maximizes T-bird with a single click instead of doing the mouse roll thing. But unfortunately it doesn't seem to leave a persistent icon in the tray when I have new mail. I guess I will stick with FireTray. Anyone know how to configure it to maximize tbird with a single click on the system tray icon?

---

### Post by smokey_58au on 2010-05-03
I upgraded to Lucid (64bit) yesterday and found this Add On when digging around:

[http://reformedmusings.wordpress.com/2010/05/01/thunderbird-message-notification-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/01/thunderbird-message-notification-in-ubuntu-lucid-10-04-lts/)

I followed the instructions and it works for me.  Pretty simple and could do with some features to spruce it up but it does the job.  What the link above doesn't mention is that you need to add Thunderbird by going to System > Preferences > Mail Notification and on the General tab choose Autodetect for Mailbox Type and then browse to the location of your Thunderbird inbox.  For example, mine is: "file:///home/rob/.thunderbird/idpo1mge.default/Mail/Local%20Folders/Inbox".  Once I did that it all worked and then the last thing I had to do was stop Thunderbird sending its own sound/pop-up notifications because they were now duplicated.

---

### Post by sigurnjak on 2010-05-04
> **kolinab said:**
> Thanks for this information on FireTray. I tried alltray and didn't like the fact that I lost my new mail notification icon in the system tray. 

Too bad the old moztraybiff doesn't work with TB3 - I still liked its simplicity best.

I also found MinimizeToTray Plus . . . [https://addons.mozilla.org/en-US/firefox/addon/2831](https://addons.mozilla.org/en-US/firefox/addon/2831). I like how it maximizes T-bird with a single click instead of doing the mouse roll thing. But unfortunately it doesn't seem to leave a persistent icon in the tray when I have new mail. I guess I will stick with FireTray. Anyone know how to configure it to maximize tbird with a single click on the system tray icon?



I just scroll mouse wheel to maximize/minimize thunderbird window in to a tray icon  . 
It works well here .

---

### Post by empty_spaces on 2010-05-04
> **smokey_58au said:**
> I upgraded to Lucid (64bit) yesterday and found this Add On when digging around:

[http://reformedmusings.wordpress.com/2010/05/01/thunderbird-message-notification-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/01/thunderbird-message-notification-in-ubuntu-lucid-10-04-lts/)

I followed the instructions and it works for me.  Pretty simple and could do with some features to spruce it up but it does the job.  What the link above doesn't mention is that you need to add Thunderbird by going to System > Preferences > Mail Notification and on the General tab choose Autodetect for Mailbox Type and then browse to the location of your Thunderbird inbox.  For example, mine is: "file:///home/rob/.thunderbird/idpo1mge.default/Mail/Local%20Folders/Inbox".  Once I did that it all worked and then the last thing I had to do was stop Thunderbird sending its own sound/pop-up notifications because they were now duplicated.

Just to be clear, this addon uses the built in notifications in Ubuntu, but it did not provide me with a **persistent tray** icon for new mail, which is basically what I'm looking for.
Or am I missing something here?

(Note: As per the instructions, I built the xpi from source, installed it, and played around with the settings, but no persistent new mail tray icon)

---

### Post by smokey_58au on 2010-05-04
Then I'm not sure what you're after.  In my environment, the solution I referred to gives me a mail (envelope) icon that appears in my system tray when I receive mail, next to my Bluetooth Indicator, Network Indicator, Skype Indicator, Dropbox Indicator etc etc.  It has a number in the bottom right corner of the mail icon that lists the number of unread emails in my inbox.  This icon stays until I acknowledge it's presence by right clicking and choosing to mark all mails as read etc.  In addition, I also get the (partly) transparent widget window that appears each time there is new mail and displays some attributes of each email in my inbox (subject, from, time received etc) but this only displays for a few seconds before fading away.  I thought from your initial post that this was something similar to what you were after?

---

### Post by empty_spaces on 2010-05-04
> **smokey_58au said:**
> Then I'm not sure what you're after.  In my environment, the solution I referred to gives me a mail (envelope) icon that appears in my system tray when I receive mail, next to my Bluetooth Indicator, Network Indicator, Skype Indicator, Dropbox Indicator etc etc.  It has a number in the bottom right corner of the mail icon that lists the number of unread emails in my inbox.  This icon stays until I acknowledge it's presence by right clicking and choosing to mark all mails as read etc.  


Yup, that is exactly what I am after.
Btw, thanks for taking the time to spell it out in detail. It gave me some idea as to what I can expect from this addon.

Your post got me thinking about why I wasn't seeing all the things you mentioned.
Then I remembered having run the **sudo aptitude remove indicator-messages** command a few days ago to get rid of the evolution envelope from the panel.
So I re-installed it back, got the envelope icon in the panel, and it was now monitoring Thunderbird and displaying a star when new mail arrived **(See screenshots)**

It seems to me that it is still not the same as what you are seeing since I don't get the number of unread messages, so any other advice is very welcome, but at least I'm seeing some new mail indication in the tray.

Also included is a screenshot of the addon manager and the preferences for this addon.

---

### Post by smokey_58au on 2010-05-05
> **empty_spaces said:**
> Yup, that is exactly what I am after.
Btw, thanks for taking the time to spell it out in detail. It gave me some idea as to what I can expect from this addon.

Your post got me thinking about why I wasn't seeing all the things you mentioned.
Then I remembered having run the **sudo aptitude remove indicator-messages** command a few days ago to get rid of the evolution envelope from the panel.
So I re-installed it back, got the envelope icon in the panel, and it was now monitoring Thunderbird and displaying a star when new mail arrived **(See screenshots)**

It seems to me that it is still not the same as what you are seeing since I don't get the number of unread messages, so any other advice is very welcome, but at least I'm seeing some new mail indication in the tray.



OK, I can see where we differ now.  I'm not using the Evolution mail notification - mine is the "mail-notification" package (see screenshot).  I have it in my Startup Applications (see screenshot) and when any new mail comes in to my Thunderbird inbox (3 different accounts feed into the inbox) then an icon appears in my system tray (see screenshot) and the transparent widget temporarily displays the details of the new email(s).  In addition, if you hover over the icon you get a preview of the unread emails (see screenshot).

The only issue I have is that the counter of unread emails does not dynamically update if I mark the emails as read in Thunderbird so after I have read the new emails I manually update the tray icon by right clicking on it and choosing "Consider New Mail as Read" - the icon then disappears and reappears with the next new email received.  I have replied to the developer with this feedback so hopefully it will only be a short term issue but as I said originally, this works for me as it is.

Good luck and I hope this works for you!

---

### Post by empty_spaces on 2010-05-05
> **smokey_58au said:**
> 
The only issue I have is that the counter of unread emails does not dynamically update if I mark the emails as read in Thunderbird so after I have read the new emails I manually update the tray icon by right clicking on it and choosing "Consider New Mail as Read" - the icon then disappears and reappears with the next new email received.


I have a similar issue with my setup i.e. If I go to my thunderbird inbox _without_ clicking on the new mail tray icon, then the icon does not dynamically update when I mark the emails as read.
On the other hand, if I click on the new mail tray icon to go to my thunderbird inbox, the star on the tray icon immediately disappears.(See screenshot)

So I'm probably going to stick with my setup for now. Thanks for your help and feedback.

---

### Post by pinguy on 2010-05-13
I'm using 2 add-ons and 2 programs for Thunderbird.
Docky [https://launchpad.net/~docky-core/+archive/ppa](https://launchpad.net/~docky-core/+archive/ppa)
Docky Unread Count [https://addons.mozilla.org/en-US/thunderbird/addon/72199/](https://addons.mozilla.org/en-US/thunderbird/addon/72199/)
AllTray and adding a Startup Application entry with this 
```
**Name:**  Mozilla Thunderbird Mail/News
**Command:** alltray "thunderbird %u"
**Comment:** Read/Write Mail/News with Mozilla Thunderbird
```
Libnotify for Mozilla [https://launchpad.net/libnotify-mozilla](https://launchpad.net/libnotify-mozilla)

---

### Post by Exterminator13 on 2010-06-01
I've successfully compiled the latest version of Fire Tray 0.2.7.2 
for Kubuntu 10.04 LTS AMD64.
Take it and enjoy!

In mail client choose Tools - Add-ons - Extensions - Install.
After extension installed, select it and in Preferences select "Start program minimized on start..."
In System Settings (if you use KDE) go to Advanced - Autostart and set Thunderbird to start on system start-up.

---

### Post by scouser73 on 2010-06-01
Use the add on FireTray which will sit in the system tray and notify you when you've received an email.

---

### Post by EddieNYC on 2010-06-18
After reading this thread I have a question that was not covered.

Do the mail clients have to be open for most of these tray mail notifiers ?

I am new to Ubuntu and I just installed Thunderbird and miss the functions of Evolution via the envelope in the tray (compose, notification, etc).

I cant seem to find a way to make the envelope work with Thunderbird the same way (and not have to have the client open/running).

Anyone ?

---

### Post by pt123 on 2010-06-19
have you tried this
[http://www.gnomefiles.org/app.php?soft_id=2670#0.3.1](http://www.gnomefiles.org/app.php?soft_id=2670#0.3.1)
 Gnome Integration for Mozilla Thunderbird

---

### Post by Exterminator13 on 2010-06-20
> **EddieNYC said:**
> After reading this thread I have a question that was not covered.

Do the mail clients have to be open for most of these tray mail notifiers ?

I am new to Ubuntu and I just installed Thunderbird and miss the functions of Evolution via the envelope in the tray (compose, notification, etc).

I cant seem to find a way to make the envelope work with Thunderbird the same way (and not have to have the client open/running).

Anyone ?
I wasn't using Evolution, but I saw your point.
[http://code.google.com/p/firetray/downloads/list](http://code.google.com/p/firetray/downloads/list)
go here and download firetray
Open Thunderbird, go to Tools -> Add ons -> Install and install firetray
In this tab select Preferences for add-on you just installed, set "Start program minimized"
In KDE go to System Settings, Advanced tab, Autostart -> Add program and set "thunderbird" to start up.
After these steps you will receive:
- thunderbird start-up in tray on boot
- mail notification
- get new messages/create new messages feature.

---

### Post by omniphil on 2010-07-13
When I try to use any newer firetray extension including this one from the .zip here, I get an error telling me

"Firetray could not be installed because its not compatible with Thunderbird 3.1"

10.04 64bit here...

> **Exterminator13 said:**
> I've successfully compiled the latest version of Fire Tray 0.2.7.2 
for Kubuntu 10.04 LTS AMD64.
Take it and enjoy!

In mail client choose Tools - Add-ons - Extensions - Install.
After extension installed, select it and in Preferences select "Start program minimized on start..."
In System Settings (if you use KDE) go to Advanced - Autostart and set Thunderbird to start on system start-up.

---

### Post by mike555 on 2010-07-13
You can just open the file in file roller then open the install.rdf file and change the Thunderbird max version to 3.1 ..... save ... then install in Thunderbird ... worked for me ..

---

### Post by omniphil on 2010-07-13
Haha! that was incredibly easy and I learned something today!

> **mike555 said:**
> You can just open the file in file roller then open the install.rdf file and change the Thunderbird max version to 3.1 ..... save ... then install in Thunderbird ... worked for me ..

---

