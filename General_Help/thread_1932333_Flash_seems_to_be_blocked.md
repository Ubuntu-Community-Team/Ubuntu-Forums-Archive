---
title: "Flash seems to be blocked"
date: 2012-02-27
forum: General Help
---

### Post by forrestcupp on 2012-02-27
I'm using what I assume is 64-bit Firefox, since I'm using 64-bit Ubuntu 11.10, with Gnome Shell. I've tried about every method of installing Adobe Flash. I installed flashplugin-installer from the repos. Then when it didn't work, I tried installing the Flash-Aid Firefox extension, which downloaded and installed, but didn't do anything at all. So when that didn't work, I removed everything, went to the official Adobe download site, and downloaded the apt package for Ubuntu, and installed it with the Software Center. I've restarted Firefox and restarted the computer, and nothing is working.

When I attempt to load anything Flash, whether it be a video or game, it just shows something that looks like a video player that doesn't work. Even if it's a game, it shows that video player. The funny thing is that it flashes the game on the screen for a split second, then switches to that non-working video player, which almost seems like it is being blocked. I don't have any noscript or adblock extensions installed at this time, so I know it's not that.

Also, the exact same thing happens in Chromium, too, so it's not just a Firefox problem.

I've attached a screen shot of what happens when I try to load a Flash game.

---

### Post by forrestcupp on 2012-02-27
My attachment didn't work. I'll try again.

---

### Post by howefield on 2012-02-27
Looks like it wants to use totem to open the flash content.

You could try the sledgehammer approach and rename your .mozilla folder forcing firefox to recreate a fresh profile.

---

### Post by Gremlinzzz on 2012-02-27
Get the one that says tar.gz on end
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
extract/ copy or cut libflashplayer.so/ go to .mozilla folder in hidden files 
open folder see if plugins folder is there if not create it and place libflashplayer.so in it.:popcorn:

---

### Post by forrestcupp on 2012-02-27
> **howefield said:**
> Looks like it wants to use totem to open the flash content.

You could try the sledgehammer approach and rename your .mozilla folder forcing firefox to recreate a fresh profile.

That helps to know that is totem. I did what you said, and it still tries to use totem to open flash.

I'm trying to think of what I've done that would have changed that. In order to get Gimp 2.7, I installed the PPA, depends on the Gnome3 PPA, and the ricotz PPA. 

I think it's probably more likely that it got changed when I installed the PPA for Cinnamon 1.3, though. Since then, Cinnamon has been uninstalled, and I've disabled that PPA. It may have screwed with things, making Totem be what opens Flash stuff instead of the Flash plugin.

Any ideas on what I can do?

---

### Post by forrestcupp on 2012-02-27
> **Gremlinzzz said:**
> Get the one that says tar.gz on end
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
extract/ copy or cut libflashplayer.so/ go to .mozilla folder in hidden files 
open folder see if plugins folder is there if not create it and place libflashplayer.so in it.:popcorn:

I tried that, and it didn't work, either. It's still trying to use Totem.

---

### Post by Gremlinzzz on 2012-02-27
disable or remove the totem plugin

---

### Post by forrestcupp on 2012-02-27
> **Gremlinzzz said:**
> disable or remove the totem plugin

Disabled all of the plugins that are compatible with totem. Still didn't change anything. It must be deeper than that, since it does the same thing in Chromium.

In my defaults.list file, the flv and x-flv entries are set to totem.desktop. Maybe I could try commenting those out and see what happens.

Edit: removing those entries in defaults.list didn't help either.

---

### Post by pqwoerituytrueiwoq on 2012-02-27
edit->preferences->applications
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213369&stc=1&d=1330357272[/IMG]

---

### Post by forrestcupp on 2012-02-27
I don't even have a Flash Video entry, but the Flash entries I have are set to use Shockwave Flash for Firefox.

Also, a reminder, the same thing is happening in Chromium, so this is not merely a Firefox problem.

Thanks for the ideas, though, guys.

---

### Post by forrestcupp on 2012-02-27
I saw other people had my exact problem and got it fixed with Flash-Aid. So I just reinstalled the Flash-Aid plugin, and this time I actually found the wizard and ran it. It still didn't help. Totem is still trying to load flash content even after a Firefox and system restart.

I'm running out of ideas.


Edit.

Heeeeeeyyy!!! Guess what? I got it working. I figured I'd try the Flash-Aid wizard one more time, and this time I went with the 32-bit stable version of Flash instead of the 64-bit beta, which was the default choice. It set up the 32-bit version to work with 64-bit Firefox, and that worked. Sweet.

When I manually installed Flash and it didn't work, I was using the latest 64-bit version, too. I guess that's just not going to work for me for some reason.

Thanks for your help, everyone.

---

### Post by pqwoerituytrueiwoq on 2012-02-27
i wonder if you intsall the 64 bit if it will work now...

---

### Post by forrestcupp on 2012-02-27
> **pqwoerituytrueiwoq said:**
> i wonder if you intsall the 64 bit if it will work now...

I don't know, but now that I have it working, I don't want to try. I installed the 64-bit three different ways, and it never worked. I'm not screwing around with something that works.

---

