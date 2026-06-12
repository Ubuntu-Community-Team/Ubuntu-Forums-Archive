---
title: "Compiz problems in Lucid (Acer Aspire)"
date: 2010-06-23
forum: General Help
---

### Post by DavidDavidson on 2010-06-23
I know you're probably sick of this problem, I've done a search and it seems to crop up a lot. To be honest there were so many threads when I searched it made my head spin so the solution may be out there but I couldn't spot the wood for the trees.

I've just installed Lucid onto my Acer Aspire 5332. It's dual booting with Windows. Lucid replaced Linux Mint where compiz and all the eye candy worked with very little tinkering; so I know the laptop is "capable" of the effects. But all I get in Lucid is "Desktop effects could not be enabled."

Does Mint use different drivers than Ubuntu? Can anyone point me in the right direction?

Thanks, DD.

---

### Post by dazndom on 2010-06-23
what type of graphics card you running?

if nvidia look here [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG] 	 	      		 		 			 				 					tags: 180.06, drivers, nvidia,  proprietary, stabilit 					 					 					 					 					 					 				 			 			[[IMG]http://ubuntuforums.org/images/buttons/firstnew.gif[/IMG]]("http://ubuntuforums.org/showthread.php?goto=newpost&t=990978") 			 			 			                          			 			[nVidia latest  Drivers - How to install]("http://ubuntuforums.org/showthread.php?t=990978")

but what i did was do an update 3 or 4 times and it found the drivers and bingo ,   	 	

     		 		 			 				 					tags: codecs, dvds, flash, java,  sound, streaming 					 					 					 					 [ [IMG]http://ubuntuforums.org/images/misc/paperclip.gif[/IMG]]("http://ubuntuforums.org/subscription.php?do=viewsubscription&folderid=all#")  					 					 				 			 			 			 			 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") 			([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=766683") [2]("http://ubuntuforums.org/showthread.php?t=766683&page=2") [3]("http://ubuntuforums.org/showthread.php?t=766683&page=3")  ... [Last  Page]("http://ubuntuforums.org/showthread.php?t=766683&page=159")) 		
  		  		 			 			 				ubuntu-freak 			 		
 , this is a must see and do!!!!!!

and have you checked e17     	 	    [HOWTO: Customize Ubuntu A-Z]("http://ubuntuforums.org/showthread.php?t=856190") 			([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=856190") [2]("http://ubuntuforums.org/showthread.php?t=856190&page=2") [3]("http://ubuntuforums.org/showthread.php?t=856190&page=3")  ... [Last  Page]("http://ubuntuforums.org/showthread.php?t=856190&page=9")) 		  		  		 			 			 				sayakb

hope some of that works for you,
it takes a bit of practice searching these forums, but search for HOWTO " whatever"
usually works for me
good:pluck

---

### Post by clhsharky on 2010-06-23
What release of mint are you referring to?

---

### Post by DavidDavidson on 2010-06-23
Thanks for the replies, working my way through daz's links now there's some handy advice there.

The graphics card is "Mobile Intel® GL40 Express Chipset" apparently.

The release of Mint I had was Linux Mint 8, I think. I can't remember if compiz was enabled by default in Mint, but I didn't have to muck about with drivers and so on to get it working.

Cheers again for the help.

---

### Post by DavidDavidson on 2010-06-24
Have worked through the above, doesn't address the problem though...

From what I've seen Googling it's going to be more trouble than it's worth to try and fix too, which is a shame. If someone knows of a walkthrough that can get me back to a configuration somewhat similar to that in Linux Mint 8 I'd be grateful.

Failing that I should probably leave well enough alone haha.

---

### Post by DavidDavidson on 2010-06-25
Sorted!

Anyone in the same boat try this:

> **bpowell2005 said:**
> Haven't seen this on launchpad yet but:

Laptops with Intel graphics chips, post upgrade may not be able to  enable desktop effects (compiz). May also get a warning during boot of  "low res mode".

The problem is during the upgrade, all sorts of Nvidia drivers were  installed, and they're clashing with the Intel drivers. The workaround  (I know of two times this worked perfectly)

```
sudo apt-get --purge remove nvidia*
```You may want to apt-get  -s first (simulate) and make sure nothing unwanted is being removed.  Then reboot and Bob's your uncle.

Was in the "common bugs with workarounds" thread...

---

