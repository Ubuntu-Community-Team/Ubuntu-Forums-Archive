---
title: "My system weights 160 GB. more than it used to."
date: 2010-07-08
forum: General Help
---

### Post by pato wlmc on 2010-07-08
Well, this is my problem. I have a 320 GB. HDD

I used to dual-boot, windows 7 and Ubuntu, but like a month ago, i decided to finally kill windows, so when i finished doing so, i had 160 GB. of free space. I never resized my ubuntu partition, since it had like 80 GB. of free space.

Yesterday, I re-compiled my kernel, mainly to enable FrameBuffer in  the console. So i decided it was time to resize my partition, to use the whole HDD.

Turns out, that i had a little bit of problems compiling my kernel, and yes it took really a lot more than i thought ( I had to compile it twice ) but finally i got it working.

Then i was ready to resize my partition, so y clicked the "REZISE/MOVE" button; and just then i realized that it was already 4:00 AM and i really had to sleep, since i was going to have my middle school Graduation event tomorrow morning, so IGNORING THE BIG ADVISE in front of me, telling me that it was potencially dangerous to cancel the frocess, y clicked cancel.

Everything seem fine, so i just when to sleep. Today afternoon i was going to resume the process i lefted incomplete las night, but i almost split my coffe all over the screen when i saw that my ubuntu partition, was almost 180 GB. when it used to weight just 20 GB.

i still got some 100 GB. free, so is there anyway to get my system to it's normal weight?.

I really don't wanna miss all my info, specially my programs, and customized desktop, it really took me a wile to set compiz just the way i like it.

IM REALLY SORRY, I KNOW IT WAS MY FAULT, BUT I REALLY DON'T WANNA LOSE ALL THAT GB. NOR MY SYSTEM. sorry, so please don't come and tell me that i did wrong, i already know that, all i want now is a little help.

Thanks.

P.D. Sorry for the bad english, i'm not american jeje.

---

### Post by Ordes on 2010-07-08
so when i get this right... nothing happened... just that u have one big 180 gb partition.

1) you could just load up gparted and resize the partition

>>
> but you drive has 320gb and you killed of windows. so why dont use the whole hdd?
> your "/" and "/home" is probably in one partition. or is it divided?
  when you already go through the process of killing of windows and repartitioning, you might want to consider to make 2 partitons. one for "/" and one for "/home".
for this have 2 options.
1.) create partitions. and move "/home" to new one. resize the old partiton around 15-20 gb (system only), and than reinstall ubuntu. !! when choosing your home partiton >> DO NOT FORMAT !! after the reinstall copy your home files into your new created home user, and you have all the settings back. but stil need to reinstall the applications you downloaded. if u use sth like remastersys. you can back up your apps. and than make a fresh install with all your applications included.

2.) make 2 partitons. move /home to new "home-partiton" (google for how to move /home to new partition, enough tutorials out there). after this is done resize system partiton. with a 320gb disc i would make 15-20gb "/" rest for /home

---

### Post by StuartN on 2010-07-08
> **pato wlmc said:**
> i still got some 100 GB. free, so is there anyway to get my system to it's normal weight?.

Applications -> Accessories -> Disk Usage Analyzer is one way of finding how the space in the filesystem is being used.

The command du is versatile if you like the command line, e.g. **sudo du / --max-depth 1** would list just the size of the top-level directories (including the contents of every subdirectory within those totals).

You need to check if the unexpected usage is within /home or not as a first step.

---

### Post by pato wlmc on 2010-07-08
[QUOTE=Ordes;9562606]so when i get this right... nothing happened... just that u have one big 180 gb partition.

Well, kind of, cause now this partition is full, of... nothing? 

It.s like, i had 160 GB. free, and then BOOM! they're all full.

P.D Thanks for the other answers i'll try them, and tell how it went

---

