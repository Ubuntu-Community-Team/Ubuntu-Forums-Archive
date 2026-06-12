---
title: "Can NVIDIA and nouveau play together?"
date: 2010-06-10
forum: General Help
---

### Post by Helios747 on 2010-06-10
Hello again,

So I've experienced the great functionality that nouveau gives me, but am a bit disappointed that it cannot support 3D acceleration. I play a few games so this is a requirement.

I don't want to switch completely back to the NVIDIA driver because it breaks my brightness control keys on my laptop, and it isn't as fast and responsive as nouveau.

Is there a way to have nouveau run by default, but when I launch a game in a separate X server it would load the NVIDIA driver?

---

### Post by Helios747 on 2010-06-11
bump. Running the NVIDIA driver full time is starting to bug me

---

### Post by wkulecz on 2010-06-11
> I don't want to switch completely back to the NVIDIA driver because it breaks my brightness control keys on my laptop, and it isn't as fast and responsive as nouveau.

I don't have a Ubuntu laptop so I don't know about brightness keys, and I don't do 3D, but on my systems the Nvidia driver blows away nouveau in all respects.  I have 10.04 systems with 5500, 6200, 7300, 9400, & 210 series video,  nouveau was barely usable to get the restricted drives installed on most of them, and I've never looked back.

After you disable/enable the restristed driver it says a restart is required, I don't know if logging out and back in again would be sufficient or not, but you could try it -- it'll be faster than rebooting, but with the new upstart system Gnome seems to take longer to start up than does the boot, a welcome improvement.  I suspect my Gnome start is greatly slowed by having the save session box checked, but its a convience I love.

---

