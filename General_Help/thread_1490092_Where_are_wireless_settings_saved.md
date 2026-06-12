---
title: "Where are wireless settings saved?"
date: 2010-05-21
forum: General Help
---

### Post by Roasted on 2010-05-21
For various reasons, I have reinstalled Ubuntu 10.04 three times on my laptop. The 2nd time I reinstalled it, when I would connect to a wireless network, it would say connected but the network manager icon at the top panel said disconnected. What confused me is when I booted up during the 2nd install, it connected to my wireless without a problem. Is wireless info (saved networks, etc) saved in the home directory somewhere??

I didn't have the icon problem the first time, so I thought hmm, I have my stuff backed up, let's try it again except let's format everything this time. The third time I had no issues with the icon saying disconnected.

My partitions are split with /root and /home. The first 2 times, I did not format home. The third time I did. Even though the first time I didn't have this issue, I couldn't understand why it popped up the 2nd time. Now that I formatted EVERYTHING, the issue isn't there.

AKA:

1st try - no issues - did not format home.
2nd try - icon says disconnected when connected - did not format home.
3rd try - no issues - formatted everything.

Where are those settings saved?

---

### Post by dcstar on 2010-05-21
> **Roasted said:**
> For various reasons, I have reinstalled Ubuntu 10.04 three times on my laptop. The 2nd time I reinstalled it, when I would connect to a wireless network, it would say connected but the network manager icon at the top panel said disconnected. What confused me is when I booted up during the 2nd install, it connected to my wireless without a problem. Is wireless info (saved networks, etc) saved in the home directory somewhere??

I didn't have the icon problem the first time, so I thought hmm, I have my stuff backed up, let's try it again except let's format everything this time. The third time I had no issues with the icon saying disconnected.

My partitions are split with /root and /home. The first 2 times, I did not format home. The third time I did. Even though the first time I didn't have this issue, I couldn't understand why it popped up the 2nd time. Now that I formatted EVERYTHING, the issue isn't there.

AKA:

1st try - no issues - did not format home.
2nd try - icon says disconnected when connected - did not format home.
3rd try - no issues - formatted everything.

Where are those settings saved?

/etc/NetworkManager
~/.gconf/system/networking

---

### Post by Roasted on 2010-05-21
> **dcstar said:**
> /etc/NetworkManager
~/.gconf/system/networking

Well, root was formatted, so /etc would have been nuked. That leaves the gconf system networking portion. Hmm.... 

Do you guys think that could have aided in any errors? I can't see how I had problems with 1 install w/ same home directory, and at the same token it worked fine on another install w/ the same home directory. The only "problem" I had was network manager saying I was disconnected when I WAS connected...

*shrug*

---

