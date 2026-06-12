---
title: "Problem with Ubuntu Install (Partitioning)"
date: 2010-03-11
forum: General Help
---

### Post by ibex333 on 2010-03-11
Well, I am trying to install Ubuntu Netbook Remix on my Acer Aspire One and I cannot understand how partitioning works here.

_**Please feel free to ignore the part in quotes, and skip below...**_

"I really tried, to understand how to do this from guides and FAQ's but there is nothing helpful that I could find. I gotta side track and b*tch a little, because I keep seeing on various pages and forums how Ubuntu guides are supposedly very simple, user friendly and simple to understand, but apparently this is very much not so. I am by far not a computer illiterate person, having fixed, repaired and assembled a very large number of PCs for various people (in Windows environment though) and when I cannot get through a simple Ubuntu installation, there's clearly a problem with the guides.
Perhaps the info I'm looking for is there, but clearly it's all hidden, instead of being easily accessible as it should be.

My apologies, but I just had to express my frustration and get this out of my system."

Back to the topic at hand. During install, "partmon" or whatever it's called asks me to create a partition. Naturally that is what I do, but then I get a message about a swap file and I cannot proceed. In the Ubuntu install  guide it says that the swap file is used sort of like RAM if I understand correctly. Well that's fine, and I'd like to make one, but I cannot because the guide doesn't bother to explain in detail, what the heck is ext4,3,2, ReiserFS, JFS, XFS and all that other stuff... It doesn't explain what /, /boot, /home, /tmp, /usr and the rest are... All it says is that for a home user it is best to use /user or /home. I used /home and created a partition, but how the heck do I create a SWAP partition? Do I use ext4 for it or something else? Does it have to be a primary or a logical one? How big does it have to be? I am completely lost, and I don't know where to find a guide on this... I dont want to use a guided install. I want to KNOW, and UNDERSTAND exactly what I am doing and why. Thanks.

I used the guide located here: [https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/module-details.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/module-details.html)

---

### Post by PRC09 on 2010-03-11
I think the instructions you are trying to use are way out of date there.Everything now is done via Graphical Install on the live CD or Live USB drive...See link below....


[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by ibex333 on 2010-03-11
Hmm.... That is the thing... My install process for Ubuntu Netbook Remix is completely different. I have the latest version of UNBR and the reason why I chose to install it was because it is supposedly "one of the best distros for netbooks and easy to use".

I am now up and running, since I figured out by trial and error how to create a swap partition. The only thing is I made both partitions "primary" and I dont know if this was the right thing to do.


EDIT: Although I am not happy about the install process, I just want to say that the guys behind Ubuntu did a really great job on this OS. Once installed it looks and works GREAT. I didnt even expect it to be this good. I tried Linux several years ago, and quickly uninstalled it because it was somewhat ugly(no offence to the devs) and pretty hard to use beyond the most basic apps. This time around, it looks like a HUGE improvement, and I actually have the desire to keep it on my PC, and learn it in depth.

---

### Post by mamdez on 2010-03-31
I am having a related problem but a bit more complex.  The ubuntu install guide that has detailed information about partitioning is located here: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) and it answers all the questions that I had about partitioning.  

Actually though, I was using the guided graphical install and was trying to install Ubuntu Netbook Remix onto an Acer Aspire One with no operating system present (previously had factory installed Linux Linpus Lite which suddenly crashed and disappeared) according to the message I get before the partitioning starts.  When the drive is partitioned and formatting begins, I get an input/output error.  I have tried selecting both "ignore" and "retry" as well as manually selecting the partition or just retrying using the default guided selections.  All attempts end in the same:  the input/output error comes up again and after a long time finally a message appears saying unable to install into the preselected partition.  I don't need a partitioned drive, and I have tried using all the freespace but I still get the same result.  Right now I am running the Uubuntu Netbook Remix O/S on a 4 GB USB stick and it is working just fine, but I would like to install it to my hard drive where I have more space and could get my system started quicker than doing the usb boot bios selection every time.  Any suggestions on how to make this happen? 

 Oh by the way I tried running the boot disk that came from the factory with the original OS and I went through all the steps to recover the system and the final step was to restart and when the machine restarts, I am back where I started, unable to boot, and no sign of the O/S.  I don't know if this is an indication of a deeper hardware issue or not, but like I said before, I am able to run Ubuntu from the USB stick and it is working just fine so far.

---

