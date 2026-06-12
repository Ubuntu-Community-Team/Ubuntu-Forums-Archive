---
title: "update-notifier appears broken!!"
date: 2006-04-02
forum: General Help
---

### Post by v4169sgr on 2006-04-02
kubuntu breezy user.

How can I get update-notifier to work properly in KDE? Running 'update-notifier' from the shell simply produces TWO empty blank squares in the system tray :( 

Yes, I have ubuntu-desktop installed.

Thanks for your help!!! 8)

---

### Post by v4169sgr on 2006-04-02
Replying to my own post ...

Given that it looks like update-notifier depends on gnome-session [I've seen it invoked with 'update-notifier --sm-client-id = default7'], and given that there is no sense in trying to run gnome-session under KDE,

how on earth can I expect to get update-notifier running under KDE???

Is there a substitute that integrates with update-manager and synaptic?

---

### Post by gingermark on 2006-04-02
I'm not sure you can get it running in KDE. I tried once, and gave up.

However, in Dapper there is adept-notifier, which is part of adept, so if you can wait two months that will be your best bet I think.

---

### Post by v4169sgr on 2006-04-02
Thanks!

Problem is that what is there for those of us who don't like Adept? Could I simply use adept-notifier as an indication that I should go start update-manager?

BTW Have there really been no breezy updates for the past week?

---

### Post by mikkelwe on 2006-04-02
Sure. It should show if updates are needed or not. clicking the icon launches adept
though. You'd have to run synaptic or whatever you use manually, but then it should
show no updates needed. that is when it works. at least atm it's somewhat broken 
here, showing the wrong icon and randomly disappearing.

---

### Post by v4169sgr on 2006-04-03
Thanks!

I've not tried the Dapper version - am waiting on the official release - however does anyone have a handle on whether the adept-notifier is expected to be stable for the official release?

I would like to be able to use adept-notifier for the notification and update-manager for the actual updates. Update-manager works fine on breezy kubuntu.

---

### Post by mikkelwe on 2006-04-03
I don't think anything that badly broken will be included in the final release.
It's probably going to be fixed.

---

