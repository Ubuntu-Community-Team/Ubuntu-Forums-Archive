---
title: "Dual Ubuntu boot, single /Home partition..?"
date: 2010-03-05
forum: General Help
---

### Post by Pott on 2010-03-05
Situation:

8GB SSD
#! on a 3.7GB partition, only 2.5GB used
Kuki (XFCE) on a 3.4GB partition, about 3GB used)

Both have their own /home folders within their individual /, but since I don't use this computer for documents/personal files, I figured it may be an idea to keep a 1GB partition just for my Home folder which would work for both distros.

Both distros are Ubuntu based. Crunchbang uses Openbox, Kuki uses XFCE. They both are running the same kernel right now too in fact.

So yeah... I know how to use Gparted to create the spare 1GB partition, but I'm not sure how to get both distros to move their /home over there...

I have the same usernames on each distros, which I hear may be an issue..?

Thanks!

---

### Post by ajgreeny on 2010-03-05
All the info you need is at [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) but I would be a bit careful about doing this, as you may find configuration problems using the same /home for both, even though they are both based on ubuntu.

It may be worth a try, of course, as long as you're aware of possible pitfalls, and if it does cause problems, just remove the separate /home mount from one of them, or alternately use separate /home partition but different usernames, eg **usercb** for crunchbang and **userk** for kuki; this will ensure your configurations are separate.  For things like ~/.mozilla/firefox and emails in ~/.mozilla-thunderbird you can always make a link from one /home/userfolder to the other, and thus keep just one version of those, the same for other config folders that keep personal files with the configuration.

---

### Post by oldfred on 2010-03-05
I also have the concerns that ajgreeny has on sharing /home. I install 3 versions of standard ubuntu, previous install, current install and beta. But rather than share /home I create a /data and all the folders in /home are in /data and linked in. I also have done as ajgreeny suggested and moved my firefox and thunderbird profiles to a shared partitions since I still occasionally dual boot winXP. My /home is still about 1GB but I have about 3 years of history on somethings still in it.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
I posted more detail on my version of above blog:
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by Pott on 2010-03-06
Well... I use the EXACT same configurations for my Firefox, but my main browser on both is actually Chrome. 
I also don't use any email app so there won't be much in there but actual files, very few of these. Pidgin etc... will be exactly the same too. Though I do think I have two different versions of Skype since #! came with its own Skype.

---

