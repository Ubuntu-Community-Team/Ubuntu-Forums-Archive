---
title: "Google Voice and Ubuntu"
date: 2011-01-20
forum: General Help
---

### Post by Consecrated on 2011-01-20
Hello all,

The ultimate goal is to have some Gnome Panel Applet that performs the same functions as the [Google Voice Extension]("https://chrome.google.com/extensions/detail/kcnhkahnjcbndmmehfkdnkjomaanaooo") for Google Chrome and the built in Gmail utility for calling and receiving calls through Google Voice. Ideally this applet would have notifications displayed in Ubuntu's Notification Area announcing Incoming Calls and Texts (contact name and content of text message). Another possible implementation could be using [Google's Desktop Gadgets ]("http://desktop.google.com/plugins/search/?query=google+voice&hl=en"), but thus far no one has developed such an application.

I have found some solutions for this objective:

1) [GoogleSysTray]("http://www.omgubuntu.co.uk/2010/06/googsystray-1-2-0-released-adds-previews-new-features/") [1.3.1]("http://sourceforge.net/projects/googsystray/files/")
"Googsystray is a system tray app for Google Voice, Gmail, Google Calendar, Google Reader, and Google Wave. The idea is to be able to keep track of all that stuff without having to keep a bunch of browser tabs open, or constantly checking them."
The updated 1.3.1 version works excellent and is exactly what I was looking for! (Well, except for the gmail calling utility.) Check it out!

2) [Gvoice-Nofitier]("http://www.omgubuntu.co.uk/2010/06/add-google-voice-alerts-to-the-ubuntu-messaging-menu/")
"Thanks to the work of Ken Van Dine you can now receive instant notifications of new voicemail, SMS&#8217;s and other Google Voice messages directly to your desktop via the Ubuntu messaging menu."
sudo add-apt-repository ppa:ken-vandine/notifiers
sudo apt-get update && sudo apt-get install gvoice-notifier
This is the second best solution. I am notified when a new text comes in, however I have to view the website to actually read it or see who it is from. Not ideal by anyones standards.

Please reply with other solutions or integrations bringing the functionality of Google Voice to Ubuntu.

Thanks!

---

