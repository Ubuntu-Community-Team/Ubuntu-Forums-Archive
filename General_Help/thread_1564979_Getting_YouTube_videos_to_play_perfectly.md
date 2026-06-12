---
title: "Getting YouTube videos to play perfectly"
date: 2010-08-31
forum: General Help
---

### Post by NeoToasty on 2010-08-31
I've recently rejoined with Ubuntu and enjoying it's life. However, one of the key factors to my enjoyment on the net is being able to watch videos. YouTube, that is. Of course, Windows is practically flawless playing them (if fully loaded), and I'm sure Ubuntu could do the same.

But, after fighting to get the flash installed, nothing is going right. I've had Flash installed, and every YouTube video told me an error had occurred. I've tried the FlashReplace Plugin, and I didn't like it because it just wasn't the same and I'd like to be able to rewind the video and watch it again before it ends. I couldn't do that with that plugin and even when the video is done, I have to reload the whole page to watch it again. It's kindof irritating.

So, I'm asking if there's a way to get youtube videos to cooperate with flash via Firefox, it'd also  help on a lot of flash-heavy applications as well. I don't know if I installed it right, but I'm willing to re-install it the proper way, if any.

I am running Ubuntu 9.10 32-Bit, by the way.

Much appreciated.

---

### Post by inso_741 on 2010-08-31
did you install it from the ubuntu software center if not uninstall the current version and try it

---

### Post by NeoToasty on 2010-08-31
First time installing it, I selected one of the Flash plug ins Firefox listed. I think I went with the last one, I forgot it's name. I know the first was Adobe's. The third and last one started with the letter G.

Second time installing it, was downloading it and then used the Terminal to install. Error.

Then uninstalled both Adobe and ReplaceFlash plug ins. And then decided to use Ubuntu Software Center to get it which is the current plug in. Still getting "Error has occurred, try again later." =\

---

### Post by coffeecat on 2010-08-31
> **NeoToasty said:**
> First time installing it, I selected one of the Flash plug ins Firefox listed. I think I went with the last one, I forgot it's name. I know the first was Adobe's. The third and last one started with the letter G.

First - flash *should* work as well as in Windows if you have a 32-bit system. Second - it sounds as though you have installed Adobe's flash as well as the open source gnash. Perhaps they are fighting each other. What you need to do is to make sure you have uninstalled everything to do with flash and then install the repository flash installer.

Instead of using Software Centre, open System > Administration > Synaptic. There's a drop-down arrow to the right of 'quick search'. Click on that and search for 'flash'. Have a look through the list of matching apps that appear in the central pane. If any have a green box to the left, highlight it and make sure it is to do with flash video and then uninstall it by right-click > 'mark for uninstallation' and then clicking on the Apply button.

Once you've purged the system of anything you've found, click on 'All' to the left of the Synaptic window, find the package flashplugin-installer, mark it for installation and click Apply again. Hopefully, you will now have flawless flash. But if you do get an error in Synaptic, post the 'exact' error message.

**Edit:** a useful page for you:

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by NeoToasty on 2010-08-31
Works great. Thanks, coffeecat.

---

### Post by Rasa1111 on 2010-08-31
yea, I never had any issues with youtube videos. 
they all play just as they should.

---

