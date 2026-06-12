---
title: "I need a linux that looks like Vista, or maybe just vista help &gt;.&lt;"
date: 2009-07-03
forum: General Help
---

### Post by Tobias-sama on 2009-07-03
[COLOR="Indigo"]alright, I broke my roommates laptop by screwing around with Windows, and he insists that it be Windows I install on this laptop, however, I can't get the stupid thing to work, and everyone I seek advice from is completely incompetent, so here's the deal

is there some way I can make linux look/function exactly like windows, like maybe run everything in Wine and have a vista theme or something? 

at the very least, when he finds out it'll be a pretty funny prank :P[/COLOR]

---

### Post by snakeman21 on 2009-07-03
In short, I think you're screwed.  Even if you use a Vista theme, directories are organized entirely differently.  And what if he tries to install Zune software?  Zunes will not run on Linux.  Error messages are completely different.  I'm not trying to rain on your parade, but the best thing you can do for your roommate is either get him to try and maybe switch to ubuntu, or take the laptop to a computer repair shop and have them install Vista.  Sorry.

---

### Post by credobyte on 2009-07-03
Yes, you can make it look like Vista by using various themes/icons, but - he'll figure it out in the first 10 minutes ( you wouldn't ? ).

---

### Post by TheForumTroll on 2009-07-03
What's wrong with it? Maybe someone could help you out :popcorn:

---

### Post by undeadboe on 2009-07-03
You could but eventually he would figure it out. Why dont you just buy a new vista cd?

---

### Post by mrbiggbrain on 2009-07-03
IM a computer tech, maybe i could help, i work w/ and on vista all day everyday... its easy if you give me the errors.

cant guarnentee anything, but how much worse could u get

---

### Post by wcutrombonekid on 2009-07-03
dude, don't you have your recovery disk?

---

### Post by mrbiggbrain on 2009-07-03
> **theozzlives said:**
> That's illegal!!!

actualy, did u try restoreing from the factory partition, whats the make and model...

also it is indeed not illegal to use iso version of windows nor is it to download them... it is illegal to use keygens. its normaly a bad thing to say on a fourum regardless though.

---

### Post by Tobias-sama on 2009-07-03
[COLOR="Indigo"]heh, I thought about posting on here just asking for vista help, but figured no one would know anything XD or at least I'd be chased out for blasphemy :P

guess I underestimated the help forums? 

anyways, yea everything works, but the problem is the wireless card isn't being recognised at all, not in the device manager, nothing, it's as if I don't even have one in, which is funny, because I do. I've tried installing the drivers offered by HP but to no avail, I've even taken the card out and  examined it and everything. Also, can't restore with just a generic vista disk. HP laptops require piles and piles of drivers on top of the original software to bring them to a functional point.

also, nuked the handy restore partition given by HP in a moment of foolishness.[/COLOR]

---

### Post by evermooingcow on 2009-07-03
Edit: nevermind.

---

### Post by Vrekk on 2009-07-03
This is kinda a shot in the dark but it has worked for me in the past.  Try unpluging the computer from the wall for about a min and try again, and if that dosnt do in (probally wont but its worth a shot right?) tell the device manager to Scan for hardware changes.  That should let it find the network card.

---

### Post by mrbiggbrain on 2009-07-03
A) contact HP, pay $30, get the recovery disks.

B) Buy a wireless card for it.

C) take it to a pc shop, they can do bigger tests

D) could be a registry issue, in which case it could be easy-hard to fix.

---

### Post by synapsys on 2009-07-03
Maybe try a live cd like Ubuntu 9.04, Knoppix, or Backtrack 4, to test the wireless card functionality. If it still doesn't work, buy a new wireless card. If it does work, try getting the latest windows updates. Microsoft is starting to include a lot of wireless drivers in their updates. They won't be 'checked' by default, you will have to go to updates, list the available updates, and check the box next to the wireless driver.

It's a laptop. Did you make sure the wireless switch on the front of it is turned on?

---

### Post by Tobias-sama on 2009-07-03
[COLOR="Indigo"]do you think the recovery disks would work? 

(wireless card worked perfectly before all this btw, the computer was just beginning to die slowly in other ways)

here's what I did 

-tried to install XP
-realised HP doesn't support/ have drivers for downgrades
-found a copy of vista on the internet, however it's a different version than the original
-loaded piles of drivers onto it, scoured the Internet for help, even contacted tech support online, all to no avail, wireless still didn't work

yes the wireless switch is in the on position XD


[/COLOR]

---

### Post by synapsys on 2009-07-03
If the wireless card is good, and the pci port that the wireless card plugs into is good, then the recovery disks from hp should work. As long as the wireless card is the same one that came with the laptop. With the recovery disks you will get a copy of XP, a driver disk, and a bunch of crapware that came with the machine.

---

### Post by Tobias-sama on 2009-07-03
[COLOR="Navy"]does it come with the OS? b/c I though I saw on the site that it said that the disks didn't come with windows..

but.. maybe I read it wrong :P[/COLOR]

---

### Post by Danbo19 on 2009-07-04
I say load Ubuntu on it in the meantime anyway. That way, if the wireless works, you know that it it isn't a problem with the wireless card. Tell him to use Ubuntu while you work on his Vista problems. Maybe if he is forced to use Ubuntu he will learn to love it and you won't need to mess with Vista!

---

### Post by t4thfavor on 2009-07-04
If you have to buy another wifi card, make sure it comes from HP, they are notorious for locking their hardware to their wifi cards.

Also, the recovery disks probably come with a generic image of windows that you will have to put your key in later. I say he's better off without if though.

You could d/l the windows 7 public beta for a while it looks like Vista, and its free for now.

---

### Post by anjilslaire on 2009-07-04
After Vista loads up, use the System Restore function (enabled by default in most systems), and pick a restore point a few days back, or back far enough to when the wifi was working, and restore the system state to that point.

This is a feature that was first introduced in XP. You can essentially roll the OS back to a previous state, similar to a snapshot in a VM, but not quite. You may be able to get back to a point before the wireless went awry.

---

### Post by Tobias-sama on 2009-07-04
[COLOR="Indigo"]@ Danbo19 - actually in the meantime he has to use my computer, which has ubuntu loaded onto it. and he's still not to keen on using linux, mostly because he wants to run games, and I'm not sure if Wine will do that. but believe me I've been trying to convert him for ages :P also.. your sig. made me lol 

@anjilslaire in regards to restore, it would only restore to a previous point in the current OS right? my wireless card was working 2 OS's ago (vista->XP->new vista) also, props for using Richard from lfg :P

I'll also take a look at windows 7, however, if both XP and vista required buckets of drivers from HP, I'm hesitant to think that 7 won't.

[/COLOR]

---

### Post by anjilslaire on 2009-07-05
Correct. If you've reloaded OSes a few times, you're out of luck.

---

