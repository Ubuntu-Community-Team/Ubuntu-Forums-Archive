---
title: "what notifications is this, and how do i keep it as default?"
date: 2011-07-07
forum: General Help
---

### Post by teklife on 2011-07-07
i normally get the black osd-notify notifications on my gnome desktop, the ones that are NOT interactive. on occasion, i have seen these alternative notification "bubbles" appear, but i do not know how to set them as the default notifications, or what they're called even. 

since they re-appeared again, i have submitted a screen capture so you can see what i'm talking about; it's the notification bubble at the top right which shows an incoming IM which says, "test", and shows a close window button, a "show" button, and a countdown timer as well as a photo or my IM buddy's icon! 

even though these notifications are not as pretty as growl or osd-notify, they are at least more functional than any other notification system i've seen/used yet on ubuntu/gnome, and i'd like to have them as the default notification all the time. 

they're working now, but will only be on until the next reboot, which i must do frequently since i am traveling. can anyone tell me how to set these notifications as default??

---

### Post by teklife on 2011-07-13
anyone?

---

### Post by teklife on 2011-07-27
no one knows this?? not even how to tell me how to figure out what it's called or how to make these notifications active? come on, am i being ignored because this is too simple? if it's so simple, just tell me the name of them, and i can try and google the rest. please.

---

### Post by Habitual on 2011-07-28
This may help.
[http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html](http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html)
or
[http://www.ubuntugeek.com/notifyosdconfig-simple-gui-for-customizing-notifyosd.html](http://www.ubuntugeek.com/notifyosdconfig-simple-gui-for-customizing-notifyosd.html)

Although you haven't specifically said what type of osd "bubble" you prefer or under what condition(s).

---

### Post by teklife on 2011-07-28
thanks habitual, but those links are for the default ubuntu notify osd notifications, and although they tell you how to modify their appearance, they're still the regular "click through" notifications. in other words, not interactive. 

the yellowish notifications that i sometimes get, act much more like growl on os x, but even better. there's a countdown timer, a close button, and a "show" button. furthermore, if you click anywhere on the main balloon part of the notification (except the "show" button), it disappears, you don't need to click the X to close it. that, in my opinion, makes this notification a bit better than growl. i have no idea how i got it, or how to make it come back, but every now and then, i get these notifications, and they stay until the next reboot, when it then goes to the normal ubuntu osd notify, or wotever it's called. 

i hope someone else has seen these before. i'm starting to think it's an anomaly on my computer, but i'm sure it's not.

---

### Post by Habitual on 2011-07-29
Well, I tried.
I believe those yellowish notifications are a result of an IM program and controlled by the same.

There is probably a way to investigate that possibility, but I am not deeply familiar with such things as dbus which is what I think the mechanism is to display such things.

you could try in terminal: 
```
dbus-monitor
```

to watch for possible activity related to IM interaction.

Sorry, I wish it was more.

---

### Post by teklife on 2011-07-29
thanks, i appreciate it. i wont rule out that it's related to an IM program (pidgin in my case), but there is a notifications system related to it already which i know how to control. also, you can see in my last screen grab, that it gives more information than just IM program notifications- such as the network connections, batttery state, etc. 

i will check the dbus monitor. thanks.

---

### Post by teklife on 2011-09-11
turns out it is the default gnome notifications. much better than the nearly useless notify osd, which is a step backwards, imho.

[http://ubuntuforums.org/showpost.php?p=8559795&postcount=8](http://ubuntuforums.org/showpost.php?p=8559795&postcount=8)

how did no one know that??

---

### Post by 3rdalbum on 2011-09-11
> **teklife said:**
> turns out it is the default gnome notifications. much better than the nearly useless notify osd, which is a step backwards, imho.

Look at how many notifications are on the screenshot posted, and tell me with a straight face that Notify-OSD isn't better :-)

Actually, the theory is that with notifications that can be closed, you feel a compulsion to close them, thus interrupting your concentration. With notifications that can't be closed, you don't even feel that you need to close them. It's a strange psychological trick, but it really works for most people.

---

