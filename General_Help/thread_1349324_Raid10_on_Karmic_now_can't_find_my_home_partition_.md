---
title: "Raid10 on Karmic now can't find my /home partition even though it booted this morning"
date: 2009-12-08
forum: General Help
---

### Post by chasetoys on 2009-12-08
guess my computer didn't like the move from one side of the room to another.  literally that's all i did and i didn't drop it. 

after the move i've had issues with overheating (fixed by cleaning out the comp & heatsink), cables detaching (fixed with tape for now; new power supply coming), and now the case of the disappearing raid10 drive.  

 my home partition (/dev/md1) isnt to be found (here is sudo fdisk -l: [http://pastebin.com/f13d1666a](http://pastebin.com/f13d1666a)), and and blkid doesnt list it at all...  this is ironic considering the root partition (/dev/md0) is on the same drive and i'm able to boot from it into a graphical ui that really needs /home/ to be useful.  keep in mind everything booted fine this morning.  when i arrived home things were frozen so i rebooted and then discovered this issue.  

also here is my current fstab: [http://pastebin.com/f602f8e15](http://pastebin.com/f602f8e15)

finanlly to be clear, all drives show up in the bios upon reboot

what should i do now?

many thanks
(Btw i'm "arooni-mobile" on #freenode, if you're an IRC type of person)

---

