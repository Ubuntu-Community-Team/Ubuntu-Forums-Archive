---
title: "Skype integration issues"
date: 2012-02-29
forum: General Help
---

### Post by DemonSharkKisame on 2012-02-29
Yeah, two posts in about an hour, shocking. :p

Anyways, this problem's been bugging me for the past couple of weeks: Skype no longer seems to want to cooperate or integrate with Ubuntu's settings and look-and-feel.

For an example of look-and-feel issues: the mouse cursor reverts to the default X11 "core" cursor within the Skype window, and the program itself no longer tries to follow the GTK theme (I know Skype is Qt-based, but most other Qt programs integrate smoothly within Unity).

Settings-wise, Skype no longer seems to follow the settings I have Unity use for my sound (I use a Microsoft USB headset). I find that having to now configure it manually is a major PITA considering I've yet to get it working properly.

Screenshots attached showing what I mean, though the cursor seems to show up as the correct one I have set up in my settings. Weird.

---

### Post by Ms. Daisy on 2012-03-01
> **DemonSharkKisame said:**
>  Settings-wise, Skype no longer seems to follow the settings I have Unity use for my sound (I use a Microsoft USB headset). I find that having to now configure it manually is a major PITA considering I've yet to get it working properly.
I have no idea about the look & feel stuff. But in regards to the headset, I found that I had to have Skype open, then go into unity's sound settings to choose the usb microphone.  It didn't work for me to use Skype sound devices to configure it. 

A more detailed description:

[http://ubuntuforums.org/showthread.php?t=1893830&page=3](http://ubuntuforums.org/showthread.php?t=1893830&page=3)

---

### Post by DemonSharkKisame on 2012-03-01
Hmm... didn't seem to work for me. I find it peculiar, especially that up to a couple of weeks ago, Skype worked *flawlessly* for me, even better than in Windows, as a matter of fact. Maybe an update somewhere borked Skype's functionality? :confused:

---

### Post by DemonSharkKisame on 2012-03-03
And just as quickly Skype got borked, something's got it working perfectly again. :D Marking as [SOLVED].

---

### Post by ScottDeagan on 2012-05-17
I understand that this bug is closed, but I'd just like to add something about the theming issues - something that was driving me crazy for weeks. Here's how I reliably got around it:

1. Completely uninstall Skype (sudo apt-get remove skype).
2. Download Skype from the Skype website.
3. Install the .deb package by double clicking it.

(after the installation is complete, you should be able to run Skype, but the icon will not appear in your top panel).

4. Get panel whitelist:[FONT=monospace]

[/FONT]gsettings get com.canonical.Unity.Panel systray-whitelist

Output could look something like this:

['JavaEmbeddedFrame', 'Wine', 'Update-notifier']


5. Add Skype to the whitelist:

gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Update-notifier', 'Skype']"

6. Restart Skype.

The GTK theming should now be gone, and Skype should look like a well behaved good Unity citizen.

---

