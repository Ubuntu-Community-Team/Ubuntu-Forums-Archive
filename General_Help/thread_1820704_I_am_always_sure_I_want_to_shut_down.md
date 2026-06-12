---
title: "I am always sure I want to shut down"
date: 2011-08-07
forum: General Help
---

### Post by tomkat3 on 2011-08-07
Hello forums,

I'm using Xubuntu 11.04. Whenever I click shut down, it always asks me "Are you sure you want to shut down?" I'd rather the computer just trust me and shut down. I wouldn't mind waiting for the computer to turn on again in the 1 in 100 chance I did it accidentally. How can I change this? 

lol, I don't think I've ever seen such a minor complaint anywhere on ubuntu forums...

---

### Post by galvatron408 on 2011-08-08
sudo init 0

that means "trust me" just shutdown.

---

### Post by uRock on 2011-08-08
When the pop up in question appears, I just tap the space bar.

---

### Post by galvatron408 on 2011-08-08
I pressed the power button on my computer and Ubuntu switched to init 0. Thats freaken awesome!

Here's the help page on it. You're going to love it. I know, I am.
[https://help.ubuntu.com/11.04/ubuntu-help/power-turnoffbutton.html](https://help.ubuntu.com/11.04/ubuntu-help/power-turnoffbutton.html)

---

### Post by Megaptera on 2011-08-08
Is this what you're looking to do?

"In ubuntu versions before lucid when the shutdown or restart button is pressed there will be a confirmation dialog asking to confirm your action and if no action is taken in 60 seconds the system will automatically confirm your action. But in lucid the auto confirmation is removed and you have to manually confirm your action no matter how long it is. However if you dont like your system asking you to confirm your action then there is a simple way to remove the confirmation dialog."

If so link here: [http://blulin.wordpress.com/2010/06/07/disable-shutdown-and-restart-confirmation-dialogs-in-ubuntu-lucid/](http://blulin.wordpress.com/2010/06/07/disable-shutdown-and-restart-confirmation-dialogs-in-ubuntu-lucid/)

If not ... apologies!!

---

### Post by uRock on 2011-08-08
> **galvatron408 said:**
> I pressed the power button on my computer and Ubuntu switched to init 0. Thats freaken awesome!

Here's the help page on it. You're going to love it. I know, I am.
[https://help.ubuntu.com/11.04/ubuntu-help/power-turnoffbutton.html](https://help.ubuntu.com/11.04/ubuntu-help/power-turnoffbutton.html)

Holding the power button does not run init 0 by default. BUT once the settings are altered to shut the system down when hitting the power button, it will do just that.

---

### Post by tomkat3 on 2011-08-08
> "In ubuntu versions before lucid when the shutdown or restart button is  pressed there will be a confirmation dialog asking to confirm your  action and if no action is taken in 60 seconds the system will  automatically confirm your action. But in lucid the auto confirmation is  removed and you have to manually confirm your action no matter how long  it is. However if you dont like your system asking you to confirm your  action then there is a simple way to remove the confirmation dialog."

That's exactly what I want! I just switched to Xubuntu 11.04 from Ubuntu 10.04 (with gnome) yesterday after using the 10.04 ever since I discovered Linux (8 or 9 months). I didn't know it was standard like that...

However, the gconf-editor didn't have the option I needed to change, and the command it gives at the end had no effect (or error message). I'm using Ubuntu with xfce, and this tool seems to be intended for gnome. Could that be why? How do I change this in xfce?

---

### Post by tomkat3 on 2011-08-16
I suppose I should add what I eventually did to fix the problem:

- I right clicked on a panel and went to "add new items"
- searched, and added 'action buttons'
- The default action is to log out, but right clicking on the new action button and there's a pull down menu where you can pick shut down, restart, etc.

Now I just click on that action button and it shuts down, no questions asked :D

---

### Post by vinodhkumarsampath on 2011-10-29
goto "gconf-editor"
navigate to "/apps/indicator-session/suppress_logout_restart_shutdown" and check the corresponding box to it.....
DONE....

---

### Post by mike555 on 2011-10-29
not a good idea to put your email address in posts, spammers will get it.

---

