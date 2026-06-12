---
title: "Ubuntu Self-Destruction."
date: 2011-08-27
forum: General Help
---

### Post by joeyarnold on 2011-08-27
I bought a dual-core HP laptop at the Free Geek store around May 2011.  Yesterday, it started messing up. I had a bunch of video programs open. I had 17  GB free space. The computer froze. I forced it off. When I turned the computer  back on, it reverted from Ubuntu 11.10, back to 10.4. Everything on the HD was  deleted, or it at least looks that way. It even asked me to name the computer  and give it a password. I have never seen a computer do this before.

---

### Post by snowpine on 2011-08-27
Ubuntu 11.10 is pre-beta, if you think you have found a very serious bug (!!!) then definitely report it so it can get fixed:  [https://wiki.ubuntu.com/Testing](https://wiki.ubuntu.com/Testing)

On a practical level, a good first step is to boot from a Live CD/USB and try to recover any data/documents to an external drive. 

After that, it's your call--my recommendation if you really want to help test 11.10 is to run it in VirtualBox or install it on a separate partition as "dual boot."

---

### Post by howefield on 2011-08-27
Thread moved to "*General Help*"

---

### Post by nothingspecial on 2011-08-27
> **joeyarnold said:**
> it reverted from Ubuntu 11.10, back to 10.4.

I would say that is the problem. Why?, I don't know, but I'd suggest filing a bug.

---

### Post by joeyarnold on 2011-09-01
> **nothingspecial said:**
> I would say that is the problem. Why?, I don't know, but I'd suggest filing a bug.

My computer's partitions were rewritten. It went back to the way that it was when I bought it at Free Geek ([http://FreeGeek.org](http://FreeGeek.org)) back in May 2011. When replying back to me via email, they stated that my problem may be due to a script (a bug, error, loop, or something) that they are familiar with. My warranty is almost up but they said they are willing to try to find my lost files. We are talking almost 100 GBs of data that is lost. We are not just talking lost files. We are also talking about lost partitions. There seems to be programs capable of finding files. I am actually writing this from my broken computer. I have a small 4GB thumb drive (iPod) that I am saving things to right now. I don't want to save anything to my computer for now. Thanks for the replies, here.

I will have to eventually get technical support from Free Geek. However, in the meanwhile, I will contemplate finding these files manually, myself. Through, can my computer find almost 100 GBs of lost files and write back onto itself? Sounds like a tough job? I don't know what that would look like. I know it would be much easier if all those files were simply just in the recycling bin. I know how to press the button to restore things out of the recycling bin. 

Photorec seems to be a program that might be able to help.

---

### Post by Tyler H 0203 on 2011-09-01
Testdisk is also really useful in situations like that.

---

### Post by hawthornso23 on 2011-09-01
Sometimes when people set up a machine to sell on they set it up with a restore partition and some restoration scripts so that the operating system can be reinstalled back to mint condition easily. Sounds like there might have been something like that on your machine and it got triggered somehow. 

Since you got the machine from Free Geek and they seem familiar with the problem, My guess is that it was their misbehaving restore script that messed you up.

---

### Post by joeyarnold on 2011-09-01
> **snowpine said:**
> Ubuntu 11.10 is pre-beta, if you think you have found a very serious bug (!!!) then definitely report it so it can get fixed:  [https://wiki.ubuntu.com/Testing](https://wiki.ubuntu.com/Testing)

On a practical level, a good first step is to boot from a Live CD/USB and try to recover any data/documents to an external drive. 

After that, it's your call--my recommendation if you really want to help test 11.10 is to run it in VirtualBox or install it on a separate partition as "dual boot."


I don't have an external hard drive to export the lost files to. I have to find the lost partition, filesystems, the loss data, which is around 100 GBs and undelete them back onto itself, on the same hard drive. It says it has just about that much GBs of free space. I would love to see a program that could do that trick. I know doing something like that would be extremely dangerous, risky, but can it be onde at all that way?

---

### Post by snowpine on 2011-09-01
This doesn't sound like an Ubuntu bug. It sounds like your computer had a "system restore" function from the manufacturer that accidentally got activated. 

If your data is valuable to you, then you should spend a little bit of $$ to have a reliable backup. I hope you are able to recover your data, but it sounds like you need help from the manufacturer to figure out what happened. Good luck! :)

---

### Post by pqwoerituytrueiwoq on 2011-09-01
can you get a gparted screenshot?
it is possible it could have not really done anything to your data and may just be unaccessable and it is booting a live iso off the hdd on a recovery partition
this is just a shot in the dark it is a slim chance

---

### Post by joeyarnold on 2011-09-01
> **snowpine said:**
> This doesn't sound like an Ubuntu bug. It sounds like your computer had a "system restore" function from the manufacturer that accidentally got activated. 

If your data is valuable to you, then you should spend a little bit of $$ to have a reliable backup. I hope you are able to recover your data, but it sounds like you need help from the manufacturer to figure out what happened. Good luck! :)


Free Geek email-replied me the following, stating that it sounds like an OEM-Config script error which creates a new default user account (brand new computer full of "free space" apparently) since I can't find my apx. 100GBs of files, data, file-systems (and even a different operating system: It went from Ubuntu 11.10 back to 10.04):


"It sounds like you may have run a script that is included with our machines called 'oem-config', which creates a new default user account that you get to name, as well as a couple of other configuration options.  The bad news is that oem-config typically removes the old home directory and all of its contents.  The good news is that we are typically able to recover data lost in such a manner."

"Since you got this machine in May of this year, it sounds like your warranty is almost up.  As a courtesy, we'll be happy to extend your warranty to cover this service if you're able to bring in to our Tech Support shop in the near future."

---

