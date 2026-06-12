---
title: "Having trouble on new install of Ubuntu, need help."
date: 2011-09-18
forum: General Help
---

### Post by alexm42 on 2011-09-18
This is my first time trying any Linux distro, so forgive me for any ignorance which I may or may not have.

I just installed Ubuntu 11.04 with Wubi on a Dell Inspiron M5010 laptop with an AMD x64 dual core processor, and everything went well while installing. I rebooted it and selected to boot into Ubuntu when the option appeared, and it quickly went to a screen with a loading bar at the bottom that said various things like completing install and configuring hardware, at the top was an introduction to Ubuntu, and at the very top of the screen was the bar that would normally be at the top with the network status, volume, and power button, all of which were functional. The loading bar finished doing its thing, and then my computer rebooted.

It went to the Username/Password screen. I typed in my password, the computer made some noises, and the password screen disappeared. I was left seeing the desktop background, and there was no bar at the top of the screen, just the desktop background image and the mouse cursor. I left it for the better part of an hour, tried the ctrl-alt-t to open terminal, anything I could find online to do from another computer I had running, but nothing happened.

Does anyone have any suggestions? I would like to be able to run Ubuntu on my computer, but I can't do anything with it in this state. Again, please excuse my ignorance, and thank you for any help you can give me.

---

### Post by bcbc on 2011-09-18
Next time when you get to the signon screen, click on your name, but before entering your password look at the bottom and select the 'Classic' desktop. Then enter the password. See if that works better.

Does your computer have an intel onboard gpu or does it have a separate graphics card?

---

### Post by bcbc on 2011-09-18
There is some issue with this model. I believe you need the "pci=noacpi" kernel boot option as per this thread: [http://ubuntuforums.org/showthread.php?t=1633642](http://ubuntuforums.org/showthread.php?t=1633642)

To see how to set kernel boot options - see post #1 of [this thread]("http://ubuntuforums.org/showthread.php?t=1613132"). Ignore where it says (not for wubi - it's the same, after the initial install).

---

### Post by alexm42 on 2011-09-19
> **bcbc said:**
> Next time when you get to the signon screen, click on your name, but before entering your password look at the bottom and select the 'Classic' desktop. Then enter the password. See if that works better.

Does your computer have an intel onboard gpu or does it have a separate graphics card?

It has a separate gpu.

> **bcbc said:**
> There is some issue with this model. I believe you need the "pci=noacpi" kernel boot option as per this thread: [http://ubuntuforums.org/showthread.php?t=1633642](http://ubuntuforums.org/showthread.php?t=1633642)

To see how to set kernel boot options - see post #1 of [this thread]("http://ubuntuforums.org/showthread.php?t=1613132"). Ignore where it says (not for wubi - it's the same, after the initial install).

Thank you for your help; I will try that when I get home.

---

### Post by cornelis spronk on 2011-09-19
I understand that the 11.04 iso download does not have a driver compatible with the Dell. I have the same problem.

However, 10.10 works very well, as does 10.04. I suggest you try one of these. Hopefully, 11.10 will work better. It will be released in a few days.

Good luck!

---

### Post by alexm42 on 2011-09-19
> **bcbc said:**
> There is some issue with this model. I believe you need the "pci=noacpi" kernel boot option as per this thread: [http://ubuntuforums.org/showthread.php?t=1633642](http://ubuntuforums.org/showthread.php?t=1633642)

To see how to set kernel boot options - see post #1 of [this thread]("http://ubuntuforums.org/showthread.php?t=1613132"). Ignore where it says (not for wubi - it's the same, after the initial install).

I'm so happy right now. You are now my new most favoritest person that I don't know personally.
(Posted from Firefox running on Ubuntu 11.04):p

---

### Post by bcbc on 2011-09-19
> **alexm42 said:**
> I'm so happy right now. You are now my new most favoritest person that I don't know personally.
(Posted from Firefox running on Ubuntu 11.04):p

Great! Glad it worked out :)

Just so you know, Wubi is great to try out Ubuntu - and some people use it longer for their own reasons - but there is a higher risk since it uses a virtual disk (a single file). To be safe, I recommend keeping your data backups current and avoiding [hard poweroffs]("https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen").

Enjoy!

---

### Post by alexm42 on 2011-09-19
> **bcbc said:**
> Great! Glad it worked out :)

Just so you know, Wubi is great to try out Ubuntu - and some people use it longer for their own reasons - but there is a higher risk since it uses a virtual disk (a single file). To be safe, I recommend keeping your data backups current and avoiding [hard poweroffs]("https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen").

Enjoy!

I wouldn't use wubi, but I don't know how to make hard drive partitions from a drive that is formated for the entire physical drive to be one continuous logical drive, and I can't just reformat my drive because I don't currently have a data medium large enough to back up all my critical files. I am happy to be using Ubuntu, however, and when I purchase a new computer I will partition it properly immediately.

---

