---
title: "Email Notification -- HOW?!"
date: 2011-10-23
forum: General Help
---

### Post by darthpenguin on 2011-10-23
Hi all.

I hope this doesn't turn into a rant. That is not my intention.

Any help the community can provide would be greatly appreciated.

Back in my Windows 95/98 days I had email programs -- either Incredimail or Outlook or both -- that had a certain feature. They would sit in the system's notification tray next to the clock and notify me when I had mail. This seems extremely simple and -- in my mind -- should be the default behavior of all email clients. Yet I can't find an email program anywhere on any system that does this anymore.

Ubuntu has the Message Menu but it will only indicate new mail if Thunderbird is open. If I need to think to open Thunderbird before the indicator can remind me to do so then the message menu becomes completely redundant. Sure, I can open Thunderbird and minimize it to the Unity launcher (even add Thunderbird to the startup applications) but it just becomes an extra program to alt-tab through. Also I need to be careful when using Thunderbird and always be sure to click the minimize button since closing the window (red X) also closes the program. This behavior makes sense in many programs but since an email application should be running at all times it becomes an inconsistency in the user experience. Basically Thunderbird should behave exactly as Empathy and Gwibber ie. closing the window doesn't stop the service/program.

I've looked into Gnome-Shell and KDE and neither seem to have this feature. Evolution doesn't show in Gnome's system tray (actually I don't understand Gnome-Shell's system tray at all). And K-Mail doesn't close to the tray either (yet KDE has a tray applet for the clipboard... WTF?). Seriously I'll switch desktop environments, distros, even whole operating systems just for this feature alone.

Windows 7 doesn't have this feature either. It's built-in email client use to hide in the tray in Vista but it won't do it in 7. Thunderbird use to have an add-on to hide in the tray but even that didn't work for me because the icon in the tray wouldn't change color or flash or do anything to let me know I had email.

The only system that gets it close to right is Apple. both Mail and Thunderbird stay in the dock (opened) even after the user closes the window (of course, all applications on Mac do that which can be a bit annoying depending on the app). The mail clients will show a badge over the icon not only indicating that you have mail but how many unread emails you have in your inbox. Still I'd like to see apps like Adium and iChat and Email clients move from the Dock to the system try in the upper right. Am I the only person who thinks that makes sense?

Basically I need something that actually indicates to me that I have email (that I received email while I was away from my computer or while it was off) regardless of whether my email client is open or not. Ideally something that works for Ubuntu but I'm open to anything.

I have installed gm-notify but that only works for gmail. I have other email accounts. and it looks out of place in the message menu (install it and you'll see what I mean).

I found this python script here [http://conjurecode.com/create-indicator-applet-for-ubuntu-unity-with-python/]("http://conjurecode.com/create-indicator-applet-for-ubuntu-unity-with-python/") which seems like a good start at creating an indicator applet for checking mail outside of the message menu. It needs a lot of work like a graphic interface for setting up email accounts and the ability to launch the default mail application when clicked. I'm not a programmer so any help would be appreciated.

I boggles the mind that this is so hard to do. I have set up my accounts on my Android smart phone so I can get email on the go. It works great it notifies my when I have mail and keeps an icon in the top bar until I open the message just like a text -- brilliant. I currently keep my phone on the desk next to my computer because without it I'd never get my emails. I seriously wait for my phone to buzz before I open Thunderbird.

What is the thought process behind this? Why have all the systems pulled email notification out of the system trays? I don't get it.

I'll subscribe to this thread with 'instant email notification' we'll see how well that goes. :)

---

### Post by jon zendatta on 2011-10-23
You didn't indicate what email service you use IMAP or POP! For Gmail, I use mail-notification
```
sudo apt-get install mail-notification
```
:KS

---

### Post by darthpenguin on 2011-10-23
mail-notification is not showing an icon in the indicator applet. It is creating a pop-up window telling me I have mail. Clicking open opened nautilus for some reason and then firefox with the gmail web interface. I want to open messages in a client like thunderbird. Also I'm getting one pop-up window for each message so if I leave my computer for any length of time I'll come back to a desktop covered in what looks like (but isn't I know) error messages (Windows ME flash back). If I get 20 messages that's 20 message boxes I need to close. so not quite what i'm looking for. Am i using it wrong? Thanks for your help though.

---

### Post by pretty_whistle on 2011-10-23
> **jon zendatta said:**
> You didn't indicate what email service you use IMAP or POP! For Gmail, I use mail-notification
```
sudo apt-get install mail-notification
```
:KS

In my case I'm POP3ing gmail accounts.  Will the notification you're speaking of work to place an icon on the notification area when I have new unread email?

---

### Post by pretty_whistle on 2011-10-23
I bet in my case it will fail because I installed Thunderbird manually without using the Software Center.

Darn.

Edit:

I tried it.  It didn't work.  Oh well.
.
.

---

### Post by darthpenguin on 2011-10-23
Okay. I have found an answer. Believe it or not the minimizetotray revived (mintrayr) add-on works on ubuntu. While you don't actually see it minimize to the tray it is clear the application is still running after the window is closed because I'm getting notifications complete with badge on unity launcher libnotify popup and (most important) blue mail icon in indicator applet. also after the app has been started once it launches much faster every time it is opened. There is a small bug, the global menu ocationally stops working. That's about it.

---

