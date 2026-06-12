---
title: "Please help me understand the &quot;update-manager&quot;"
date: 2010-11-29
forum: General Help
---

### Post by germanix on 2010-11-29
I regularly start-up the update-manager once a week to check for any updates. The update manager then always tells me that my system is up to date and that no updates are available. I then ask it to check, and it then comes back with a list of updates available. This is double work and not very effective When I use the update manager in Mint for instance it gives me the list of updates on the first check. Why is this not so with ubuntu 10.10? If I do not ask it to make a double check I would never know that updates were available!

Also, I removed certain applications like gwibber and empathy via the software center, but still the update manager offers me updates for these apps no longer installed. Is it not supposed to check what apps are installed before offering such updates?

---

### Post by ean5533 on 2010-11-29
1) You don't need to manually start update-manager once a week. By default it will automatically pop up once a week to show you all the latest updates that are available. You can also change the frequency that it automatically checks in the settings.

2) When update manager is started manually it does not immediately go look for new updates; instead, it just tells you about updates that it already knew existed last time it ran. Clicking the "Check" button is what tells it to go out at look for new updates. Again, this is a non-issue if you let it pop up on its own.

---

### Post by ajgreeny on 2010-11-29
I am pretty sure that the default is for update-manager to check once per day, not once a week as ean5533 says, so it is an application that you should be able to set up as you want and then forget.  The only change I make is to stop it opening in the background, but just show an icon in the panel when updates are available, as it always used to.

Check how your system is setup by opening update-manager and going to the settings button, bottom left.

---

### Post by TBABill on 2010-11-29
+1. Just like in Synaptic when you open it up it loads what it knows. If you click reload it will pull in things that changed since it's last look. If you were to use PCLinuxOS and try to update you'd see this same behavior there because you use Synaptic...open it up, then click reload, then mark all updates, apply. Same behavior, different presentation. It only reloads when told or on the schedule it is set to look for updates within.

---

### Post by germanix on 2010-11-29
Thank you very much for this information. I do now understand how it works somewhat better. I still would like to know however why I get offered updates for apps no longer installed.

---

### Post by oldos2er on 2010-11-29
> **germanix said:**
>  I still would like to know however why I get offered updates for apps no longer installed.

It's showing all the updates available on the repositories, without regard as to whether or not they're installed on your system. No worries--if you don't have a particular package installed, it won't be upgraded.

---

### Post by germanix on 2010-11-30
Thank you all for your help and input. This Noob now understands somewhat more. You learn as you go along and you have all helped me to learn more.

---

### Post by ajgreeny on 2010-11-30
> **oldos2er said:**
> It's showing all the updates available on the repositories, without regard as to whether or not they're installed on your system. No worries--if you don't have a particular package installed, it won't be upgraded.
No, sorry, but I think that is wrong.

Update manager should only ever show packages that are installed on your machine.  It will not show packages that are no longer installed, or have never been installed.  If the OP is seeing that behaviour, something is definitely wrong.

---

### Post by germanix on 2010-11-30
Thanks for that, ajgreeny. That was exactly my concern. I used synaptic to completely remove gwibber and empathy and still when I update via the update manager it tells me that packages and updates for these applications are available for update. I obviously do not want it and then have to manually de-select those packages before installing the rest of the update that I want. But the next day I get offered these packages again.
Surely the update manager should first check which packages/apps are installed and then offer updates for those packages only.
I used to run Linux Mint and that is exactly how the update manager functioned there. I believe Mint has a different update manager to Ubuntu but am not sure but I also cannot recall ever having this problem with previous Ubuntu versions either.

---

### Post by oldos2er on 2010-11-30
> **ajgreeny said:**
> No, sorry, but I think that is wrong.

Update manager should only ever show packages that are installed on your machine.  It will not show packages that are no longer installed, or have never been installed.  If the OP is seeing that behaviour, something is definitely wrong.

It's always behaved that way for me, FWIW. If it is misconfigured in some way, I'd really like to know, if anyone knows.

---

