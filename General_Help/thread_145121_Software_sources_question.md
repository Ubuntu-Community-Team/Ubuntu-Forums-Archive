---
title: "Software sources question"
date: 2006-03-15
forum: General Help
---

### Post by snooker on 2006-03-15
Hi ... I have been reading a lot for this OS Ubuntu in the last few days  , There only so much that I can read before I go blind :mrgreen: , Any ways , I like to know your opinion on this matter that I have , From the ( Repo) Synaptic Package Manager area >>> The Software Preferences , I like to know is it wise to have everything check off for the "Software Sources" ? Because I notice from the default setting that it wasn't ,  Could someone please explain some details about it , Thanls

---

### Post by Sutekh on 2006-03-15
I assume you mean is it okay to use the universe and multiverse repository sources?

I'll try to explain from what I've learnt in my short time with Ubuntu.  Hopefully I'm not too far off the mark.

The Ubuntu repositories have 4 sections; **main, restricted, universe and multiverse**.  By default only main and restricted are enabled for use in Synaptic.

The software that you download from these repositories is supported by Ubuntu and includes updates and bug fixes.

The universe and multiverse repositories are disabled by default as they are unsupported by Ubuntu.  They do however contain a huge (well over 17000 I think) amount of software packages.  You can enable if you wish, just be judicious and careful about those packages you install.

The [Masters of the Universe (MOTU)]("https://wiki.ubuntu.com/MOTU") try to make sure that the sotftware is bug free in the universe repository, but as you can see it is a big job.  The multiverse is probably install at your own risk.  At this point in time, I don't think I've ever needed to install anything from the multiverse.


Then there are also the **backports** repository.  This repository is enabled after the final release of an Ubuntu release.  They basically provide a 'back-door' or newer software to find its way into an older release.

---

### Post by snooker on 2006-03-15
Hey Sutekh , First off I like to thank  you for your description , It gave me a better understanding of the Ubuntu repositories , Still I have lots to learn about it but , People like you makes it easier for me to understand it , Thanks

---

