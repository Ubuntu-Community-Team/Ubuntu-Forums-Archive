---
title: "5 year old messed up my login screen"
date: 2011-01-21
forum: General Help
---

### Post by cbnation on 2011-01-21
Hi,

I have a problem on Ubuntu 10.04 with the login screen. This machine has been working great for months now, but my 5 year old daughter was playing with the computer when it was at its login screen. She clicked everywhere with the mouse and filled in garbage in the password field, and this is what I have now:

[IMG]http://www.baelemans.com/loginscreen.jpg[/IMG]

I see half of the login screen on the left with an on-screen keyboard, and the right hand side shows a magnified view (sort of) that follows the mouse. I can only login by using the on-screen keyboard. Once logged in, all is working fine.

I already changed the Nvidia drivers from the open source to the proprietary drivers and back, but it doesn't help.

Anybody an idea of what can solve this? 

Cedric

---

### Post by silkworm2.5 on 2011-01-21
Search along the bar at the bottom for accessibility features. Try disabling them. This Should help.

---

### Post by irv on 2011-01-21
I take it you tried to restart it after a complete power off?

---

### Post by cbnation on 2011-01-21
Yes, I already did multiple complete power-offs. The bottom bar is unreadable, so no idea where to click. Is there a keyboard short cut to do the same?

---

### Post by Smart Viking on 2011-01-21
Hm, a five year old did that to my moms computer too O.o

Maybe reinstall gdm? :)

---

### Post by irv on 2011-01-21
After doing some searching I found some setting in CompizConfig Settings Manager your 5 year old might have changed. Under Accessibility there is a Magnifier and Zoom Desktop that might have got turn on. I was looking for that keyboard on your desktop but I didn't find it yet. I hope you can get it fixed. Things like this should not be able to change without admin rights.

---

### Post by cbnation on 2011-01-21
She must have changed it at the login screen, cause I hadn't logged in yet. I also find it incredible she managed to do it and that it is persistent after a cold restart. I will try the GDM reinstall.

---

### Post by cbnation on 2011-01-21
GDM re-install didn't solve it :-(

---

### Post by 3Miro on 2011-01-21
All that your daughter did was to enable Accessibility features (hence the magnifying glass and the keyboard). You have to find a way to turn those off, they persist, because Ubuntu thinks that you "need" this "help". The login screen is controlled by GDM (not compiz), GDM exists in its own separate environment (that is why once you login everything is fine).

On the other hand, reinstalling software doesn't help, when the issue is with the settings. Reinstall doesn't overwrite the settings files. What you need to do is to reconfigure GDM. If I am correct, the command is:

```
sudo dpkg-reconfigure gdm
```

But I am not 100% sure.

---

### Post by stinkeye on 2011-01-21
```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
```

---

### Post by cbnation on 2011-01-22
Stinkeye, you rock !!!

This did the trick. I will look to disable them completely. Nobody in my family needs the accessibility features.

---

### Post by stinkeye on 2011-01-22
No problem, I've done it myself 'cause I have to see what things do.
Basically I've got the mind of a 5 year old.
;)

---

### Post by stinkeye on 2011-01-22
> **cbnation said:**
> Stinkeye, you rock !!!

This did the trick. I will look to disable them completely. Nobody in my family needs the accessibility features.

You can disable the screenreader, magnifier and screen keyboard at the GDM with 
```
gksudo gconf-editor /desktop/gnome/applications/at
```


and right clicking on each entry and selecting **Set as Mandatory** (untick first)


[COLOR="Red"]#[/COLOR]If you ever need to set them back 
```
gksudo gconf-editor
```
go to 
File > New Mandatory Window

This window only lists keys you have made mandatory, so it is
easy to find the relevant entries,
and Right click and select **Unset Key**

---

### Post by pinay311 on 2011-05-21
> **stinkeye said:**
> ```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
```

hi stinkeye!

i have the same problem and tried entering the code you posted. but i'm getting an error:
"Can't overwrite existing read-only value: Value for '/desktop/gnome/applications/at/screen_magnifier_enabled' set in a read-only source at the front of your configuration path"

how do I fix this?

---

### Post by stinkeye on 2011-06-10
> **pinay311 said:**
> hi stinkeye!

i have the same problem and tried entering the code you posted. but i'm getting an error:
"Can't overwrite existing read-only value: Value for '/desktop/gnome/applications/at/screen_magnifier_enabled' set in a read-only source at the front of your configuration path"

how do I fix this?
Sounds like you set the key as mandatory (ie unwritable) before doing
```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
```

See my previous post @ [COLOR="Red"]#[/COLOR] to make the key writable and try again.
Log out/in between the two steps.

---

### Post by ssr003 on 2011-06-30
hey stinkeye thanks for the help man. I had same problem with on screen keyboard and magnifier.
however after disabling as mandatory on screen keyboard and magnifier
next login long key presses was enabled
cant seem to disable this now, can you help?

---

### Post by stinkeye on 2011-07-01
This will tell you if slowkeys is enabled at the login screen
```
sudo -u gdm gconftool-2 --get /desktop/gnome/accessibility/keyboard/slowkeys_enable
```


To disable at the login use
```
sudo -u gdm gconftool-2 --set /desktop/gnome/accessibility/keyboard/slowkeys_enable --type bool false
```
or check in the accessibilty icon at the bottom right of the login screen that slow keys is not ticked.


If you have slowkeys after you have logged in use this to disable.
```
gconftool-2 --set /desktop/gnome/accessibility/keyboard/slowkeys_enable --type bool false
```

---

