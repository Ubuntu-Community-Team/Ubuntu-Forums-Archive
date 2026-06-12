---
title: "Num Lock fix anytime?"
date: 2010-06-23
forum: General Help
---

### Post by Ub28 on 2010-06-23
[FONT="Arial"][SIZE="3"][COLOR="Navy"]Hi.

I'm wondering why the num lock doesn't work in Ubuntu anymore? When you press the "num lock" key, you're supposed to be able to input the numbers along with **+ - * /** and decimal point.  When I press num lock and try typing numbers, nothing happens.

I've done a google search and this is a well known problem that nobody has fixed.  In Windows it's never a problem.

Seems such a shame that the great Ubuntu and Linux are so good for stability and speed, but can't get a simple num lock working. :confused:

I really hope to get in contact with the developers of Ubuntu and Linux to try and get the num lock to work properly.  Can anyone reading this do that for me?[/COLOR][/SIZE][/FONT]

---

### Post by cryptotheslow on 2010-06-23
Are you having this problem on a laptop or a desktop PC?

Num lock has always worked fine for me on a desktop with 9.01, 9.10 and 10.04.

---

### Post by stoneage on 2010-06-23
You mean this?

[https://bugs.launchpad.net/xorg-server/+bug/192508](https://bugs.launchpad.net/xorg-server/+bug/192508)

I don't know if this is still current on Lucid, but it is certainly present on Karmic.

---

### Post by NoBugs! on 2010-06-23
[Here]("http://ubuntuforums.org/showthread.php?t=1079020") is a workaround to make a num-lock shortcut, it even works if you have an apple keyboard without num lock.

---

### Post by tom.swartz07 on 2010-06-23
Found a workaround for this. First, find an unused modifier by typing:

```
xmodmap -pm
```

My mod3 was free (so adjust the commands accordingly if you use a different modifier). Now type the following:

```
xmodmap -e 'add mod3 = Scroll_Lock'
```

After doing this, your scroll lock key will now work. You can now make this a permanent fix by adding the following line to /root/.Xmodmap (if the file isn't there, then create it):

```
add mod3 = Scroll_Lock
```

By putting this in root's Xmodmap, it will enable the scroll lock key every time X starts.

---

### Post by sgosnell on 2010-06-23
This must apply only to certain systems/keyboards.  I've never had a problem with NumLock on any computer I've used, and that's several, with Ubuntu from 8.04 onwards.

---

### Post by dcstar on 2010-06-24
> **sgosnell said:**
> This must apply only to certain systems/keyboards.  **I've never had a problem with NumLock on any computer I've used, and that's several, with Ubuntu** from 8.04 onwards.

+1 - from Ubuntu 4.10 onwards.......

---

### Post by Ub28 on 2010-06-24
I'm using a desktop computer and an ordinary UK keyboard.
Thanks for your replies.

How do I file this as a bug report for Ubuntu?
I still don't know how I can fix it.  I would like to be able to press "Num Lock" and use the numbers when the LED light for Num Lock is on.

---

### Post by dcstar on 2010-06-24
> **Ub28 said:**
> I'm using a desktop computer and an ordinary UK keyboard.
.........

Go into System-Preferences-Keyboard-Layouts and make **sure** that the correct keyboard model is actually selected.

---

### Post by Ub28 on 2010-06-24
> **dcstar said:**
> Go into System-Preferences-Keyboard-Layouts and make **sure** that the correct keyboard model is actually selected.


[FONT="Arial"][SIZE="3"][COLOR="Navy"]It is showing as "United Kingdom" in the Keyboard-Layouts section. :)
[/COLOR][/SIZE][/FONT]

---

### Post by tom.swartz07 on 2010-06-24
Try the fix that I had posted. It was taken directly from the bug report from ages ago. 

Fixed the same issue on my computer

---

### Post by stoneage on 2010-06-24
Ub28 - try System -> Preferences -> Keyboard -> Mouse Keys

If 'Pointer can be controlled using the keypad' is enabled, then probably it is the same bug I posted the link to. Uncheck the option and your keypad should work. If not then I don't know what the problem is :)


I think SHIFT+NumLock is the shortcut to turn it on/off.

---

### Post by doas777 on 2010-06-24
if the mouse cursor thing doesn't work out, try numlockx

```

sudo apt-get install numlockx
numlockx

```

and if that works for you, check this out to make the change permenent by placing it in the gdm/init/Default. 
[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

---

### Post by Ub28 on 2010-06-24
[FONT="Arial"][COLOR="Navy"][SIZE="3"]THANK YOU for your help.

I pressed SHIFT and Num Lock and the problem has been magically fixed. :guitar:

Yes the mouse was moving very slightly when I was tapping the arrows in the num lock area.

Is this a bug?  Pressing SHIFT and Num Lock toggles between Num Lock working properly and the mouse moving when you press the arrow keys in the num lock.[/SIZE][/COLOR][/FONT]

---

### Post by doas777 on 2010-06-24
i think it may be a bug that mouse keys was on by default. does disabling it via stonage's instructions make the numlock button work without shift?

---

### Post by dcstar on 2010-06-25
> **Ub28 said:**
> 
........
Is this a bug?  Pressing SHIFT and Num Lock toggles between Num Lock working properly and the mouse moving when you press the arrow keys in the num lock.

Problems caused by users accidentally turning features on are not "bugs" - and please cease using fonts and colours to attract attention, you are no more important than any other poster in these forums.

---

### Post by stoneage on 2010-06-25
According to the bug reports the fact that it gets turned on without the user enabling it is a bug. 

The fact that SHIFT+Numlock toggles it on is not.

So if it repeatedly reoccurs it is a bug, if it gets enabled accidentally it is not.

---

### Post by Ub28 on 2010-06-25
> **stoneage said:**
> According to the bug reports the fact that it gets turned on without the user enabling it is a bug. 

The fact that SHIFT+Numlock toggles it on is not.

So if it repeatedly reoccurs it is a bug, if it gets enabled accidentally it is not.

[FONT="Arial"][COLOR="Blue"][SIZE="3"]I have never pressed SHIFT and Numlock until I read these comments.  Perhaps Numlock does mysteriously get changed and moves the mouse instead of entering numbers as it should do?  That *is* a bug.

To the user who told me off for having my text a different colour etc - this is what I've done for years in forums and I started this thread.  To everyone else, thanks for your help - much appreciated. :p[/SIZE][/COLOR][/FONT]

---

### Post by tom.swartz07 on 2010-06-26
> **Ub28 said:**
> [FONT="Arial"][COLOR="Blue"][SIZE="3"]I have never pressed SHIFT and Numlock until I read these comments.  Perhaps Numlock does mysteriously get changed and moves the mouse instead of entering numbers as it should do?  That *is* a bug.

To the user who told me off for having my text a different colour etc - this is what I've done for years in forums and I started this thread.  To everyone else, thanks for your help - much appreciated. :p[/SIZE][/COLOR][/FONT]

If you are fairly convinced that this is a genuine bug, you could report it on Launchpad.net. This website is the host of many, if not most, Ubuntu applications. Search for acpi or xorg, those would be the packages most likely to be related to your problem. The developers will take it from there.


***_Also, please make a note of this:_***
As the one user so bluntly (and rather impolitely) pointed out, it is generally frowned upon when users edit their posts with extra colors and different fonts. While these tools are useful for formatting things like 'how-tos' and the like, they are really difficult to process when used in a heavy-handed manner like you have been throughout this thread.

I understand that although it may be the norm for other forums, it is generally not accepted and many users will actually refuse to help someone that uses crazy font colors and sizes.
If you have any questions, please refer to the sticky thread posted at the very top of the Beginner Forums. Here: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
(It specifically says to avoid such actions)


Im glad that we were able to get this somewhat sorted out. 
I hope you have a great time here on the forums! :D

---

### Post by Ub28 on 2010-06-26
> **tom.swartz07 said:**
> If you are fairly convinced that this is a genuine bug, you could report it on Launchpad.net. This website is the host of many, if not most, Ubuntu applications. Search for acpi or xorg, those would be the packages most likely to be related to your problem. The developers will take it from there.


***_Also, please make a note of this:_***
As the one user so bluntly (and rather impolitely) pointed out, it is generally frowned upon when users edit their posts with extra colors and different fonts. While these tools are useful for formatting things like 'how-tos' and the like, they are really difficult to process when used in a heavy-handed manner like you have been throughout this thread.

I understand that although it may be the norm for other forums, it is generally not accepted and many users will actually refuse to help someone that uses crazy font colors and sizes.
If you have any questions, please refer to the sticky thread posted at the very top of the Beginner Forums. Here: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
(It specifically says to avoid such actions)


Im glad that we were able to get this somewhat sorted out. 
I hope you have a great time here on the forums! :D

I never knew that fancy fonts were taboo.  Plain text from now on.  I will try to report this numlock bug on Launchpad.net.

---

### Post by tom.swartz07 on 2010-06-26
> **Ub28 said:**
> I never knew that fancy fonts were taboo.  Plain text from now on.  I will try to report this numlock bug on Launchpad.net.

Great! Let us know how it turns out- the guys on Launchpad are generally really helpful when it comes to their projects! :D


Its not that the fancy fonts and colors are taboo, per se, but it just makes the user seem like they are a bit less 'professional' than others. Don't get me wrong, when used properly fonts and colors will really help your posts, its just that when an entire post is in giant letters and bright orange, it doesn't seem like the user is really all together there. haha

---

