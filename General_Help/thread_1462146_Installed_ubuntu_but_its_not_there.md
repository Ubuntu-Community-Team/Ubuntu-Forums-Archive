---
title: "Installed ubuntu but its not there?"
date: 2010-04-25
forum: General Help
---

### Post by DreamShardDev on 2010-04-25
Im having a problem installing ubuntu on my laptop. Basically i booted from live cd clicked install and Went through the process partioning it at 60 gb Microsoft 20 gb ubuntu went through the whole process and all it got to 100% finished and then it went into ubuntu (note the reboot message did not come up) after looking around ubuntu decided to make sure it was all good and I rebooted and basically windows booted up like normal. When i tried re-installing the ubuntu partioin is still there with all the files so i think it installed properly it just wont boot for some reason ??
 
Im totallly clueless as to whats wrong 
 
 tried sudo update-grub
didnt work
Any help would be appreciated

---

### Post by DreamShardDev on 2010-04-25
**Installed ubuntu but its not there?** 
Im having a problem installing ubuntu on my laptop. Basically i booted from live cd clicked install and Went through the process partioning it at 60 gb Microsoft 20 gb ubuntu went through the whole process and all it got to 100% finished and then it went into ubuntu (note the reboot message did not come up) after looking around ubuntu decided to make sure it was all good and I rebooted and basically windows booted up like normal. When i tried re-installing the ubuntu partioin is still there with all the files so i think it installed properly it just wont boot for some reason ??

Im totallly clueless as to whats wrong 

tried sudo update-grub
didnt work
 
Any help would be appreciated I am pulling my hairout at the moment!!:(

---

### Post by mike555 on 2010-04-25
What Windows os , XP,Vista or Windows 7 ?

---

### Post by louieb on 2010-04-25
Take a look at what happened - follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by Iowan on 2010-04-25
Threads merged.
From the Code of Conduct:> 
# Please do not cross post, or post the same thing in multiple locations.If you wish to have the thread moved, just ask. :)

---

### Post by coffeecat on 2010-04-25
> **DreamShardDev said:**
> it got to 100% finished and then it went into ubuntu (note the reboot message did not come up) after looking around ubuntu decided to make sure it was all good and I rebooted

You were still in the live environment all this time. It's interesting that a prompt asking you if you wanted to reboot didn't come up. As far as I remember, this always happens after the installation has finished, so I wonder if the installation didn't actually finish. As installing the grub bootloader is the last part of the installation process, perhaps this is why you can only boot into Windows. Are you sure you didn't close the installer window before it had finished?

> **DreamShardDev said:**
>  I rebooted and basically windows booted up like normal.

Yes - sounds as though grub hasn't installed properly.

> **DreamShardDev said:**
>   When i tried re-installing the ubuntu partioin is still there with all the files so i think it installed properly it just wont boot for some reason ??

Do you mean that you rebooted the live CD and went through the installation process again? Please clarify.

The link louieb posted will help. Just to clarify - you will need to boot into the live CD to run this script. You'll need an internet connection, of course.

---

### Post by Serpher on 2010-04-25
I think the most probable cause of this is you responded to a Window incorrectly or somehow accidental pressed something like Alt + F4 at the wrong moment. This happens to me a couple times using applications where you think you did something but for whatever reason you didn't do to something unnoticeable you did that messed things up. Try installing it again and read the instructions carefully around where the install "ended" for you.

---

