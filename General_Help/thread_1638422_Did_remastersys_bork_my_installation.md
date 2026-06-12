---
title: "Did remastersys bork my installation?"
date: 2010-12-05
forum: General Help
---

### Post by Mistiq Dragon on 2010-12-05
Here's my situation
  I have Ubuntu 10.04 installed right now, as of right now, I can't log into it at all.  I'll boot into Ubuntu, the login screen pops up (it looks different, like it's low graphics or actually reminds me the way some WINE apps look in Ubuntu, if that makes any sense)and I'll get a notification that *Install problem!  The configuration defaults for Gnome Power manager have not been installed correctly.  Please contact your System administrator*

I'm not positive but the only thing I can attribute this to is when I was looking into backing up my home folder with Remastersys.  I launched the program, maybe clicked through the first few steps saw that it wasn't what  i was looking for and hit cancel or something.  the gui closed but I noticed that there was a terminal operation going but I chose not to interrupt it.  I continued my normal browsing for a while until I noticed that chrome was stuck in permanent reloading status (all tabs) and that firefox wasn't loading new pages.  So I restarted both browsers, no change so I restarted the whole computer.

Unfortunately once I got to the log-in screen I got to the problems listed above.  Screen graphics look bad, I'll put in my password, the screen will blink for a long second and then take me right back to that screen.

I believe it's due to something going on with Remastersys, I didn't do any updates lately, Iv'e used Remastersys before and never saw it close like that before.

---

### Post by Mistiq Dragon on 2010-12-05
Well.......unfortunately nobody responded luckily for me, I found out the answer.

I'll post the problem here if anybody needs this one day.

It seems I had this issue because Remasterysys filled up my drive with the backup (or something similar), So I ended up accessing the terminal by (CTRL + ALT + F1) and emptying out the root trash by entering this command sudo rm -r /root/.local/share/Trash/files

Once that was done, I was able to log in and do some more detailed cleaning.

I know it's not pretty or elegant, but I don't have the level of knowledge to make it all effecient, I just have to do what works

---

