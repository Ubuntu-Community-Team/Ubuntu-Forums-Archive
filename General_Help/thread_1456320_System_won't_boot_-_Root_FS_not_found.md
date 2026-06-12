---
title: "System won't boot - Root FS not found"
date: 2010-04-17
forum: General Help
---

### Post by ZootHornRollo on 2010-04-17
Hi,

I have a system i use as a media source for music running ubuntu 9.10.

I haven't used it for a couple of weeks but it has been running.  Today i went to use it.  Turned on the monitor and gave the mouse a wee shake to wake up the system however nothing happened.  Tried a few more times, key presses etc but nothing.  Eventually had to hold power button for 5 secs to power down and then rebooted.

Got stuck on splash screen.

Powered down again and rebooted, got this:

[IMG]http://farm5.static.flickr.com/4011/4527050689_f4022acdd6_b.jpg[/IMG]

Powered down and rebooted in recovery :

[IMG]http://farm5.static.flickr.com/4059/4527682820_f6d131b563_b.jpg[/IMG]
[IMG]http://farm5.static.flickr.com/4009/4527053681_25d0cae972_b.jpg[/IMG]

Any idea what could be wrong - hoping its not HD failure  [-o<

Any idea how to resolve?

---

### Post by ZootHornRollo on 2010-04-17
have tried booting with ubuntu 9.10 live disc, gets to selecting 'try ubuntu' then end up on screen with flashing cursor - nothing happens with keyboard entry tho?

Tried with Mint Live disc.  Get Mint splash with progress bar for about two minutes then screen with flashing cursor.

---

### Post by ZootHornRollo on 2010-04-17
unable to download gparted live disc as sourceforge is down just now.

---

### Post by 3rdalbum on 2010-04-17
If you can get to a command-line, try:

```
sudo fsck /dev/sda2
```

If not, then do it from a live CD.

---

### Post by ZootHornRollo on 2010-04-17
i can get into a shell via recovery mode but there is no prompt.

only prompt i can get to is grub.

---

### Post by ZootHornRollo on 2010-04-18
have tried three different live CDs (Ubuntu, Mint and Gparted) none which get much further than selecting to install/try.

Can someone tell me how i can get into a shell?

---

### Post by john newbuntu on 2010-04-18
Well, using Ubuntu liveCD, it gives you the option to try without installing.  Use that option.  Wait for a while.  Once it completes, go to Application->accessories->terminal.
Then run the commands:

```
sudo e2fsck -C0 -p -f -v /dev/sda2
```
and
 ```
sudo e2fsck -f -y -v /dev/sdb1

```

---

### Post by ZootHornRollo on 2010-04-18
when trying to run the ubuntu live cd and selecting try without changes it gets to the glowing ubuntu logo then hangs.  All CD Drive and HD activity stop.

---

### Post by john newbuntu on 2010-04-18
I suppose you are not able to get to the memory test either from the liveCD.  If so, you could have tried that option first

---

### Post by ZootHornRollo on 2010-04-18
Booting from liveCD (Ubuntu) and using graphical safe mode i get this error screen :

[IMG]http://farm5.static.flickr.com/4015/4530664410_c94645482e_b.jpg[/IMG]

---

### Post by ZootHornRollo on 2010-04-18
will try memory test

---

### Post by ZootHornRollo on 2010-04-18
Memory test running and it does not look good.  Might eb useful if someone could confirm that for me tho as i don't really know what i'm looking at.

[IMG]http://farm5.static.flickr.com/4046/4530061141_3c77edf974_b.jpg[/IMG]

---

### Post by ZootHornRollo on 2010-04-18
still running - over 7m errors!

---

### Post by klemes on 2010-04-18
It's obvious that what you are facing is a hardware failure:memory problem for sure maybe even motherboard chipset error too.What you need to do is repeat the test with some good exchange memory modules known to work and if this fails then you are looking at a possibly 'fried' motherboard.Before you do that it would be wise to open the case and try to reseat the memory modules,and try to9 see if it is a poor contact problem but the possibilities of that are pretty slim.Seem you might need new memory modules and/or new motherboard,so things are not looking bright at the moment.

---

### Post by ZootHornRollo on 2010-04-18
> **klemes said:**
> It's obvious that what you are facing is a hardware failure:memory problem for sure maybe even motherboard chipset error too.What you need to do is repeat the test with some good exchange memory modules known to work and if this fails then you are looking at a possibly 'fried' motherboard.Before you do that it would be wise to open the case and try to reseat the memory modules,and try to9 see if it is a poor contact problem but the possibilities of that are pretty slim.Seem you might need new memory modules and/or new motherboard,so things are not looking bright at the moment.

Thanks.

Have identified that one of my two 256mb DIMMS has failed.

i can temporarily use one of the 1GB dimms from my main pc unitl i get some replacement sticks.

Thanks again.

---

