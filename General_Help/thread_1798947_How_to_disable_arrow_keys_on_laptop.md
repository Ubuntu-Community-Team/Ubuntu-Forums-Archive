---
title: "How to disable arrow keys on laptop?"
date: 2011-07-06
forum: General Help
---

### Post by trekon86 on 2011-07-06
Hey all,

Real quick question here. I am having a lot of problems with hitting the arrow keys while typing. At least, I think that's what it is. Maybe the page up/down/back buttons, too. Is there a way to disable one or more keys on the keyboard via software, other than going into BIOS? It's getting annoying having to retype stuff over and over. I guess maybe I'm just not used to my new keyboard, is all. But I never use those buttons and likely never will.

Thanks all,

PMZ

---

### Post by Krytarik on 2011-07-06
Yes, you can! :-D No, seriously, you can't disable individual keys through the BIOS, so the software way is the only available way anyway.

Create a file called ".Xmodmap" in your home directory with the following content:

~/.Xmodmap:```

keycode 111 = 
keycode 113 = 
keycode 114 = 
keycode 116 = 
keycode 112 = 
keycode 117 = 
```Which is usually:

keycode 111 = Up NoSymbol Up
keycode 113 = Left NoSymbol Left
keycode 114 = Right NoSymbol Right
keycode 116 = Down NoSymbol Down
keycode 112 = Prior NoSymbol Prior
keycode 117 = Next NoSymbol Next

You can lookup any further keys by running "xev" in the Terminal and pressing the concerning keys. Close the little window that it pops up to quit it.

The next time you login, you will most probably be asked if you want to use those keymap file*, then just choose "Add" and confirm with "OK". It should work then.

Greetings.

*depends on if you had such a file before, and did already confirm/disable those query

---

### Post by enimeizoo on 2011-07-06
Hello,
It might be a little bit brutal, but you can unmap them with xmodmap. You will need to find the keycode of your key, you can use xev for that.
The command to unmap a key is 
```
xmodmap -e "keycode XX = "
```Where XX is the keycode you want to unmap.

Since you need to unmap several keys, you might find more useful to put them in a file. (let's say foo.txt)
```

keycode XX = 
keycode YY = 
keycode ZZ = 
keycode AA =

```Then just run :
```
xmodmap foo.txt
```It will be undone on reboot, so you might want to put it in a .profile or something (something that will be run while X is running). Note that it only works if you have X support (e.g. not in virtual terminals).

Well, just a lil bit late :oops:

---

### Post by trekon86 on 2011-07-06
Thanks much! I will try that and post back if it works, I'm sure it will:)

PMZ


> **Krytarik said:**
> Yes, you can! :-D No, seriously, you can't disable individual keys through the BIOS, so the software way is the only available way anyway.

Create a file called ".Xmodmap" in your home directory with the following content:

~/.Xmodmap:```

keycode 111 = 
keycode 113 = 
keycode 114 = 
keycode 116 = 
keycode 112 = 
keycode 117 = 
```Which is usually:

keycode 111 = Up NoSymbol Up
keycode 113 = Left NoSymbol Left
keycode 114 = Right NoSymbol Right
keycode 116 = Down NoSymbol Down
keycode 112 = Prior NoSymbol Prior
keycode 117 = Next NoSymbol Next

You can lookup any further keys by running "xev" in the Terminal and pressing the concerning keys. Close the little window that it pops up to quit it.

The next time you login, you will most probably be asked if you want to use those keymap file*, then just choose "Add" and confirm with "OK". It should work then.

Greetings.

*depends on if you had such a file before, and did already confirm/disable those query

---

### Post by trekon86 on 2011-07-06
Solved! Thank You Muchly:)

PMZ


> **Krytarik said:**
> Yes, you can! :-D No, seriously, you can't disable individual keys through the BIOS, so the software way is the only available way anyway.

Create a file called ".Xmodmap" in your home directory with the following content:

~/.Xmodmap:```

keycode 111 = 
keycode 113 = 
keycode 114 = 
keycode 116 = 
keycode 112 = 
keycode 117 = 
```Which is usually:

keycode 111 = Up NoSymbol Up
keycode 113 = Left NoSymbol Left
keycode 114 = Right NoSymbol Right
keycode 116 = Down NoSymbol Down
keycode 112 = Prior NoSymbol Prior
keycode 117 = Next NoSymbol Next

You can lookup any further keys by running "xev" in the Terminal and pressing the concerning keys. Close the little window that it pops up to quit it.

The next time you login, you will most probably be asked if you want to use those keymap file*, then just choose "Add" and confirm with "OK". It should work then.

Greetings.

*depends on if you had such a file before, and did already confirm/disable those query

---

### Post by trekon86 on 2011-07-08
Hmm...well it seems I'm back to the same problem again. All of the keys I disabled are now working, again. Drat.

Any way to make this permanent? As in, across sessions?

Thanks,
PMZ

---

### Post by Krytarik on 2011-07-08
> **trekon86 said:**
> 
Any way to make this permanent? As in, across sessions?

The way I described it.

---

### Post by trekon86 on 2011-07-09
It only works right after logging in. If I close the laptop lid or allow it to log me out, it doesn't work again after I re-log.

This sucks. I guess, given the expected life of a laptop screen, I may as well just keep it on all the time. LCDs last a darn long time...
PMZ

---

### Post by Krytarik on 2011-07-09
> **trekon86 said:**
> If I close the laptop lid or allow it to log me out, it doesn't work again after I re-log.
Ok, this is different then. This has to do with the suspend/resume feature.

Please take a look at this thread, the least poster is even an Ubuntu user, with Lucid 10.04, so it should work:
[https://bbs.archlinux.org/viewtopic.php?pid=719692](https://bbs.archlinux.org/viewtopic.php?pid=719692)

Basically, it means creating a file like "/etc/pm/sleep.d/11_suspend" -notice that this must be executable-, and run 'xmodmap' with your newly created file ".Xmodmap". There might be a syntax for a command to work with every user, but I think you don't need to bother with this.

Good luck!

---

### Post by trekon86 on 2011-07-09
Thanks for your help!

I ended up just setting it so that it wouldn't logoff when the screensaver goes on. I played around a little and discovered that that's what the little checkbox labeled "lock screen when idle" does...

PMZ

---

