---
title: "General doubts on raid0 and dualboot"
date: 2011-01-30
forum: General Help
---

### Post by balta on 2011-01-30
Hi there!
So, I am interested in getting two small and fast HDD and set them up into RAID0 to enhance the startup time of my system and, generally, of every program. 
Mainly I'd use this for Windows 7 x64 (my other OS) which I use mainly for games and some other stuff (photoshop autocad 3DSMax etc..) that I'd love to eventually end doing under linux using free software.
I got a few doubts on this that I'll write down here:

What's the difference (in terms of performance and support) of raid, fakeraid, hardware raid and software raid ?

How can I discover if my mobo supports hardware raid?

Is it worth it?

If it's not worth it, can I have windows in raid0 and ubuntu "normal"?

Is it dangerous or risky (more than a normal installation)  to have raid0 set up?

In case I do decide to set up both win an ubuntu on the same hdd raid0 how do I do it? Is the procedure different in base of the type (not number, I mean fake hw sw ...) of raid I choose?

Is there a better raid than 0 for performance?

Sorry for the very noob questions, I'm reading stuff on myself and I'll give me so answers if I find them.
It should not be a double post but well, I'm a (lazy) human too so It could be, in case I beg your pardon and please, redirect me.

Thanks for your time!

Edit:
Just in case: my motherboard is an *ASUS Rampage GENE II*. 
Reading a bit the manual it pops out that there is a section about RAID but it only refers to *Intel Matrix Storage support* and how to configure it from the Bios and from the *Intel Matrix Storage Manager ROM Utility* (graphic tool outside the OS). Am I correct assuming it would be an hardware RAID (which I was told has better performance)?
Also there is a JMicron something blablabla that pops out on the boot and I do believe it means something good for an hardware RAID. Am I correct?

Once again sorry for the noob questions\statements and for the WOT, thanks again

---

### Post by LoneWolfJack on 2011-01-30
> What's the difference (in terms of performance and support) of raid, fakeraid, hardware raid and software raid ?

raid is a general term, fakeraid and software raid are the same. for small arrays with few disks it barely makes any difference whether you use a software or hardware raid. the more disks, the more a hardware raid will pay off.

for complex raid levels like 5,6 and 10, a hardware raid controller will take the load from your CPU, offering much better performance.

> How can I discover if my mobo supports hardware raid?

if your mainboard cost less than say 400 bucks, it doesn't. some tyan server boards come with adaptec raid controller chips.

> Is it worth it?

for larger arrays and raid levels other than 0 or 1, yes.

> If it's not worth it, can I have windows in raid0 and ubuntu "normal"?

you can't use the same two discs as raid 0 in windows and as normal discs in ubuntu. but of course you can install one OS on the raid 0 and the other on an extra drive.

> Is it dangerous or risky (more than a normal installation) to have raid0 set up?

the failure rate for raid 0 multiplies with the number of discs. if any one disc of a raid 0 fails, your data is gone. 

> 
In case I do decide to set up both win an ubuntu on the same hdd raid0 how do I do it? Is the procedure different in base of the type (not number, I mean fake hw sw ...) of raid I choose?


unless ubuntu doesn't recognize your raid array, the installation procedure isn't any different from a normal install.

> Is there a better raid than 0 for performance?

no.

---

### Post by balta on 2011-01-30
Thanks for the quick and precise responce, une more question, less techinical tough: would you advice me to give it a try or not?
Thanks

---

### Post by oldfred on 2011-01-30
I am not a fan of RAID for desktops. For servers it is required, if serving many users and you want better uptime. But you use 5 or more drives with hardware RAID. Some mistakingly think it is a backup, but there is no backup. A deleted file is deleted from both places. RAID also adds a level of complexity which is more advanced.

For a desktop will RAID allow you to type faster, will your Internet downloads be faster? No for both and those are the main things most Desktops are used for.

The only slight advantage was if you are doing a lot of drive intensive activities, and now SSD's are a better choice for that on a desktop.

---

### Post by balta on 2011-01-30
Yep! Fair and square man! 
Thanks! I think I'll then just replace my dear old 5400rpm hdd with an sdd or a single 7200rpm ;)
Thanks!

---

