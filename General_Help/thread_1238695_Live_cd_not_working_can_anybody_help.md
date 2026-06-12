---
title: "Live cd not working can anybody help?"
date: 2009-08-12
forum: General Help
---

### Post by rock it on 2009-08-12
Hello all,
I've been trying to switch to ubuntu for the past few days now and have had some problems. I wanted to know if the disk i burned would work so i booted it up and came to the menue fine, selected my language and entered in the "try without any change to your computer" option. The loading screen loaded the screen went black and then.... this happened (click the link)

[http://www.flickr.com/photos/41385134@N07/3815626314/](http://www.flickr.com/photos/41385134@N07/3815626314/)

has anybody got any idea whats wrong? thx in advance.

---

### Post by bodyharvester on 2009-08-12
okay, that was wierd, has this happened more than once? you could just install ubuntu only and see if the same error occurs

id advise burning another copy, how did you get it in the first place? torrents or other?

-joe

---

### Post by Landscapeman on 2009-08-12
I have yet to see that. See if you can try it on another computer. I know that burning ISOs seems to have some issues with high speed burning. If that LiveCD does not work try reburning at the lowest speed.

---

### Post by bodyharvester on 2009-08-12
> **Landscapeman said:**
> try reburning at the lowest speed.

and if you have the option to, verify the data that has been burned

---

### Post by RedSingularity on 2009-08-12
You can always use the alternate install cd.

---

### Post by overdrank on 2009-08-12
Hi and welcome, You may check the cd for errors and also checksum the iso,[HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")
What is the model of the graphics card?

---

### Post by rock it on 2009-08-12
I downloaded it of the ubuntu site and went by what it said there. I burned the iso image to a disc I tried max burn speed then i tried 6x then 2x. I did get an error at first just trying to open the cd but i was told windows xp sp2 would solve that, and it did but now theres this. I also tried installing using wubi but that didn't work (not sure if I did it right though).

---

### Post by bodyharvester on 2009-08-12
if you have the space just do a dual boot and install it next to whatever else is on there

---

### Post by rock it on 2009-08-12
oh yeah and my graphics card is 32mb nvidia geforce4 420. I know its rubbish but as far as im aware it should run. 256mb ram 30gb hdd 1.8ghz processor.

---

### Post by bodyharvester on 2009-08-12
which version of Ubuntu are you trying to install, 9.04?

EDIT: a google search showed you do have minimum RAM for ubuntu 9.04 (256Mb)

---

### Post by rock it on 2009-08-12
Is should have enough space to do that but I looked tutorials and not 100% sure how to do it. also i dont want to try dual boot then find out theres disc faults then have to try and clean up. I have checked the disc for errors and apparently its fine but i dont trust it.

---

### Post by bodyharvester on 2009-08-12
when you dual boot you see a little bar on the screen showing your disk size (EDIT: this is during the installation), there will be one colour section showing where windows is and another where you can specify how much to give to ubuntu and whenever you computer starts it gives you the clear option of booting from either partition, that is it says "Windows or Ubuntu"

choose Ubuntu ;)

---

### Post by rock it on 2009-08-12
the only reason I'm keeping windows is incase theres any complaints from other family members :) not that they use the computer more than once a year. does the choice to partition automatically come up when you install?

---

### Post by rock it on 2009-08-12
also d'you think its safe to install a possibly faulty disc?

im gonna go sleep on it dunno where you are in the world but here its 5mins past midnight. thx for help will continue the research tomorrow or later on today.. whatever

---

### Post by bodyharvester on 2009-08-12
> **rock it said:**
> the only reason I'm keeping windows is incase theres any complaints from other family members :) not that they use the computer more than once a year. does the choice to partition automatically come up when you install?

well you get all those choices,
try without any changes blah blah
install
install within windows (or something like that)

if you "install within windows" think of it like a pie in pieces, one piece is already a windows piece but the rest of the pie you can decide how much you give to Ubuntu ;)

---

### Post by bodyharvester on 2009-08-12
> **rock it said:**
> also d'you think its safe to install a possibly faulty disc?

im gonna go sleep on it dunno where you are in the world but here its 5mins past midnight. thx for help will continue the research tomorrow or later on today.. whatever

10 past for me lol

as for tha faulty disc...if it doesnt work you could remove the partition manually, i can give you some help on that if its needed, im going to sleep too

ill check back tomorrow

---

### Post by rock it on 2009-08-13
It didnt work i pressed install and went away to do some other stuff. then 20mins later came back it asked to reboot. "OK" i pressed ok then the cd ejected so i put it back in. The computer shut down, i went away again and when i came back it looked like this again

 [http://www.flickr.com/photos/41385134@N07/3815626314/](http://www.flickr.com/photos/41385134@N07/3815626314/)

---

### Post by rock it on 2009-08-13
i have allready uninstalled it with a disc cleaner and im back to where i was.

also some guy on yahoo answers says to download an ubuntu cleaner which fixes errors so i might try that.

---

### Post by sblunix on 2009-08-13
Ai Ai Ai! You're copy of the Ubuntu installation CD downloaded improperly, go back to the Ubuntu homepage and restart all over again, sorry :( (it's happened to me too)

---

### Post by MeanEYE on 2009-08-13
> **rock it said:**
> Hello all,
I've been trying to switch to ubuntu for the past few days now and have had some problems. I wanted to know if the disk i burned would work so i booted it up and came to the menue fine, selected my language and entered in the "try without any change to your computer" option. The loading screen loaded the screen went black and then.... this happened (click the link)

[http://www.flickr.com/photos/41385134@N07/3815626314/](http://www.flickr.com/photos/41385134@N07/3815626314/)

has anybody got any idea whats wrong? thx in advance.

Ok, firstly did you burn your image to CD or DVD. I know of similar problems that happend whit CDs. It's funny I know, but took me a while to figure that one out. I had a similar problem only kernel was spitting out problems with SATA controller. Weird, then I found somewhere on this forum a tip that I should burn on DVD. :) heh... that settled it for me.

---

### Post by rock it on 2009-08-13
did you get crazy colors?

---

### Post by rock it on 2009-08-13
cd is what i burned it on should i try a dvd? yea ill try it k thx ill get back to y'all

---

### Post by MeanEYE on 2009-08-13
> **rock it said:**
> cd is what i burned it on should i try a dvd? yea ill try it k thx ill get back to y'all

No problem. I only hope that this is the problem. :) Because the solution is simple hehe :)

---

### Post by P4man on 2009-08-13
whatever you burn to, when you boot from it, one of the options in the first menu is "check this cd/dvd for errors". A good idea to let that run.

Another idea is to stop wasting blank discs and make a bootable stick instead. This may help make it really easy:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

That said, im not 100% convinced the problem lies with the cd, but it could well be. Either way, its a funky theme you got there lol.

---

### Post by theozzlives on 2009-08-13
Seems like it may be a bad .iso, or your video card. I'd try the alternate CD and do the text based installer. When the CD ejects, don't put it back in, let it boot off the hard drive.

---

### Post by rock it on 2009-08-13
for some reason infrarecorded is not detecting the dvd

---

### Post by bodyharvester on 2009-08-13
yup, good advice, burn to a blank DVD after making sure with md5sum that its a good download, verify data at every step, once cd ejects take it out

good luck, ill keep checking back till its done

---

### Post by bodyharvester on 2009-08-13
> **rock it said:**
> for some reason infrarecorded is not detecting the dvd

you need to be ABSOLUTELY sure your cd/dvd drive WRITES to a dvd, mine didnt, i pissed away money on blank dvd's not knowing what id done wrong, till i burned the disk on my mates drive which does WRITE to dvd's:P

---

### Post by theozzlives on 2009-08-13
> **rock it said:**
> for some reason infrarecorded is not detecting the dvd

You don't need a DVD, CDs work fine. I even use a RW for testing all my pre-release versions.

---

### Post by bodyharvester on 2009-08-13
> **theozzlives said:**
> You don't need a DVD, CDs work fine. I even use a RW for testing all my pre-release versions.

really? :| never knew that, i was trying to install the RC of Win7 though

---

### Post by theozzlives on 2009-08-13
> **bodyharvester said:**
> really? :| never knew that, i was trying to install the RC of Win7 though

Vista and 7 need a DVD but not Ubuntu. Unless you want all the extra languages that come on the DVD you buy.

---

### Post by rock it on 2009-08-13
> **bodyharvester said:**
> you need to be ABSOLUTELY sure your cd/dvd drive WRITES to a dvd, mine didnt, i pissed away money on blank dvd's not knowing what id done wrong, till i burned the disk on my mates drive which does WRITE to dvd's:P

clever I'll use the other laptop to burn it cause it writes dvds thx.

---

### Post by bodyharvester on 2009-08-13
> **theozzlives said:**
> Vista and 7 need a DVD but not Ubuntu. Unless you want all the extra languages that come on the DVD you buy.

i didnt buy my 9.04, i asked for it from [http://shipit.ubuntu.com](http://shipit.ubuntu.com) and i recieved it a week later, never used windows since

---

### Post by rock it on 2009-08-13
should i download md5sum and check before burning?

---

### Post by bodyharvester on 2009-08-13
> **rock it said:**
> should i download md5sum and check before burning?

id advise it, i did that with the UNR of 9.04, its a little extra work but worth it

---

### Post by rock it on 2009-08-13
if downloaded and extracted what now?

---

### Post by bodyharvester on 2009-08-13
> **rock it said:**
> if downloaded and extracted what now?

:| um... there was a post here earlier by someone who gave a link with instruction on how to do this page 2 or 3 maybe

---

### Post by rock it on 2009-08-13
> **bodyharvester said:**
> :| um... there was a post here earlier by someone who gave a link with instruction on how to do this page 2 or 3 maybe

nah thats how to make a bootable usb
 
but ill google it anyway

---

### Post by bodyharvester on 2009-08-13
> **rock it said:**
> nah thats how to make a bootable usb
 
but ill google it anyway

it must have been in another thread, ill go find a link for md5sum thing...

---

### Post by bodyharvester on 2009-08-13
done :)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

:popcorn:

---

### Post by overdrank on 2009-08-13
> **overdrank said:**
> hi and welcome, you may check the cd for errors and also checksum the iso,[howtomd5sum]("https://help.ubuntu.com/community/howtomd5sum")
what is the model of the graphics card?

:p

---

### Post by bodyharvester on 2009-08-13
i knew it! i knew someone posted that link!

now to wonder why i didnt check the first page :lolflag:

---

### Post by P4man on 2009-08-13
just to be clear: checking the MD5 hash ensures your download is not corrupted, but of course it doesn't guarantee your cd is burned without problems, so if you are burning it to cd, still run the "check this disc for errors" in its main menu after booting from it.

---

### Post by rock it on 2009-08-13
anyway got it now thx and im checking the hashes

fingers crossed

---

### Post by rock it on 2009-08-13
check sums are the same

---

### Post by rock it on 2009-08-13
gonna check for defects on the boot menu

---

### Post by rock it on 2009-08-13
both test showed no faults hmmm.... what now?

---

### Post by bodyharvester on 2009-08-13
install it by itself wiping the whole disk clean or give a bit of space on the disk to ubuntu to dual boot

---

### Post by overdrank on 2009-08-13
> **rock it said:**
> both test showed no faults hmmm.... what now?

Have you tried any of the options from the F4 menu on the start install page.

---

### Post by rock it on 2009-08-13
> **bodyharvester said:**
> install it by itself wiping the whole disk clean or give a bit of space on the disk to ubuntu to dual boot
  so I need to partition my drive?

---

### Post by P4man on 2009-08-13
> **rock it said:**
> so I need to partition my drive?

I dont mean to be rude, but you might want to ignore bodyharvester's posts :s

---

### Post by rock it on 2009-08-13
> **overdrank said:**
> Have you tried any of the options from the F4 menu on the start install page.
  no  ill try that in a minute once ive set up a dvd burner to burn the iso again to dvd

---

### Post by rock it on 2009-08-13
I have managed to load it of the live cd in safe graphics mode. I got that option by pressing F4. The graphics dont look any different from what I've seen from the normal graphics mode on the internet. but YEI!!! it works but is there a way I can install it in safe graphics mode or will it when installing go back to normal graphics?

---

### Post by rock it on 2009-08-13
should i install xubuntu instead? is that less demanding on the system?

---

### Post by P4man on 2009-08-13
This thread is getting long, so let me try and summarize, see if I got it right:
1. you can boot from a live cd, even without "safe graphics mode", and everything seems ok. right?
2. You  installed ubuntu, and when you booted it for the first time, you got strange graphical artifacts that you posted a video off. Correct?

Then we made you test your disc and download, and they turned out fine. But those where made after you did the install, so have you tried installing again with a "known good install cd" ?

If you have, and if the problem persists, we may try altering your videocard settings on the 'corrupted video ubuntu install'.

As to your other questions: xubuntu is indeed lighter on resources, I dont remember your system specs, but if you have less than 512Mb, it might be a better option

---

### Post by bodyharvester on 2009-08-13
> **P4man said:**
> I dont mean to be rude, but you might want to ignore bodyharvester's posts :s

if i made a mistake somewhere tell me, :confused: dont just mention it like "psst, he made a mistake, ignore what he said", ive never used the partition manager because i have only one for Ubuntu and never want to have a windows again (no offense to windows users) but the screen i mentioned was the one i saw when i was installing my 9.04 desktop edition.

i dont take offense to what you posted but if ive made a mistake or if something i said was unclear id like to know so i can avoid making the same mistake in the future, 

thanks

- joe

---

### Post by rock it on 2009-08-13
ok heres the update. I can get ubuntu and xubuntu to run on safe graphics mode. I can understand this with ubuntu but I'm unsures as to why xubuntu needs safe graphics. Heres my spec again for all who dont know

1.8 GHz cpu
256mb ram
32mb graphics card (nvidia geforce 4 420)
30gb hdd

When I boot xubuntu in normal mode what happens is similar to the video i posted on the first post, except different colors. Do I need to change my graphics settings or something can somebody please help?

i dont want be stuck with windows :(

---

### Post by P4man on 2009-08-14
dont see why you're not surprised ubuntu doesnt work, but xubuntu should. They both use the same X windowing system and same kernel (therefore X drivers).

Anyway, lets try a few things. There are 2 or maybe 3 videodrivers you can try. Vesa, nv (opensource nvidia) and nvidia (closed source binary driver). im not sure the latter still supports your card, but lets try vesa first.

Boot ubuntu. When you get the funky graphics, press control+alt+F2 to get a console. Im hoping that looks allright. If so, type in the following:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.back
```

(makes a backup of the file). Note uppercase X in X11.
Then edit it:

```
sudo nano /etc/X11/xorg.conf
```

Look for any "driver" line, and if there is one, report here what it is. If its not vesa, or more likely, there is none, then put this in:

> Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection


Save by pressing control+X and confirming save changes.
Reboot (sudo reboot).

---

### Post by rock it on 2009-08-14
I have installed xubuntu now and it seems to be working fine, couldn't be bothered with windows so I dindnt bother partitioning, Linux rocks!!! its just so nice compared to windows i could never go back. thanks all for all your help.

---

### Post by bodyharvester on 2009-08-14
glad to hear it, i was wondering what happened to you.

---

### Post by theozzlives on 2009-08-15
Great! You should still have a seperate /home. Take a gander at this, [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/"). It comes in handy for re-installs and whatnot.

---

