---
title: "Questioning wether drive is bad of if os is glitched"
date: 2009-12-20
forum: General Help
---

### Post by sofasurfer on 2009-12-20
I asked about this the other day but now I have more details to add.

Wifes Windows pc won't boot. It prompts for "enter BIOS" and "Boot Menu" then it goes to the Windows splash screen for about a second and then goes back to the prompt screen and repeats the loop. 

I slaved it up with a working drive containing Ubuntu. Both drives are recognized in BIOS but neither drive will boot.

I then put a Ubuntu Live CD in the drive and now am able to access the files on the Windows drive. But I have now way of copying the files to another hard drive since none will work with the funky Windows drive hooked up. So I took my DVD drive from my pc and installed it in wifes pc. Now I am able to copy files from dead Windows system onto DVD by accessing them with my Live CD.

So I am wondering what is wrong with the Windows drive. Obviously the drive is not dead because it does get to the splash screen fore a short time, and I am able to access the files from my Live CD. But it seems to me that there must be something more severe than just a glitched OS that causes other hard drives to not operate along side of it. 

Any ideas?

---

### Post by byStanderone on 2009-12-20
...have you done a sudo blkid and compared the uuid results from that of your current fstab file?

---

### Post by sofasurfer on 2009-12-20
No I have not. I would like to do that sort of thing but I am lost when it comes to uuids. It just confuses me. I don't understand it. If you could explain it so I could understand it I would be greatful.

But aside from that, isn't that somewhat irrelavant? The Ubuntu drive that I installed operateds on its own. But when it is install along side of the disfunctional Windows drive it fails to operate properly. That is not dependant on the uuids, is it?

---

### Post by PseudoLemon on 2009-12-20
The BIOS is looking for the Windows drive to boot, I think, and since it can't find it it just dies.

---

### Post by byStanderone on 2009-12-21
...yup, and fstab i guess is one place that the system looks at when searching for drives.

---

