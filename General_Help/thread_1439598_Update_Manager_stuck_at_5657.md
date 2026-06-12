---
title: "Update Manager stuck at 56/57"
date: 2010-03-26
forum: General Help
---

### Post by altjx on 2010-03-26
For some reason, when I run Update Manager, it gets stuck at 56/57, and when I click cancel, I get this. 

```
Failed to fetch http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2  
Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release  
Some index files failed to download, they have been ignored, or old ones used instead.
```

I've tried this, and this doesn't work either for some reason.
> PART ONE

Hi, with the help of many others I've been able to fix this problem for good.
First bring up a terminal (shell prompt) with something like "Konsole" found under "System Tools" in the applications bar. Second, completely purge anon-proxy with the following command:

sudo apt-get purge anon-proxy
<AND ENTER YOUR PASSWORD>

(The above command works on my Ubuntu 7.10 OS)
(OR if you are running a system that does not do the sudo thing type the following:

su
<ENTER YOUR ROOT PASSWORD>
apt-get purge anon-proxy


PART TWO

Then type the following:

export HTTP_PROXY=
export http_proxy=

<and you are done!>

Note: To save yourself trouble like this simply don't install anon-proxy; it just messes things up. Use something like Tor instead if you need an anonymous proxy route to the Internet. It is located at [http://www.torproject.org](http://www.torproject.org) or (formerly) [http://tor.eff.org](http://tor.eff.org). On their site they also note that you should download the software from their own site rather than Ubuntu's repositories because the software is the latest and greatest when retreived from torproject.org rather than the "universe" or "multiverse" repositories that the Ubuntu people provide.

If this still doesn't work then also try what Movius posted on [http://forums.debian.net/viewtopic.php?p=1209](http://forums.debian.net/viewtopic.php?p=1209) when he said the following:

PostPosted: 2007-11-11 13:57 Post subject: Another thing Reply with quote
Another thing you have to do is look with the "ifconfig" if the lo {loopback} is activated,
in affirmative case

gedit /etc/network/interfaces

and then

delete or put a # in the lines to make it like this :

# The loopback network interface
# auto lo
# iface lo inet loopback


Good luck

If you do choose to use Movius' suggestion make sure that you ONLY put the # sign in front of text; if you delete it and you want to change it back to what it was you may not remember what used to be printed there. The number sign (#) simply "comments out" the instructions, so that the instructions for the computer are translated to be simply notes to the computer operator rather than actual commands to act on. Following these instructions will fix your problem. It worked for me. But DO NOT do what Movius has said to do UNLESS Part One and Part Two combined are unsuccessful. Part#1+Part#2 should work on most every system. Use Movius' suggestion only if Part#1 and Part#2 do not work for you.

Anyhow, I'm apt-getting away now. Yay! L8r

P.S. Regarding Movius' post: You can replace gedit with whatever text editor you want. The command runs a text editor which opens the file /etc/network/interfaces

---

### Post by ubername on 2010-03-26
There are a few threads on this now. I wonder how to get google to fix this. it used to work. I solved it using squid as a proxy. See this:
Google chrome (dev) sources.list problem
[http://ubuntuforums.org/showthread.php?t=1430453](http://ubuntuforums.org/showthread.php?t=1430453)
__________________

---

