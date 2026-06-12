---
title: "How safe is moving a boot partition?"
date: 2011-03-02
forum: General Help
---

### Post by tedrogers on 2011-03-02
Hi all,

Using gparted as shown on the partitions in the image:

[IMG]http://i77.photobucket.com/albums/j58/fiddybux/Screenshot-3.png[/IMG]

sda1 is Windows 7
sda2 is swap
sda3 is root
sda4 is home

I'd like to move sda4 to the end of the drive, thus shrinking it by 20GB, and shunt every other partition along to make an extra 20GB for sda1 at the start of the drive, and expand this partition into the 20GB of space I created.

When I start moving and shrinking sda4 (before I apply and execute the command) I get a warning saying that it is very dangerous to move a boot partition and it could render my system unbootable etc etc.

How safe is it to do this? If I bork it, can I recover easily? 

I assume the error has something to do with start/end disk sectors in the grub2 list (however this works these days). In short, messages like this do what they should and scare me just enough to seek assistance from this wonderful online community! ;)

Thanks in advance peeps.

---

### Post by Spyderkid on 2011-03-02
I imagine its going to be extremely complicated because you've got to redirect for things to look for stuff in different places i think

---

### Post by bprins on 2011-03-02
Dunno how dangerous it is, I've done the same thing on my laptop without any probs, but that's no guarantee that it'll work for you as well.

But, would it be an alternative to make your /home partition smaller, and use the free space for a NTFS data partition so that you can offload your windows partition?

---

### Post by tedrogers on 2011-03-02
> **bprins said:**
> Dunno how dangerous it is, I've done the same thing on my laptop without any probs, but that's no guarantee that it'll work for you as well.

But, would it be an alternative to make your /home partition smaller, and use the free space for a NTFS data partition so that you can offload your windows partition?

I guess I could do what you suggest...but you just made me think of something.

Why would gparted say that sda4 is a boot partition? It is my /home where I keep all my crud. Nothing of any 'system wide' importance is on that drive.

Furthermore, if I do what you suggest and shrink sda3 instead, this really is the boot partition...but at least I'll be taking it from the back-end of the partition (so to speak) and won't be moving the (seemingly vital) start point of the partition.

Or is it just a standard unintelligent message that gparted has issued?

Ponder on brave soldiers!

:)

---

### Post by bprins on 2011-03-02
Not sure if I follow you, but shrinking sda4 (/home) seems the appropriate action to me. With the saved space together with the unused space create a new NTFS partition and use that partition to offload data from your win7 partition.

About the warning. If the warning is only about the actions you planned to do on sda4, then I agree with you, it's a bogus warning since your sda4 partition is indeed not a boot partition. Maybe you also queued something for sda3 partitions?

---

### Post by tedrogers on 2011-03-03
> **bprins said:**
> Not sure if I follow you, but shrinking sda4 (/home) seems the appropriate action to me. With the saved space together with the unused space create a new NTFS partition and use that partition to offload data from your win7 partition.

About the warning. If the warning is only about the actions you planned to do on sda4, then I agree with you, it's a bogus warning since your sda4 partition is indeed not a boot partition. Maybe you also queued something for sda3 partitions?

Yes you understand me correctly I think, and I would agree that the warning concerning sda4 would appear to be unwarranted/bogus.

I may try imaging every drive, making a record of the physical disk structures and formats, so that I can go back if needed, then I'll just try the shrinking and moving thing and see what happens!

---

### Post by tedrogers on 2011-03-03
> **bprins said:**
> Dunno how dangerous it is, I've done the same thing on my laptop without any probs, but that's no guarantee that it'll work for you as well.

But, would it be an alternative to make your /home partition smaller, and use the free space for a NTFS data partition so that you can offload your windows partition?

Were there absolutely no issues, and did it take an age?!?

---

