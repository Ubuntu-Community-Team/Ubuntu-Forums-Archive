---
title: "Xubuntu internet upgrade anomalies - blue screen and wireless drivers not activated"
date: 2011-11-03
forum: General Help
---

### Post by Rytron on 2011-11-03
Hi.

Today I did an internet upgrade for the first time on a real computer (I tried it once before inside VirtualBox with no problems). I went from Xubuntu 11.04 –> 11.10.

I have noticed that soon after I login, the screen goes blue and there is black text on the desktop icons [image attached]. How do I sort this out?

Also, my wireless works fine but in 'Additional Drivers', it says my wireless drivers are not active [image attached]. I don't understand this. Can someone explain it please?

---

### Post by gsmanners on 2011-11-03
You probably lost an icon theme in the upgrade. I'd double-check your Appearance settings.

Why are you complaining about something working w/o drivers? Isn't that a good thing?

---

### Post by decoherence on 2011-11-03
> **Rytron said:**
> 
Also, my wireless works fine but in 'Additional Drivers', it says my wireless drivers are not active [image attached]. I don't understand this. Can someone explain it please?

This means that there is a proprietary driver available for your wireless card. If it works fine currently, then you don't need it. If you find you have problems like getting disconnected after being online for a while, you might give it a try, but don't install it if you don't have to because then you'll be dependent on Broadcom for fixes.

---

### Post by Rytron on 2011-11-03
> **gsmanners said:**
> You probably lost an icon theme in the upgrade. I'd double-check your Appearance settings.

Why are you complaining about something working w/o drivers? Isn't that a good thing?

I should have added that I have Xubuntu freshly installed in VirtualBox and that too gets that odd blue background glitch. Therefore it couldn't be an issue with upgrading from Xubuntu 11.04.

I am not complaining ;). I am just curious as all previous installs of Ubuntu/Xubuntu on my laptop required me to have drivers installed from the 'Additional Drivers' window. Perhaps those drivers are now built-in to the latest Xubuntu?

---

### Post by Rytron on 2011-11-03
> **decoherence said:**
> This means that there is a proprietary driver available for your wireless card. If it works fine currently, then you don't need it. If you find you have problems like getting disconnected after being online for a while, you might give it a try, but don't install it if you don't have to because then you'll be dependent on Broadcom for fixes.

I went to install it before but got some error and it told me to check a log somewhere. I will heed your advice and let things as they are.

---

### Post by gsmanners on 2011-11-03
> **Rytron said:**
> I should have added that I have Xubuntu freshly installed in VirtualBox and that too gets that odd blue background glitch. Therefore it couldn't be an issue with upgrading from Xubuntu 11.04.

The background looks fine on my system. Therefore it works fine all computers. :P

That is a weird issue. You sure you can't just fix it with Appearance and Desktop Settings?

---

### Post by Rytron on 2011-11-03
> **gsmanners said:**
> The background looks fine on my system. Therefore it works fine all computers. :P

That is a weird issue. You sure you can't just fix it with Appearance and Desktop Settings?

I will look further into changing themes. It must be a bug though since I used my desktop computer's VirtualBox with Xubuntu 11.10 and it had the exact same sudden blue desktop problem issue as my laptop's Xubuntu 11.10. The two installs were independent of each other.

---

### Post by Rytron on 2011-11-04
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206223&d=1320334634[/IMG]

I have found the cause. It happens when nautilus is launched. It can be remedied by ending/killing nautilus.
Previously a log out/in or reboot was the only solution that I knew of.

There was nautilus installed on both my laptop Xubuntu 11.10 and VBox Xubuntu 11.10.

---

### Post by Rytron on 2012-03-22
Nautilus problem was solved. Check my post at the end of this web page: [http://ubuntuforums.org/showthread.php?t=1934926](http://ubuntuforums.org/showthread.php?t=1934926)

---

