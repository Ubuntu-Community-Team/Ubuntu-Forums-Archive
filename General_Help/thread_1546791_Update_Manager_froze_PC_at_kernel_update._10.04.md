---
title: "Update Manager froze PC at kernel update. 10.04"
date: 2010-08-05
forum: General Help
---

### Post by Maliron on 2010-08-05
OK, I have searched through the forums here and didn't find much pertaining to my issue..

I started an update from the Update Manager. There were lots of updates to do, so I let it do it's thing. Everything was going fine until it got to what appeared to be a new kernel. It got about 2/3 of the way through the progress bar, and the entire system hung. No drive access, no caps light when I hit the caps-lock key, could get to a terminal or anything, so I had to hard power off.

Everything booted fine, and when I launched the Update Manager again it said something about a partial update. I clicked yes without thinking and it started doing it's thing. I tried to cancel the partial update to do some more research on it first, but it wouldn't really stop. It continued and eventually told me there were no updates that needed to be done.

Now when I run the update manager, it doesn't list any updates. 

Did it actually finish all the updates and I am safe? How do I know? I come from a Gentoo background so I am used to updates breaking lol, but I am not familiar with doing my sanity checks in Ubuntu and how to make sure everything is cool. 

I tried to do a:

```
 sudo dpkg --configure -a 
```I am not entirely sure what that command is supposed to do, but it drops back to the prompt immediately without any output.

Thanks in advance for any help!

---

### Post by linux18 on 2010-08-06
the sanity check for synaptic in ubuntu (it's quite long):

 ```

sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center && sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 

```

---

### Post by linux18 on 2010-08-06
oops double post

---

### Post by Maliron on 2010-08-12
Thanks for the reply! Sorry I have been a bit busy lately with work so have not had a chance to look at this.

First of all I had to break up all the killall's because once one fails because the process isn't running, the && doesn't allow the others to progress.

Second, I assume it is supposed to purge anything the shows in a "dpkg -l" that starts with an "rc" of which there were none. After the autoremove and the rest there were some, so I ran through the steps again, now it's back to showing none.

Understand all the step, except for the rc, what are those packages, what does the rc signify, and why is it needed to purge those?

I have ran through everything, and it's all coming back fine now, so it's reasonably safe to say I have a sane system, and nothing was broken from the freeze up during the update?

---

### Post by linux18 on 2010-08-12
Ok, a summary of the script
the killall's were supposed to be || not &&, but you seem to have figured it out 
its actually "^rc" not "rc", basically the command finds packages that were downloaded but not needed
clean and autoremove are redundant but commonly grouped together and both purge package caches
-f install will download and install packages to fix dependancies 
update is not necessary 99% of the time but is absolutly essential, so its included
--fix-broken upgrade does exactly what it sounds like

Its nice to see someone interpreting commands instead of just running them like many newbies.
One question, why switch from gentoo to ubuntu? it seems like switching a computer from windows server 2003 to windows 7 if you know what I mean.

---

### Post by Maliron on 2010-08-26
Thanks for the info! I have always verified what I was being told to run, just a good habit to be into.

Gentoo was great, I loved it, and ran it for many years. I always did stage 1 installs because I thought it was more fun that way (yes I know, I have a sick idea of what "fun" is). The thing that really got me started on Ubuntu is what a monster portage has turned into. Package maintainers started really letting things slide, and the direction it was heading was really starting the get annoying. Things making it into the "Stable" tree that had no business being there, and things not making it that should. I would end up having such a convoluted installation with too many package.masks to build 10 packages from the "unstable" tree just so I could get perl 5.10. Things of that nature. It just got to be way to much to administer. Doing an "emerge world -uDa" and then the "etc-update" sifting through the 100+ config files, merging them into new configs, then the inevitable "rev-dep-rebuild" to fix all the things the update broke. That's if any of the updates didn't have problems compiling! It would take the better part of the evening just to do what takes 10 minutes in Ubuntu, which has most, if not all, of the versions I needed for things in binary already.

In short: beastly, bloated, broken portage was the end of the Gentoo era imho. *sniff

I still love the three command easy install of Gentoo though. [http://bash.org/?464385](http://bash.org/?464385)

---

