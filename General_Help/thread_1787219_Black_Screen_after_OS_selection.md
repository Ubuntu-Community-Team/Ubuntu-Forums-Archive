---
title: "Black Screen after OS selection"
date: 2011-06-20
forum: General Help
---

### Post by JulianHeidt on 2011-06-20
This has been fixed by help of the #Xubuntu channel.

I still appreciate all the help I got here!

- Julian

---

### Post by Toz on 2011-06-20
What happens if you try without the nomodeset command?

Do you have an /etc/X11/xorg.conf file? If so, try booting into recovery mode and renaming the file (so that you start without it).

If possible, post back the results of:```
lspci -vnn
```
and the contents of **/var/log/Xorg.0.log**

---

### Post by JulianHeidt on 2011-06-20
with nomodeset the screen is blank.
Same for recovery mode cannot access it, the only thing i can access is the grub, and the memory test. :S
Where would I input this code? I haven't touched any linux distribution in a year or so.

---

### Post by JulianHeidt on 2011-06-20
> **JulianHeidt said:**
> with nomodeset the screen is blank.
Same for recovery mode cannot access it, the only thing i can access is the grub, and the memory test. :S
Where would I input this code? I haven't touched any linux distribution in a year or so.

also i tried lspci in grub - vnn is an unknown argument.

---

### Post by Toz on 2011-06-21
When you boot and get a blank screen, press Ctrl+Alt+F1. This should take you to a command prompt. Here you can login and do the following:

```
lspci -vnn
```
I'm interested in the section about your VGA compatible controller. Specifically the make/model (first line) and the last 2 lines "kernel driver in use" and "kernel modules"

```
ls -l /etc/X11/xorg.conf
```
I'm interested to see if this file exists

```
cat /var/log/Xorg.0.log | grep EE
```
I'm interested in seeing what errors are generated.

---

### Post by JulianHeidt on 2011-06-21
> **Toz said:**
> When you boot and get a blank screen, press Ctrl+Alt+F1. This should take you to a command prompt. Here you can login and do the following:

```
lspci -vnn
```
I'm interested in the section about your VGA compatible controller. Specifically the make/model (first line) and the last 2 lines "kernel driver in use" and "kernel modules"

```
ls -l /etc/X11/xorg.conf
```
I'm interested to see if this file exists

```
cat /var/log/Xorg.0.log | grep EE
```
I'm interested in seeing what errors are generated.

something seems to be wrong with the keyboard as well.
I tried Ctrl+Alt+F1 yet no result, on top of it I tried putting caps lock on to see if it was the keyboard, and it was. As soon as I boot in to Xubuntu the keyboard is no longer working. I don't know why, it worked in LiveCD Environment, am I missing plugins or updates?

Anyway thanks for the help you've been giving me so far. I really appreciate it!

- Julian

---

### Post by Toz on 2011-06-21
Make sure you press all 3 keys (Ctrl+Alt+F1) and the same time. If it still doesn't work, try choosing the recovery mode option in grub and booting into recovery mode and seeing if your keyboard works.

---

### Post by JulianHeidt on 2011-06-21
> **Toz said:**
> Make sure you press all 3 keys (Ctrl+Alt+F1) and the same time. If it still doesn't work, try choosing the recovery mode option in grub and booting into recovery mode and seeing if your keyboard works.

Does not work in normal boot or recovery mode.
I can see the lights of the keyboard OFF as well.

Recovery mode brings me to a black screen just like normal boot.
The only thing I can access that's linux related is the memory test.

---

### Post by cubsfan53 on 2011-06-21
I have an eMachine E525, I had the same blank screen and tried the same options listed. What I found was that the screen was going into the lowest brightness setting.

When I hear the login sound, I hit my Fn+brightness^ keys. I found this out because I coulc just barely make out the Ubuntu logo and log in by shining a flashlight onto the screen, so then I knew that it was something to do with the backlight.

I haven't found a permanent fix yet, but it works. Hope this works for you.

Rick

---

### Post by JulianHeidt on 2011-06-21
> **cubsfan53 said:**
> I have an eMachine E525, I had the same blank screen and tried the same options listed. What I found was that the screen was going into the lowest brightness setting.

When I hear the login sound, I hit my Fn+brightness^ keys. I found this out because I coulc just barely make out the Ubuntu logo and log in by shining a flashlight onto the screen, so then I knew that it was something to do with the backlight.

I haven't found a permanent fix yet, but it works. Hope this works for you.
Rick

I really appreciate the help rick, I see the fn but where is the brightness? thanks, I hope this works.

(do note it's apparent that the keyboard doesn't work so this might not help)

okay UPDATE:

The keyboard turns off ONLY WHEN I use Ctrl+Alt+F1
Brightness has nothing to do with the issue

---

### Post by cubsfan53 on 2011-06-21
Check your arrow (directional < >)keys, mine are under the Rt Shift Key.

When I tried the Ctrl+Alt+F1 key combination the system didn't seem to respond because the backlight wasn't allowing me to see the change in tty.

Rick

---

### Post by JulianHeidt on 2011-06-21
> **cubsfan53 said:**
> Check your arrow (directional < >)keys, mine are under the Rt Shift Key.

When I tried the Ctrl+Alt+F1 key combination the system didn't seem to respond because the backlight wasn't allowing me to see the change in tty.

Rick

brightness has nothing to do with the issue, I used FN and directional works in Windows but not in Xubuntu

and keyboard completely shuts down after i use ctrl + alt + f1 at the same time.

---

### Post by JulianHeidt on 2011-06-21
> **JulianHeidt said:**
> brightness has nothing to do with the issue, I used FN and directional works in Windows but not in Xubuntu

and keyboard completely shuts down after i use ctrl + alt + f1 at the same time.

tried again just in case same results.

I'm also on the IRC channel #xubuntu if anyone thinks they can help me please go there, so that the responses are instant. Thanks guys!

If not I understand.

---

