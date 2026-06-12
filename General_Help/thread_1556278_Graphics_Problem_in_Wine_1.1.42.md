---
title: "Graphics Problem in Wine 1.1.42"
date: 2010-08-19
forum: General Help
---

### Post by Speedsmack on 2010-08-19
I'm fairly new to Ubuntu, but I'm trying to learn.  I've been all through at least 100 threads trying different tweaks and apps and I cannot get past this problem-

Edit: My Graphics Card is ATI Mobility Radeon 9200

I'm using Ubuntu 10.04 and am running Shaiya with Wine 1.1.42.  I have a patcher that bipasses both GameGuard and Updater, but it makes no difference whether I use the hacked game.exe(renamed) or the original game.exe (that comes with download).  

I have Wine configured to ALSA sound, Auto Detect Drivers, Windows 95, etc.. like I've read to do, but no matter what settings I use or which way I go about logging onto the game, the graphics are crap.

The SonoV screen displays flawlessly, then the login screen is real shaky and laggish.  Once I get through that to the character screen.. the background is upside down, but graphics wise "okay" still.  

Once I select my character and it goes to load the map I can't see anything but greyish green color.  The userbars and skills show perfectly.. I can see players' names floating around.. the chatbox is fine.. but I cannot see my character or any background at all.


Can someone tell me what I need to do?  I feel like I should be using a proprietary driver for graphics, but none are listed.  Downgrading Wine and everything else people have suggested in this thread have not worked at all.. I have already tried Wine 1.0.1 and every other suggestion in these forums.

From what I've described.. any ideas?  

P.S. I can also see my health/mana/SP bars just fine.. and pop up boxes, too.  Also when I type /return to port to nearest town.. the picture with the progress bar displays just fine.  It's pretty much JUST the background.. I'm running around blind and invisible.

---

### Post by dino99 on 2010-08-19
you might use the latest wine: 1.30

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by realzippy on 2010-08-19
...have you imported the DLL Files ?

---

### Post by Speedsmack on 2010-08-30
> **realzippy said:**
> ...have you imported the DLL Files ?


If I'm not sure on exactly what it takes to do that, then I probably havent.  Can you give me a quick run down on what I need to do to do this?  Thanks.

---

### Post by Speedsmack on 2010-09-01
Okay I'm running the latest Wine 1.3 and am still having the same problems.

The login screen is shaky and greyish.  I manage to get my name and password in and get [OK] clicked to go to character screen..

At the character screen.. the character and background are upside down, yet the character choice box and other boxes are not.  At this point it's still a bit laggish to where I have to click the buttons a few times to get it to click.

The load screen is just fine.. graphics are perfect.. it's back to right-side-up..  the red progress bar does just fine, etc.

Once the load screen is done and it goes to load the map, everything is dark green/black, except for:

- I can see my userbar and skills perfectly
- I can see people's names and guild names around me (but not THEM)
- I can read chat just fine.. as well as type and private message.

These are the only things I can see and everything else is this greenish black.  Does it trigger any thoughts or ideas with you "linux geniuses?"

I feel like there's just something being left out, since the sound works and everything.. the game runs fine, whether I use my hacked game file to bi-pass game guard and updater or whether I use the original game.exe file.  There's no difference between the two other than running the updater (which I also have no problems with.)


I saw the comment asking if I imported the DLL files and I'm unsure of what DLL files they're referring to or how to go about importing them.. if that is the problem or would help.


Also.. I've configured Wine to run as every Windows OS type listed.. they all run and act the same.


P.S. I did some research on the "playonlinux" application, though it's not free.. I read in there that Shaiya does play flawlessly through this too.


Any suggestions, tips or ideas please?

---

### Post by dino99 on 2010-09-01
the easier way might be to make a clean install: save your work if any into .wine, then delete it before clean installation

note: you might post into wine subforum, not here

---

