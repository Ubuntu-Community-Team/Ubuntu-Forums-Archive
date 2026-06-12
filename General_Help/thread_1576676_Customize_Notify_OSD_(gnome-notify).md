---
title: "Customize Notify OSD (gnome-notify)"
date: 2010-09-17
forum: General Help
---

### Post by raafaell on 2010-09-17
[SIZE="4"][LIST]
[*]Customize The Customization Bubble
[/LIST][/SIZE]
[IMG]http://filestatic.com/images/Screenshot.png[/IMG]

I found a way of customizing the Bubble that appears on the top right corner of you desktop.

By doing the following you will be able to change color, size, position, fade away time, icon size etc.. 

[SIZE="4"]Step 1[/SIZE]: First of All Open Your Terminal

[SIZE="4"]Step 2[/SIZE]: Add the PPA to the repository copy/paste in Terminal

```
sudo add-apt-repository ppa:leolik/leolik
```

[SIZE="4"]Step 3[/SIZE]: Now install the 'patched' Notify OSD, copy/paste in Terminal

```
sudo apt-get update && sudo apt-get upgrade
```

[SIZE="4"]Step 4[/SIZE]: Now you will create an Empty File called .notify-osd in the HOME folder, copy/paste in Terminal

```
gedit ~/.notify-osd &
```

[SIZE="4"]Step 5[/SIZE]: With the gedit opened, you will need to add the following, copy/paste in Terminal

```
slot-allocation = fixed
bubble-expire-timeout = 10sec
bubble-vertical-gap = 5px
bubble-horizontal-gap = 5px
bubble-corner-radius = 37,5%
bubble-icon-size = 30px
bubble-gauge-size = 6px
bubble-width = 240px
bubble-background-color = 131313
bubble-background-opacity = 90%
text-margin-size = 10px
text-title-size = 100%
text-title-weight = bold
text-title-color = ffffff
text-title-opacity = 100%
text-body-size = 90%
text-body-weight = normal
text-body-color = eaeaea
text-body-opacity = 100%
text-shadow-opacity = 100%
```

[SIZE="4"]Step 6[/SIZE]: Now customize it, then Save and Close.

For Example: If you want the bubble to appear at the bottom right corner, change the slot-allocation value '**fixed**' to '**dynamic**'..

Do the following ```
gconftool-2 -s /apps/notify-osd/gravity --type=int [number]
``` With the number of position below:

1 - top-right corner
2 - middle-right
3 - bottom-right corner
4 - bottom-left corner
5 - middle-left
6 - top-left corner


Now to test your customization, do **notify-send test** in the terminal. You may need to install **libnotify-bin**, so do **sudo apt-get install libnotify-bin** to install it.

If you haven't see any changes, try to kill notify-osd, do **pkill notify-osd** in Terminal..


):P

---

### Post by begtognen on 2010-09-26
Thanks so much for posting this.

I was able to customize most of notify-OSD. I did run into some trouble here:

```
bubble-expire-timeout: 10sec
```

If I change it to anything else, it behaves as if I've set it to "never expire", and shows the first notification that comes up until I kill the process.

Any ideas what I'm doing wrong?

Or, alternately, is there a way to tweak notify-OSD so that the user must acknowledge seeing the bubble before it goes away? I use it primarily as a timer, and because it's only there for 10 seconds I'm prone to missing the notification.

Thanks so much for any suggestions/information you might have.

---

### Post by raafaell on 2010-09-26
> **begtognen said:**
> Thanks so much for posting this.

I was able to customize most of notify-OSD. I did run into some trouble here:

```
bubble-expire-timeout: 10sec
```

If I change it to anything else, it behaves as if I've set it to "never expire", and shows the first notification that comes up until I kill the process.

Any ideas what I'm doing wrong?

Or, alternately, is there a way to tweak notify-OSD so that the user must acknowledge seeing the bubble before it goes away? I use it primarily as a timer, and because it's only there for 10 seconds I'm prone to missing the notification.

Thanks so much for any suggestions/information you might have.

Mine is like this:
```
slot-allocation = dynamic
bubble-expire-timeout = 5sec
bubble-vertical-gap = 5px
bubble-horizontal-gap = 8px
bubble-corner-radius = 37,5%
bubble-icon-size = 36px
bubble-gauge-size = 6px
bubble-width = 300px
bubble-background-color = 131313
bubble-background-opacity = 50%
text-margin-size = 6px
text-title-size = 100%
text-title-weight = bold
text-title-color = ffffff
text-title-opacity = 100%
text-body-size = 90%
text-body-weight = normal
text-body-color = ffffff
text-body-opacity = 90%
text-shadow-opacity = 100%
```

use that for a test, and you must kill the notify to make changes...

---

### Post by begtognen on 2010-09-26
Interesting. If I use your code, it works just fine. (I made sure to kill the notify between changes.)

If I use your code, and change the expire to:

```
bubble-expire-timeout: 90sec
```Then it's like there's no timeout at all, and no new notifications ever happen.

---

### Post by begtognen on 2010-09-26
So I tried this (which is really just a graphical interface for the hack above):

[http://www.kabatology.com/06/02/customize-ubuntu-notification-bubbles-with-notifyosd-configuration/](http://www.kabatology.com/06/02/customize-ubuntu-notification-bubbles-with-notifyosd-configuration/)

And interestingly, using this you *can't* set it for more than 10 seconds. I wonder if it's even possible? I feel like the only freak who would like it to sit there for at least 2 minutes. *laughing*

---

### Post by begtognen on 2010-09-29
I found two great work-arounds.

1) For a timer, I'm using Tomboy, with the Reminder plugin.

[http://flukkost.nu/blog/tomboy-reminder/](http://flukkost.nu/blog/tomboy-reminder/)

2) To get my mail notifications to show up for more than 10 seconds:

Install Mail Notification.

To get Mail Notification to use Notify-OSD:

1. Run gconf-editor
2. Navigate to apps -> mail-notification -> popups
3. Delete all values for the 'actions' key

Now you *can* set it to expire in MORE  than 10 seconds, which is exactly what I wanted. (Be careful not to set  it *too* high; no other notifications can appear while that one's on the  screen.)

---

### Post by eudennis on 2011-03-10
Have any way to change the opacity when mouse is over the notify?

---

### Post by alperyilmaz on 2011-04-01
Is it possible insert a gauge into notification window? (just like in brightness and volume notifications)

---

