---
title: "Won't Lock on Suspend or Ctrl+Alt+L"
date: 2012-05-05
forum: General Help
---

### Post by thinkingotherthings on 2012-05-05
I would like Ubuntu 12.04 to make my computer lock so that a password is required when I wake it from suspend, but I can't figure out how to do that.  I've searched the forums and found users with the same problem in older versions, but none of those fixes have done the trick for me.

Under 'System Settings' > 'Brightness and Lock' I have the LOCK option turned on, and 'Require my password when waking from suspend' is checked, but it does not seem to work.

I also have Ubuntu Tweak, and under 'Session Indicator' the 'Disable lock screen' box is not checked.

In a terminal I've looked in 'sudo vi /etc/default/acpi-support' and found this line:
# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

And the lock option is not commented out.

Also, even though the keyboard shortcut is set to Ctrl+Alt+L, it does not do anything.  I have tried mapping the lock function to a different shortcut but it still does not work.  In the top right menu there is a "Lock Screen" option, but clicking that button does not do anything either.

Does anyone know what else I should try?  Btw I am very new to Ubuntu and Linux so please explain your answers in simple terms.

Thanks!

---

### Post by OS Stuntman on 2012-05-11
Hello,  I just finished installing Ubuntu 12.04, I am also having this problem with Ubuntu; I thought installing xscreensaver had overwriting a setting somewhere.

32-bit version of Ubuntu 12.04 LTS

---

### Post by Amndeep7 on 2012-05-28
BUMP - I'm interested in finding a solution to this as well.

---

### Post by pettergoldstine on 2012-06-02
Same for me.  It was working when I updated to 12.04, but I think it was the last update a few days ago that changed something. 






32-bit version of Ubuntu 12.04 LTS on a Lenovo X201

---

### Post by mdeslaur on 2012-06-02
Is the gnome-screensaver process actually running?

Replacing gnome-screensaver with xscreensaver most likely breaks all the screen locking integration.

---

### Post by pettergoldstine on 2012-06-03
> **mdeslaur said:**
> Is the gnome-screensaver process actually running?

Replacing gnome-screensaver with xscreensaver most likely breaks all the screen locking integration.

Great, thank you.  That did it.  I just removed xscreensaver and replaced the gnome-screensaver.  I realized that I'd rather have the blank screen, but if anyone wants to keep xscreensaver there is this article [http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/]("http://www.howtogeek.com/114027/how-to-add-screensavers-to-ubuntu-12.04/") which goes through configuring your system, including replacing the lock screen.

---

### Post by omff613 on 2013-03-30
Good post and anser. Worked for me too. Re-install gnome-screensaver.

---

### Post by marko.brose on 2013-10-29
I have the same problem but I don't have gnome screensaver I have xscreenSaver 5.15 and my screen won't lock anymore even when I click on seetings on the taskbar or Ctlr+Alt+L

---

