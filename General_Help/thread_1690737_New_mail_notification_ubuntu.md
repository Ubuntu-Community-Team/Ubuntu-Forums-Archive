---
title: "New mail notification ubuntu"
date: 2011-02-18
forum: General Help
---

### Post by darthpenguin on 2011-02-18
Okay, I know this is a question that has been asked in the forums before but I just haven't found a solution that works for me. So, I'm going to ask again. Sorry. Is there a good email notification solution for Linux? I know there are many options like browser plugins and such. But all I want is a monochrome icon in the notification area that indicates when new mail arrives (don't even need to see an unread count). I've tried all kinds of solutions but the only thing that comes close is gm-notify and checkgmail. gm-notify only works with the indicator-applet-message menu (I don't like the indicator applet and don't want to use it). And checkgmail looks terrible in the notification area. There is no transparency around the icon so it is really out of place in the tray. Both these apps only work for gmail. As that is the service I use that's not a big deal for me, but what about everyone who uses other services? What do they use? It's ridiculous that Thunderbird does not run in the tray by default. I mean, isn't that the point of an email client or am I missing something? I can use the firetray addon but it is not elegant. When you get mail the icon changes to an ugly box and show a count of new messages. Again, I don't need a count. Isn't there a way to get a mail icon in the tray that turns green or something when I get mail? is it too much to ask? Don't mean to rant but it seems like a necessary feature. I mean Ubuntu 10.10 came with the indicator-applet-message menu but even that only informed you of new mail *if* the mail client was open COMPLETELY defeating the purpose of having it in the system tray in the first place.

Anything we can do about this?

Many Thanks.

---

### Post by Frogs Hair on 2011-02-18
I have not used this , but it works from a tray icon and with multiple mail boxes.[http://linux.softpedia.com/get/Communications/Email/Mail-Notification-3483.shtml](http://linux.softpedia.com/get/Communications/Email/Mail-Notification-3483.shtml)

---

### Post by darthpenguin on 2011-02-18
I've tried mail-notification before. I just don't understand how it works. I don't see an icon in the panel. does an icon appear only when it finds unread messages? what's so hard about keeping an icon in the tray at all times and changing the icon when mail arrives?

---

### Post by sabbs666 on 2011-02-19
Gmail notifier will use panel indicators and set up is easy of all the options this i8s my personal preference.

---

### Post by pqwoerituytrueiwoq on 2011-02-19
```
sudo apt-get install mail-notification
```
and ```
mail-notification -sm-disable
``` to startup
to start it for the 1st time it is under internet in the applications menu
an icon will appear in the panel when you get mail
mail-notification is also under preferences for configuration

---

### Post by Krytarik on 2011-02-19
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get install mail-notification
```and ```
mail-notification -sm-disable
``` to startup
to start it for the 1st time it is under internet in the applications menu
an icon will appear in the panel when you get mail
mail-notification is also under preferences for configuration
You have to add it's PPA before to make the commands work:
[https://launchpad.net/~mail-notification-ssl/+archive/ppa](https://launchpad.net/~mail-notification-ssl/+archive/ppa)

But since it requires an additional install of 76 MB of packages, I didn't tried it.

---

### Post by Zill on 2011-02-19
> **darthpenguin said:**
> I've tried mail-notification before. I just don't understand how it works. I don't see an icon in the panel. does an icon appear only when it finds unread messages? what's so hard about keeping an icon in the tray at all times and changing the icon when mail arrives?
Mail-notification *can* be configured to show an icon at all times.

Simply open the [GConfEditor]("https://help.ubuntu.com/community/GConfEditor"), select "apps" and "mail-notification" then set the value for "always-display-icon" to true.

---

### Post by darthpenguin on 2011-02-20
> Simply open the GConfEditor, select "apps" and "mail-notification" then set the value for "always-display-icon" to true.

Ah ha. Thanks. That works. I still don't understand why I have to jump through hoops to accomplish this. I don't even get why a separate app is required to notify a user of new email. It's not just Thunderbird either. Evolution doesn't sit in the tray either. If someone has to manually check an email client then they might as well just open a web browser and pull-up webmail. I'm not saying there is anything really wrong with that. I'm just saying that without system tray notifications there is absolutely no good reason whatsoever to even bother with an email client. But the developers insist I use a separate notifier program... fine, ok. Now the notifier doesn't show in the tray at all times, wtf, how is the user suppose to know it is running? sure you can keep it showing if you toggle a hidden config option. But it's as if the developers don't expect users to want an email icon in their tray. WHY NOT?! sorry.. this just bugs me.

Thanks for the fix.

---

### Post by allergygorilla23 on 2011-02-20
Hi guys, let me ask you something, i'm using gmailcheck and it works perfectly, but i want it to check my mail when i click on the icon (left click). I know you can set up a command on icon click but i just don't know what the command is to update the unread count. I've tried with GetUnread(),  CheckGMail() and UpdateList() and nothing works. Could you please give me a hand?

Thanks!

---

### Post by Zill on 2011-02-20
> **darthpenguin said:**
> ... But it's as if the developers don't expect users to want an email icon in their tray. WHY NOT?!...
Err, sorry but *I* don't really want a permanent icon in my tray telling me I have no mail ;-)  All I want is an icon to appear showing if I *have* new mail.

Still, Linux is all about choice and so your preferences can be different to mine and we can both be happy :-)

---

### Post by darthpenguin on 2011-02-20
> **Zill said:**
> Err, sorry but *I* don't really want a permanent icon in my tray telling me I have no mail ;-)  All I want is an icon to appear showing if I *have* new mail.

Still, Linux is all about choice and so your preferences can be different to mine and we can both be happy :-)

Of course, your right. Sorry, I didn't mean to rant. Software should be about choice. It seems odd to me that the *default* option is no icon. But that could be a bias view based on personal preference. At the very least there could be a toggle in the preferences instead of fudging around in gconf. Not saying that a computer system should (or could) have a setting for every possible user preference but this particular one is not exactly unpredictable. I'd guess this is a feature that a significant number of users would want.

---

### Post by darthpenguin on 2011-02-22
While the solution posted by Zill worked it still was not as clean as I would like (didn't much like the icon either). So I have gone in a different direction. 

I have bit the bullet and installed the indicator applet. It takes a bit to get use to and I had to dump a few apps that are not supported by the applet. I'm using the indicator-applet-complete which includes the datetime component and installed the indicator-network package thus allowing me to dump the notification area completely. I refuse to run both at once. with gm-notify installed and evolution-indicator removed I now have a clean email notification experience. The indicator-network is in beta and is buggy but I can manage my network connection from the command line if needed.

if you need mail notification AND you have a gmail account here is your solution:

> apt-get install indicator-applet indicator-applet-complete indicator-network gm-notify && apt-get remove evolution-indicator

remove notification-area and clock from gnome-panel and add indicator-applet-complete. run gm-notify-config and set it up (easy to use, self explanatory). logout/login. done.

if you don't have gmail follow instruction from Zill in this thread. I'll mark this thread as "solved". though it is far from an elegant solution unless you have a gmail account. And even then gm-notify is stuck in the indicator-message menu. It's the rhythmbox-in-the-sound-menu all over again. Why can't apps have there own notification icons instead of hiding in menus? I switched to banshee *only* because it can have an icon in the tray independent of the sound menu.

Again, don't mean to rant. Just looking for the best UI experience possible. Besides, what's the alternative? Switch to Windows? Forget that noise.

---

