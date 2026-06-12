---
title: "Confused about Advance option in Partition Editor"
date: 2009-09-09
forum: General Help
---

### Post by rmcellig on 2009-09-09
I have an external 500GB USB hard drive that I just erased. I would now like to create a partition but when I click on the advanced tab I get a list of options. Which one should I choose if I am going to use this drive to clone my Ubuntu drive with Image files?

---

### Post by baseface on 2009-09-09
gpt looks good.

---

### Post by plucky on 2009-09-10
> **rmcellig said:**
> I have an external 500GB USB hard drive that I just erased. I would now like to create a partition but when I click on the advanced tab I get a list of options. Which one should I choose if I am going to use this drive to clone my Ubuntu drive with Image files?

Why are you trying to create a partition table?

Just delete the partition and then the space becomes un-allocated.

Select the unallocated space, right click and select **new**.Then you can create whatever partitions you need (primary or logical) and whatever filesystem you require.**You don't need to create a partition table!!!**


Good Luck

---

### Post by rmcellig on 2009-09-10
Thanks Plucky! I am new to this so I am still learning which I really enjoy. I tried cloning my drive to the 500GB USB drive using Clonezilla on the Parted Magic live CD. I could harly read what was written in Clonzilla and thus failed to clone properly. Maybe there is an easier way to do this, or is it that my head is somehow not wrapping around all this stuff.

It can't be this hard. Is there something that I should use instead of Clonezilla that may be simpler and more intuitive. Thanks for all the help and patience!!

---

### Post by rbc on 2009-09-10
I agree that Clonezilla can be a bit daunting at first, but after the first couple times it will be second nature. Clonezilla can make two different types of "copies", an image or a clone. If you are cloning your internal hard drive (probably recognized as /dev/sda) to the external drive (probably recognized as /dev/sdb), then there is no need to create as formatted partition first. Is there a particular step that is giving you problems?

---

### Post by rmcellig on 2009-09-10
> **rbc said:**
> I agree that Clonezilla can be a bit daunting at first, but after the first couple times it will be second nature. Clonezilla can make two different types of "copies", an image or a clone. If you are cloning your internal hard drive (probably recognized as /dev/sda) to the external drive (probably recognized as /dev/sdb), then there is no need to create as formatted partition first. Is there a particular step that is giving you problems?

I guess that all the info that came up confused me. I can't remember exactly what the text said but I was afraid that I might do something wrong. If there was something out there with a nice GUI and was simple to understand, that would be great. 

On the PC side, I find Norton Ghost really easy to us and on the Mac side, Superduper is a no brainer. It creates a bootable backup which is great. I have it scheduled to backup every morning around 1am. Would be nice if I could do something similar with Ubuntu.

---

### Post by rbc on 2009-09-10
Have a look here:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
Or let me know if you want further help with Clonezilla.

---

### Post by rmcellig on 2009-09-10
That link you posted is so helpful. With Simple Backup it looks like I can use it like I use Time Machine on my Mac. Pretty exciting. Thanks rbc for your continued help. Like I said before, I come from a GUI background having used Macs for years so I am always looking for GUI ways to accomplish things whenever possible. Another plus doing it this way is that I can show my Mom who is running 8.10, some cool apps that she can understand.

---

