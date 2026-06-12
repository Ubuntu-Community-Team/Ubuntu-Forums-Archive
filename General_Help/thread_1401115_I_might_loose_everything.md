---
title: "I might loose everything"
date: 2010-02-07
forum: General Help
---

### Post by Keaton_Brown on 2010-02-07
What i really need to know is if there is a way to access a Ubuntu file system on a hard drive from a live CD. When i acess it now it just shows the Windows files on it, and i cant access the Ubuntu partition.
What happened was this:
I was trying to install Ubuntu on an external hard drive. I moved all the settings to the Hard drive so i didnt think it would affect my other drives. I mustve missed one of them because insteading of loading GRUB like it normally does, it came up with GRUB error 21 and did nothing. I tried to fix it, but nothing worked. I finally decided to unplug everything except the external and install it from there, so id atleast have a functioning desktop. As it turns out, my comp doesnt suport USB booting. So the only way i can use my computer is by Live CD. I was trying to fix things so i had both hard drives power supply unplugged.  being slightly drowsy from staying up late that night, I plugged them in while my computer was on. the first one went in just fine, no problems. The second one though, also my master drive, i was having troubles pluging in. while i was turning it to fit in, it made a big spark and shocked my master drive. That drive had my MBR and Windows on it. Now It cant find a MBR, and i cant access the ubuntu partition on my slave drive. Is there any way to save this?? im 99.9% sure ive screwed myself over hardcore epically, but im hoping to save at least 1/2 my data.

---

### Post by electricFan on 2010-02-07
You should already be able to access the Ubuntu file system from a live cd.

Perhaps try another live CD such as puppy linux to access the existing filesystem.

That's really all I have to offer, hopefully someone else can help.

---

### Post by Keaton_Brown on 2010-02-12
> **electricFan said:**
> You should already be able to access the Ubuntu file system from a live cd.


Thats just the problem though. it only accesses the windows partition on it, but if i open the partition editor it only finds one partition on it.

but ive never heard of puppy linux before so ill google that and give it a shot

---

### Post by Keaton_Brown on 2010-02-13
Yeah Puppy Linux was a definate failure. i downloaded the new one on my laptop and burnt a cd with their recommended program, at the correct speed. i put it into my desktop and booted from the disk. it came up with the puppy linux screen, i can access the boot menu, but other than that it does nothing. it just sits there and says "loading". i left it on overnight and it still didnt do anything. so im going to need a different live CD. Or if theres a way to access a filesystem from a ubuntu live CD i need that.

---

