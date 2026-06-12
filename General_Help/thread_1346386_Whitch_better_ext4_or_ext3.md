---
title: "Whitch better ext4 or ext3"
date: 2009-12-05
forum: General Help
---

### Post by MMALLOW on 2009-12-05
Hi
 
i want instaal ubuntu 9.10 
 
which better ext4 or ext3
 
my frnd told me ext3 better beacuse ext4 have some proplem with big files and not faster  and make bad sector in the future
 
second
 
i use laptop toshiba  , prosser pentum due intl 2.
 
Ram 4 giga
 
 
which better oubuntu desktop or ubuntu remix
 
olso if you have another kind of remx ph. Tell me
 
 
third
 
 
i instaled oubuntu 9.10 desk top on my lap top
 
but some times i heard  more sound outside from fan
 
and very haot air  that meaning some thing is heavy on prsesor
 
i dont kno what the thing is heavy'
pls help me  also if ican delete some thing to make ubunto faster tel me
thanks

---

### Post by Silent Warrior on 2009-12-05
And I seem to be first yet again.

I don't really know which EXT is best, but EXT4 has more bells and whistles and is more refined. Still, EXT3 works just fine.

I haven't looked too closely at the download-pages - I run Ubuntu Desktop myself, and it's listed quite early, as I recall - so I have no idea what specific remix you're referring to. But if you're running a laptop there still shouldn't be a need to install any netbook-variant of Ubuntu. Unless you've tried it and liked it better than the desktop-version, that is. (I haven't.)

As for the fan, I know that on my laptop (Toshiba L300-somethingsomething) the fan kicks in when the CPU temperature reaches a little over 75C (no sooner) - understandably the exhaust would feel hot then, but it should get colder. This particular laptop has been A-OK running Linux for about 8 months, so that's probably nothing to worry about, unless you're the sort that likes to keep your computer/laptop running all day long, never turning it off.

---

### Post by Marvin666 on 2009-12-05
I've always used ext3. My laptop was only shut off for more than 5 minutes, a few times over the few years I owned it. It gave out due to an unrelated water incident... Jaunty Xubunutu

---

### Post by MMALLOW on 2009-12-05
Also i have toshiba l300-ifr
 
but from where this hot or which program is heavy on prosesor
iwant to know to delete it

---

### Post by Silent Warrior on 2009-12-05
You know, the CPU will heat up over time, no matter what you do with it. But one thing you could do is of course to make sure you're not running any desktop compositing (Appearance-settings -> Visual effects, select 'None'). If you have the chance to deactivate - I really don't dare suggest to uninstall - any indexing-process, that should speed you along. Look for Strigi, Beagle, or Akonadi in the System Monitor to see if they're running, or anything ending with -indexer. I haven't looked for the setting myself, so I don't know where to look in the Control Center.

---

### Post by fluffman86 on 2009-12-05
Ext4 is WAY faster than Ext3.  

If your laptop screen is less than 12 inches (30 cm) you might want to try out Ubuntu Netbook Remix.  Otherwise install the 64bit Desktop.

---

### Post by bumanie on 2009-12-05
ext4 is better, for a number of reasons that you can easily read about by doing a search with a search engine of your choice. I have been using ext4 since Karmic alpha 3 and found it to be stable and for the most part, faster than ext3.

---

### Post by akakingess on 2009-12-06
Also, you can install "top" or "htop" and run within a terminal to see if a particular app is taking up more than it's fair share of CPU or RAM usage for that matter. For installation and running of top/htop
```
sudo apt-get install top
```
or
```
sudo apt-get install htop
```
and then just open a terminal and type whichever app you chose to install, and this will tell you what processes are running and how much %-age wise CPU and memory each process is using.  This is just a FYI , by the way.

---

