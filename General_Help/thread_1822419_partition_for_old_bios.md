---
title: "partition for old bios"
date: 2011-08-10
forum: General Help
---

### Post by warped4sure on 2011-08-10
I may be in over my head, acquired an old gateway 2000,p55c-166 less the hdd. i had a 40Gb seagate st340016a and put it in. The bios auto-detected it, except it only saw 8455Mb of it. Since i'm an idiot, i didnt discover this until after i attempted to install Lucid 10.04. It acted as though it installed, but gave me a grub loading wait-error 18.
   Still being an idiot, I tried installing dapper or something even older, with the same or similar results. Finally looked at my bios and see how the hdd was detected. Then used a live ubuntu cd and accessed the gparted app.
   Not being any more than a noobie as experience goes, I concluded that what bios saw and what ubuntu saw could have caused a hiccup in the mbr. So I think partitioning is required. Have never attempted anything like this and only have vague idea of whats required. I have burnt a "Gparted-Live-CD" and looked things over with it.
   Dont intend to run anything but 1 distro of linux on it so I guess a primary partition plus an extended partition broken into logical partitions is required, or am I already getting into deep doo-doo? 
  Anyone interested in holding my hand and walking me through this project??

---

### Post by warped4sure on 2011-08-10
I may be in over my head, acquired an old gateway 2000,p55c-166 less the hdd. i had a 40Gb seagate st340016a and put it in. The bios auto-detected it, except it only saw 8455Mb of it. Since i'm an idiot, i didnt discover this until after i attempted to install Lucid 10.04. It acted as though it installed, but gave me a grub loading wait-error 18.
   Still being an idiot, I tried installing dapper or something even older, with the same or similar results. Finally looked at my bios and see how the hdd was detected. Then used a live ubuntu cd and accessed the gparted app.
   Not being any more than a noobie as experience goes, I concluded that what bios saw and what ubuntu saw could have caused a hiccup in the mbr. So I think partitioning is required. Have never attempted anything like this and only have vague idea of whats required. I have burnt a "Gparted-Live-CD" and looked things over with it.
   Dont intend to run anything but 1 distro of linux on it so I guess a primary partition plus an extended partition broken into logical partitions is required, or am I already getting into deep doo-doo? 
  Anyone interested in holding my hand and walking me through this project??

---

### Post by Matt__ on 2011-08-10
Sounds like an option if you cant update the bios to detect the whole drive.
Partitions for root, home, and even music, downloads etc etc.

Your machine can take up to 256Mb RAM (I am fairly reliably informed) 2x128.

I have a dell with similar spec, 144Mb ram, 224 Mhz cpu 4.5Gb HDD that  runs a minimal install of 8.04 fine...its no speed demon but usable,  runs flash and tux paint mostly for a 4 year old :smile:

_[Bios flash here]("http://support.gateway.com/support/drivers/getFile.asp?id=14781&dscr=BIOS%20revision%201.00.07%20DQ0T&uid=314355599") _

_[minimal cd releases]("https://help.ubuntu.com/community/Installation/MinimalCD")_

and some advice on [U][installing on low ram system]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
  
[/U]Anticipate a long and interesting project lol and good luck

/edit: you might also consider [ DamnSmallLinux]("http://www.damnsmalllinux.org/download.html")

---

### Post by lazerking9 on 2011-08-10
[EDIT BY USER] Sorry, posted in wrong thread ;) feel free to delete this

---

### Post by oldos2er on 2011-08-11
First thing I would do would be to look for a BIOS update.

---

### Post by AgentZ86 on 2011-08-11
No ! the bios does not matter and Ubuntu should use what is called dynamic overlay to create the proper partition.

The live ubuntu CD's already have Gparted on them so just a matter of selecting the correct partition type and also be sure to select a home partition, typically just use the / selection from the pulldown menus during the partitioning process.

You may have to google how to setup the partition or partition tool with Gparted or Ubuntu in order to make use of the whole hardrive

This was typical on older computers that hard drives larger then 20GB had to use a partition tool that came with the drive to setup dynamic overlay

I don't fully understand what the partition tool actually did but the bios always said stupid stuff when booting and gave the wrong drive info, however the partition tool took care of this.

I think in your bios you can also select manual user input and as long as you know the correct heads/sectors of the drive you can put that in manually.

There is ONE other setting that I can't remember in the bios that also worked to get older drivers and older CD's working. I think it was to change the setting to something like PIO instead of DMA or something like that.

You may want to fool with your bios setting some more and/or find out more about setting up the partition but I'm quit sure it can be done just a matter of getting the right info to partition the drive properly.

I hope this helps a little :popcorn:

---

### Post by warped4sure on 2011-08-11
> **Matt__ said:**
> Sounds like an option if you cant update the bios to detect the whole drive.
Partitions for root, home, and even music, downloads etc etc.

Your machine can take up to 256Mb RAM (I am fairly reliably informed) 2x128.

I have a dell with similar spec, 144Mb ram, 224 Mhz cpu 4.5Gb HDD that  runs a minimal install of 8.04 fine...its no speed demon but usable,  runs flash and tux paint mostly for a 4 year old :smile:

_[Bios flash here]("http://support.gateway.com/support/drivers/getFile.asp?id=14781&dscr=BIOS%20revision%201.00.07%20DQ0T&uid=314355599") _

_[minimal cd releases]("https://help.ubuntu.com/community/Installation/MinimalCD")_

and some advice on [U][installing on low ram system]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
  
[/U]Anticipate a long and interesting project lol and good luck

/edit: you might also consider [ DamnSmallLinux]("http://www.damnsmalllinux.org/download.html")
tnx for your response, looked at flash update to bios and found it primarily addressed an issue of booting from cd-rom which isn't issue for me.
regards the ram, it looks like iv'e got 192mb (64+128) but your advice about smaller linux distro may be well placed Thanks again

---

### Post by warped4sure on 2011-08-11
> **oldos2er said:**
> First thing I would do would be to look for a BIOS update.
Thanks for response- looked at bios update, it appears to deal with a cd-rom boot issue mainly. I dont have that problem.  Thanks again, warped4sure

---

### Post by oldos2er on 2011-08-11
Can you manually input the hard disk info into the BIOS setup?

---

### Post by warped4sure on 2011-08-11
> **AgentZ86 said:**
> No ! the bios does not matter and Ubuntu should use what is called dynamic overlay to create the proper partition.

The live ubuntu CD's already have Gparted on them so just a matter of selecting the correct partition type and also be sure to select a home partition, typically just use the / selection from the pulldown menus during the partitioning process.

You may have to google how to setup the partition or partition tool with Gparted or Ubuntu in order to make use of the whole hardrive

This was typical on older computers that hard drives larger then 20GB had to use a partition tool that came with the drive to setup dynamic overlay

I don't fully understand what the partition tool actually did but the bios always said stupid stuff when booting and gave the wrong drive info, however the partition tool took care of this.

I think in your bios you can also select manual user input and as long as you know the correct heads/sectors of the drive you can put that in manually.

There is ONE other setting that I can't remember in the bios that also worked to get older drivers and older CD's working. I think it was to change the setting to something like PIO instead of DMA or something like that.

You may want to fool with your bios setting some more and/or find out more about setting up the partition but I'm quit sure it can be done just a matter of getting the right info to partition the drive properly.

I hope this helps a little :popcorn:
Thanks for responding. Yes I know that ubuntu live CD'S have gparted on them, I guess I was concerned about the hdd maybe being mounted by the ubuntu disk and if so it might reduce flexibility of partitioning. Might have been a silly thought, but I have never done any thing like this before so thought I'd burn a stand-alone Live Gparted CD and use it.
     The bios does detect correct number of cylinders,heads, and sectors but doesn't translate that into the correct capacity. You also mentioned that there might be something else that might manually be set for the drive - perhaps you were thinking Of enabling LBA and setting a number into it???
     I did have another thought (always dangerous), Perhaps I could find a hdd smaller than the 8.5Gb limit - set it as the master, then put the 40Gb in as a slave, partition it as one big extended partition chopped up by logical partitions each smaller than the 8.5Gb bios limit. I would think that the bios would see it as a bunch of drives or at least the ubuntu install would see them that way. Assuming the ubuntu kernel and boot installed on the master I would expect it to automatically partition the logical drives to its requirements. Dont know - I imagine I know just enough to be dangerous. Anyway being lazy and all-if it would work it sounds much easier.    Thanks much for your input.  warped4sure

---

### Post by warped4sure on 2011-08-11
> **oldos2er said:**
> Can you manually input the hard disk info into the BIOS setup?
yes, can manually enter info, but bios auto-detects correct number of cylinders,heads,and sectors but doesnt translate that into the correct capacity. and if i manually try to configure the drive with correct capacity the bios regards it as an error and reports no drive on bootup. I think it has to do with an inability of older bios's to handle the larger numbers required in more modern hdd's

---

### Post by LowSky on 2011-08-11
Older equipment does have some limits. Viewing the size of a hard drive could be such a limit. You have to recall when windows XP was released it had issues with hard drives sizes, I think over 13GB originally.It was patched to see up to a 2-3 Terabytes.

I was surprised you could run a Ubuntu Live CD on such hardware.

---

