---
title: "Screen tearing"
date: 2012-02-16
forum: General Help
---

### Post by janderson91z on 2012-02-16
I'm using the open source ati driver in Xubuntu and everything works flawlessly except i'm getting screen tearing. I can notice it when dragging around windows and more importantly in VLC when trying to watch videos.

Is there a way I can turn on vsync with the open source ati driver in xubuntu or something? Thank you.

Edit: I also noticed that with compositing turned off I don't have any tearing.

---

### Post by Grenage on 2012-02-16
Are you unable to use the proprietary driver?  The control centre used to have an anti-tear feature which you can enable?

---

### Post by Jose Catre-Vandis on 2012-02-16
Try turning compositing off.

You can do this from the command line and / or create a launcher to turn it on and off if this is the problem.

To turn off
```
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=false
```

To turn on
```
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=true
```

---

### Post by lildigiman on 2012-02-16
I had the same issue with the open source driver and tried several things to remedy this. However the only successful option was switching to the proprietary AMD/ATI driver which has an option for fixing the tearing.

---

### Post by janderson91z on 2012-02-17
Thank you for responding guys.

Yeah, the ATI proprietary driver does fix this issue. I forgot to mention that. However when I use the ATI driver I can't enable my second monitor to extend the desktop. It only mirrors. When I try to extend it just closes out the AMD control center and doesn't change anything.

And yes Jose, turning off compositing works but I like using compositing =/

Currently I just have it turned off to resolve the issue but I would love to be able to use it with the ATI driver but the multimonitor issue is holding me back.

---

### Post by janderson91z on 2012-02-19
Alright guys, I wanted to post that after searching and trying a few methods I was able to get dual monitors working in Xubuntu with the AMD proprietary driver by adding a line to the xorg.conf

```
Option "Xinerama" "on"
```

If someone would like to explain to me what this is and why it's working I would love to know what this is doing.

However, I have a new issue now. Everything is working perfectly BUT, now when I go into the XFCE settings panel and turn on the compositor, I hit the check box and nothing happens. The compositor doesn't turn on, despite the box being checked. I would love to have the compositor on with the tear free desktop. I like having opacity on the panel.

Thank you.

---

### Post by Grenage on 2012-02-20
Greetings;

Xinorama is an X extension which basically just allows you to display a desktop across multiple displays.  I've seen other people complain about compositing and xinerama not working together; so it's probably common.  It may be worth having a search for "xinorama compositing", as that seems to bring up a fair few things to try.

I only use Nvidia (with twinview), so I have no means to dabble here.

---

