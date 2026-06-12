---
title: "How to uninstall ubuntu and reinstall back the windows 7 without any disc installer?"
date: 2012-03-14
forum: General Help
---

### Post by Thebuntuway on 2012-03-14
Alright guys..There are some problem that i got here. I feel like i just involve in very high level puzzle to solve. Yes, it is HOW TO UNINSTALL UBUNTU AND REINSTALL BACK THE PREVIOUS WINDOWS 7 that before in my laptops. Here are some few reason why i want my dumb windows 7 back:
--------------------------------------------------------------------------------------------------------------------
-My netbook keep freezing everytime i want to surf internet and takes abot 5 minutes or something like that to back resposive
-Very worse lag in online gaming
-So many freak error like 'Broken count', Broken package, cannot install that, cannot install this..bla bla bla..
-a very long and long and slow and aslow startup even the startup music was running and i had to wait about 2 minutes or something to get in the real startup appear like the desktop..
-'eats' lot of my energy sources. before that, these one freak me out when i use ubuntu last week, MY PC MAKE A SMOKE COMES OUT FROM COOLING PASSAGE!!!..Thats makes me panic very much and that thing does not happen when in use windows 7 and happen when i use Ubuntu Linux.
-Well, you know many people like guitar pro and pyros drum for windows, not when i using ubuntu, that stuff cannot use anymore.
-These os cannot reinstall..i had done that before a few time, then suddenly, it cannot reinstall!..THAT WAS WEIRD..
-I am pc gaming user and i wish ubuntu can play many games. But, its need emulator or something like wine or crossover codeweavers to play through..that was waste my time..
-Many software are not supported and also my internet mode was cannot supproted also and that have been burning down my money about few dollar..
-i know that ubuntu had a very good security, but, these time, that security is useless for me because it cannot install updates, software that advailable  in ubuntu software center and sometimes, when i want to reinstall back, it said these ubuntu are NOT GENUINE!!(BUT I DOWNLOAD IT FROM THE OFFICIAL UBUNTU WEBPAGE!)
-and so on and so on
---------------------------------------------------------------------------------------------------------------------
Well, i know that windows 7 are also dumb and im also freakin **** off with that software, but, it seems windows had less problem than Ubuntu. IM NOT SAYING THAT I 'ANTI' TO UBUNTU but, there are no such broken packages, broken count, crazy updates, cannot support that, cannot support these and bla bla ba pot pet pot pet..I think i more familiar with windows 7. The only problem that asking me to unistall windows 7 and change it to ubuntu is when my pc starting lagging when i playing games and slow startup(taking about 2 or 3 minute if i not mistakes) and that was annoying very much. So i google ubuntu and download and install it to my pc and replace my ****** windows and hope thing turn better. But things gone worse. EVEN MORE WORSE...to know the WORSE is, see above why i want my windows back. because that guys, i need ya help, i try to solve the problem about a month and i waste my time infront of my laptops only at that time to fix such thing. I HATE TO INSERT COMMAND IN THE TERMINAL because i can't remember command well. Sudoing that, sudoing these just zero jobs and wasting my time. Well, my school project are in a few weeks to be finish and sent but these ubuntu(I THINK IT MIGHT HELP ME VERY WELL THAN WINDOWS) just SCREW THINGS UP!.HFS!!!..I wish there are time machine and tell me at the past to not install ubuntu in my pc. THT WAS IMPOSIBRU!!!..now, how to get my windows 7 back??..please guys, i really need that windows 7...only you my hope before my parent know something about my pc and give me a bad side looking...HHHHEEELLLPP!!!!!!!:mad:

---

### Post by Mark Phelps on 2012-03-14
To get Win7 BACK, you must HAVE Win7 somewhere.  Sounds simple, but it might not be.

If your PC came with Win7 preinstalled, then there's likely a Recover partition (may be hidden) containing a compressed Windows image file (*.wim) that can be used to restore the original Win7 setup.

If you don't know if that partition still exists, you will have to do some work to find out.

Either inside Ubuntu (if it is still working) or booting from an Ubuntu desktop CD, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on your drive -- and from that, we can see if your Recovery partition still exists.

[Note: I know you hate doing command line work, but if you want our help, you have to provide us the detailed information we need]

If your Recovery partition is intact, then you can move to the next step of using it to restore your PC.

If there is no Recovery partition, then you will need a Win7 Installation DVD -- and since you probably don't have one, you will have only a couple of choices.  First, if your PC came with Win7 preloaded, you will need to contact the supplier to see if they will SELL you a set of full-restore optical media.  They are likely to charge you for this, but the cost will be a LOT less than buying it outright. Second, if the PC did not come preloaded, then you have no option other than buying it.  IF you are a full-time student, you should be able to get it at a massive discount through your educational institution; otherwise, you are looking at paying $100 USD and up to get an actual DVD.

And, not to imply any wrongdoing, but don't ask about ways to download a FREE version of Win7.  That is considered piracy and is prohibited on this form.  Just telling you in advance -- in case anyone else should suggest this approach.

Once you had a chance to run the terminal command and see what you have now, please come back with the results.

---

### Post by squilookle on 2012-03-14
I once had smoke coming out of one of my computers, and it turned out one of my fans had failed and the cpu overheated. 

Did this happen just the once or more than once? Did the computer work okay after that? 

I'm not sure if yours is caused by the same issue or if something has gone wrong with Ubuntu to cause that, but, unless you are certain there is nothing wrong with the computer, I would look into that...

---

### Post by Mark Phelps on 2012-03-14
Sorry ... got focused on the reinstalling-Win7 part and overlooked the smoke-coming-fom-the-PC part!

This latter event is NEVER a good sign and nearly always indicates that something is FRIED on your laptop.  With a desktop, if it is a processor, there MIGHT be a chance you could replace it and the PC will then reboot, but on a laptop, the components are fixed in place.

As to Ubuntu causing this, directly, I would have to say NO; but there is the problem of known kernel bugs that can result in overheating -- which, if severe enough (laptops tend to be worst) and left long enough, can result in components overheating to the point that they are destroyed.  Usually, folks notice the SCREAMING fans and the intense heat coming out of the fan ports -- before the PC burns itself up.

---

### Post by Thebuntuway on 2012-03-15
OK, i will tried first and i will give more information about it later.
Oh yes, did this mean i need to buy again new windows 7??..

---

### Post by Thebuntuway on 2012-03-15
it happen three times..because that i had a limited usage of laptop now..im freakin weird why did this thing happen when i using ubuntu and not happen when i using windows...it start to smell like a burning cat fur or something then suddenly smokes comes out!..because that i need to shut down my laptop quickly if i start to smell something burn and it will give me a time to let my laptop rest..geezz...sound like unfamiliar huh?..

---

### Post by Thebuntuway on 2012-03-15
> **squilookle said:**
> I once had smoke coming out of one of my computers, and it turned out one of my fans had failed and the cpu overheated. 

Did this happen just the once or more than once? Did the computer work okay after that? 

I'm not sure if yours is caused by the same issue or if something has gone wrong with Ubuntu to cause that, but, unless you are certain there is nothing wrong with the computer, I would look into that...

it happen three times..because that i had a limited usage of laptop  now..im freakin weird why did this thing happen when i using ubuntu and  not happen when i using windows...it start to smell like a burning cat  fur or something then suddenly smokes comes out!..because that i need to  shut down my laptop quickly if i start to smell something burn and it  will give me a time to let my laptop rest..geezz...sound like unfamiliar  huh?..

---

### Post by Thebuntuway on 2012-03-15
> **Mark Phelps said:**
> Sorry ... got focused on the reinstalling-Win7 part and overlooked the smoke-coming-fom-the-PC part!

This latter event is NEVER a good sign and nearly always indicates that something is FRIED on your laptop.  With a desktop, if it is a processor, there MIGHT be a chance you could replace it and the PC will then reboot, but on a laptop, the components are fixed in place.

As to Ubuntu causing this, directly, I would have to say NO; but there is the problem of known kernel bugs that can result in overheating -- which, if severe enough (laptops tend to be worst) and left long enough, can result in components overheating to the point that they are destroyed.  Usually, folks notice the SCREAMING fans and the intense heat coming out of the fan ports -- before the PC burns itself up.

Yes, that was the problem i guess..My laptop sound like grinding chainsaw suddenly before the burning smell and smoke appear..it will sound crazy first and it stop then things come calm again and you will think 'Oh, well, it stop, countinue again' until then a few seconds the smoke comes out with a very annoying smell...

---

