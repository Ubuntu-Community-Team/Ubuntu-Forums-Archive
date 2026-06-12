---
title: "Keyboard Indicator Problem in Ubuntu 10.10"
date: 2010-10-10
forum: General Help
---

### Post by tareq.mhd on 2010-10-10
I have installed Ubuntu 10.10 64-bit. But it has a problem. Keyboard indicator does not showing layout. Look at the picture. Now tell me what can I do ?

[img]http://img242.imageshack.us/img242/3595/selection045.png[/img]

---

### Post by The Bright Side on 2010-10-10
Hey,

do you have more than one layout installed?
Otherwise the indicator won't show. Don't know how to make it show when only one layout is installed.

M.

---

### Post by tareq.mhd on 2010-10-10
There are two indicator, one is for Bangla and another is for English.

---

### Post by yacine on 2010-10-10
Right click on top Panel; chose Properties. Click on "Keyboard Indicator" and Add.
You're set!

---

### Post by tareq.mhd on 2010-10-10
But there is no "Keyboard Indicator" option in the Add to Panel.

---

### Post by The Bright Side on 2010-10-10
Huh. Yeah that's really strange. When I installed Maverick today, I went to System => Preferences => Keyboard, then selected the "Layouts" tab and clicked on "Add" to install the US keyboard layout along with my default German one. As soon as I installed it, the indicator popped up on my top panel.

Do you have the sound and mail indicator on your panel? Because all three are part of the "Indicator Applet", which can be found as package "indicator-applet" in Synaptic.

I know that the sound indicator's package is called "indicator-sound", the messaging indicator is "indicator-messages". Not really sure what the name of the keyboard indicator package is, though.

In any case, perhaps there's something missing there in your system.

It's true though, I can't add the keyboard indicator to my panel through the "add to panel" function either.

---

### Post by Kuzma86 on 2010-10-11
Installed 10.10 32bit yesterday. Once I added a different layout, a little keyboard icon appeared in the panel, but it has 0 use, as it just takes up space and would not show the language that is being used. Didn't have this problem in 10.04. Any help?

---

### Post by yesint on 2010-10-11
Just posted the same problem in separate thread. The indicator is useless. I have Cairo dock, so I'm using its native indicator istead, but this is not an option of course

---

### Post by arborrow on 2010-10-11
I was having the same problem and started playing around with the panel. When I added in the indicator panel it restored a keyboard with some letters next to it.

It does seem that having both the text and keyboard image is redundant. I'm just happy with the letters so that I can see which keyboard I am currently using so folks may be interested in:
[https://bugs.launchpad.net/ayatana-ubuntu/+bug/620331](https://bugs.launchpad.net/ayatana-ubuntu/+bug/620331)

If you are interested in seeing flags then check out:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/623435](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/623435)

This seems to be an area that was receiving some attention earlier ([https://bugs.launchpad.net/ayatana-ubuntu/+bug/621838](https://bugs.launchpad.net/ayatana-ubuntu/+bug/621838)) so hopefully things will get patched up.

Peace - Anthony

---

### Post by tareq.mhd on 2010-10-11
Problem solved, I had to reinstall indicator applet. Thanks all.

---

### Post by yesint on 2010-10-12
It is not that simple. You need an Indicator applet in the panel. But if I don't want to use it the notification area shows only the keyboard icon and nothing else.

---

### Post by october1917 on 2010-10-18
> the notification area shows only the keyboard icon and nothing else.Is that finally fixed or not?

---

### Post by The Bright Side on 2010-10-18
I don't think it's been solved. However, I had the same problem the other day, and I fixed it by moving the panel to the right of my desktop and then back up.

I think it could be related to this bug:

[https://bugs.launchpad.net/bugs/439448](https://bugs.launchpad.net/bugs/439448)

---

### Post by tanim009ir on 2010-12-19
:o

---

### Post by nick_goodfate on 2011-04-02
I tried to reinstall indicator applet but the problem remains. I just want to remove completly the keyboard layout indicator. 

I'm using Ubuntu 10.10 and here is a screenshot of my indicator applet:[ATTACH]187872[/ATTACH]

Instead of the keyboard indicator icon i have this:[ATTACH]187873[/ATTACH]

There must be a way to remove this really annoying indicator ...

---

### Post by nick_goodfate on 2011-04-02
*wrong post*

---

### Post by emzo on 2011-04-29
1. Open 'gconf-editor'
2. Locate branch '/desktop/gnome/peripherals/keyboard/indicator'
3. Untick 'showFlags'
4. Close gconf-editor
5. Relog the session

---

