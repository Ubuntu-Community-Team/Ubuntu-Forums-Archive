---
title: "Blocklists and Mobloquer"
date: 2011-06-04
forum: General Help
---

### Post by sking5 on 2011-06-04
I just installed Moblock/Mobloquer, but I want to make sure I am using the right blocklists. I was using PeerBlock before I switched to Ubuntu, and I must admit that I don't really know what I'm doing... haha. I know I need to block the educational institutions because I'm on a college campus, and I have been doing some web searches to find out what was recommended and I keep seeing "anti-p2p list" or something similar. However, I don't see that on the list on Mobloquer and I don't really know how to add more than what is already there or if it's even necessary. Help? :)

---

### Post by jre on 2011-06-07
You can add any URL in mobloquer (I think there is a "+" button below the lists). Have a look at iblocklist.com for a collection and description of all available blocklists.

You can also manually edit /etc/blockcontrol/blocklists.list and add the URL there (that's the same like making changes in mobloquer).

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **sking5 said:**
> I just installed Moblock/Mobloquer, but I want to make sure I am using the right blocklists. I was using PeerBlock before I switched to Ubuntu, and I must admit that I don't really know what I'm doing... haha. I know I need to block the educational institutions because I'm on a college campus, and I have been doing some web searches to find out what was recommended and I keep seeing "anti-p2p list" or something similar. However, I don't see that on the list on Mobloquer and I don't really know how to add more than what is already there or if it's even necessary. Help? :)

When you install it from the terminal, you are allowed to select all of the lists.. Did you do that? If not just reinstall it, and watch for the option to select additional blocklists.  You have bluetack and others you can use..   A whole bunch of them listed that you can select too. :) Make sure you use them all. That's what I recommended.  But do it from the installation.

---

### Post by jre on 2011-06-07
The technical point: instead of reinstalling you can simply do a "sudo dpkg-reconfigure blockcontrol". The result is the same. Currently I don't remember whether this way offers more blocklists then.

About blocklists: More is not always better:
[LIST=1]
[*]Every blocklist has its own purpose, using a blocklist which you don't need doesn't help, but blocks the good guys, too. In extreme, you may simply block 0.0.0.0-255.255.255.255, that's just the whole internet - 100% of the bad guys. But you surely don't want that.
[*]If you use too many blocklists you may be tempted to use excessive port whitelistings (e.g. per default already port 80 and 443 are whitelisted). So generally you have a massive protection, but at the same time you open some ports with no protection at all.
[/LIST]

---

