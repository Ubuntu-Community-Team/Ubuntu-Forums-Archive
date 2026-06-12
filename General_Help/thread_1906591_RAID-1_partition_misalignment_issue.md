---
title: "RAID-1 partition misalignment issue"
date: 2012-01-09
forum: General Help
---

### Post by chemnerd1 on 2012-01-09
Hello All!

First of all I just started using Linux for the first time 2 days ago so I am very new to pretty much everything and my computer experience has pretty much been limited to basic Windows functions with only a little command line experience so very basic click by click instructions would be very much appreciated.

I am a research scientist and we using a Linux 64 bit machine with Ubuntu installed to run some MATLAB scripts. I bought 2 3TB Lacie external d2 Quadra drives and I wanted to do a software RAID-1 for basic storage only. We load a ton of data on this computer so I just need them for storage with an automatic backup so I don't have to manually back up data every week. Pretty much I just need information stored on one drive to also be stored on the other so I figured a RAID-1 was the way to go.

My problem is that I used the Ubuntu Disk Utility to set up the RAID-1 but every time I do it the drives state "WARNING: The partition is misaligned by 3072 bytes. This may severely impact drive performance." When I click on the Multi-disk Device (the RAID-1) in the Disk Utility it says it is "resyncing". After 2 days the progress bar for the resyncing is only about 10% complete. When I try to start saving data to the RAID-1 the data will save but the Status of the array just changed to "Degraded" in angry red font. Also initially the "drive activity" lights were in sync for both drives but once the status was changed to "Degraded" the lights were out of sync.

I have heard that to avoid this I need to set up the RAID using the console and not the Disk Utility but I have no idea how to do any of this. I have read the online "how-to's" but they are above my head. One big issue I am running into is that I don't know how to partition the drives in the console or even how I should partition them including size and formats. The drives will be used only with the Linux Computer.

Thanks in advance for any help.

---

### Post by Double.J on 2012-01-09
Hi there and welcome to the forums! based on what you've said I'd agree that RAID 1 is the way to go over 5 or 10 - you only have 2 drives in the array and data protection is more important than data quantity? However i'll explain other aspects of data protection later.

in terms of RAID, I would say that RAID really should be configured before installation, or suring for software raid. I'd also go out on a limb here as you didn't ask, but I'd really not recommend installing Ubuntu 11.10 in a business/research environment, MY personal recommendation is debian squeeze. The documentation is a lot more detailed and the OS is designed for stability and reliability over "the latest thing."

Of course I'd recommend hardware raid if you could get the institution to pay for it ($200+), but as I'm guessing that's been ruled out, I'd say have a look through the debian documentation about setting up software raid on install. If you're really not feeling comfortable, i'd say spend the $40 on what Ubuntu calls "fake raid" - these are pci(e) cards and very easy to set up in my experience - the advantage is once they're set up, you can basically install using default partitioning settings if you like, but have a look at debians installation documentation and see what you think - you can always post here as well about it.

As I said at the start, RAID isn't the only way to protect data. One thing to remember- RAID only protects you against hardware failure - you say you don't want to do a weekly backup, concidering this is research I would say unwise - you should always have a copy of your data not connected to your machine - ideally in a different location altogether to protect it from things like theft and fire. 

If you can only afford 2 drives, I would actually say your data is safer using one of them as a separate backup drive, stored somewhere else than being used as a RAID drive, after all drives can go without warning, this balance tips at three drives.

It isn't just hard drive failure, fire and theft you need to worry about there's, err... human error - downloading malware, deleting files, formatting the wrong partition etc - all can cause loss of data, and in RAID1 what you do to one you do to the other

Just some things to think about.

---

### Post by chemnerd1 on 2012-01-09
Thanks for the response gnu/mirow

I really appreciate the information but the problem is that this computer isn't owned by my lab so I can't change it. It is part of the Computer Science and Engineering department who are helping us set up this research tool. The computer is running fine and seems stable enough for what we are doing, I just need to increase storage space. I wanted to do a NAS type system with parody but due to funding restraints as far as who we can order from and how much money we can spend I had to resort to just getting these 2 drives (the mobo doesn't have slots for more internal drives). 

So pretty much I just need to set this up on the existing infrastructure. If I have to I will just set these up as 2 independent drives and do manual backups but the RAID would just be more convenient. Also, each scientist has their own back-ups for data but we wanted to use this communal PC as a central back-up for everyone just in case someone personal drives went down.

The hard drives are set up now where I have firewire connecting the 2 drives and eSATA connecting the one drive to the PC (This PC does no have firewire on the mobo). I was able to RAID these fine in windows but linux is giving me this alignment issue. I have read this is caused by the Disk Utility program doing a crappy job of creating the RAID but I don't know another way to do it.

Thanks again.

---

### Post by Double.J on 2012-01-09
I'm afraid I just don't know how to set up software RAID on an all ready running system from the terminal. Sorry I couldn't be of more use - I've only ever done it from alternate installs for Ubuntu. 

Hopefully someone will be along shortly...

All the best :)

---

