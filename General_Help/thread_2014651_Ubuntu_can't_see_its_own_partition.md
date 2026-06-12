---
title: "Ubuntu can't see its own partition"
date: 2012-07-02
forum: General Help
---

### Post by Fabones on 2012-07-02
Hello everyone,

I have a notebook with dual boot for windows 7 and Ubuntu.

I had the 11.10 version and then I decided to upgrade for 12.04 from the internet.
And then from the boot options I could'nt select ubuntu anymore, it said the partition did not exist.

So I used a burned DVD with 12.04 to try to reinstall. I did not use the advanced configuration to select partitions. I just choose the "uninstall ubuntu 12.04 and reinstall".
So it did. But it installed Ubuntu at the 100 mb partition reserved by windows...
I reinstall it again but this time I selected the right partition and formatted the 100mb partition. At this point i think I did a huge mistake, I did  not realize that the 100 mb partition was for windows and maybe ubuntu wasn't installed there at all. But well...

The point is, now I have Ubuntu installed at its right partition. But I dont acces the boot menu, it goes right into Ubuntu even if I "sudo grub-install /dev/sda". And thats not the worst. Inside Ubuntu I can see and acces the partition for windows and a partition that I have for common data, but I cant acces its own Ubuntu partition, I dont know what that means...

So... what I need to know is **how to access grub from the boot**. **how to restore the 100mb windows system recovery partition** ( if I really need this to run windows) and [B]how to see and acces Ubuntu's own partition from Ubuntu.

edit: [/B]Well... this is strange... Now I was using kdenlive, a video editiing software, and inside it while navigating folders it sees the Ubuntu partition, but inside the ubuntu's "explorer" it doesn t show. That calms me down to know that the partition is there. But I need to see it normally to manage my files.

**edit2:** Now I realize that the ubuntu partition is acessed trough the "system files " inside the personal folder. I'm sorry for the newbie confusion. But I have a PC with Ubuntu and it shows its partition like any other mounted one, like windows' and the commom files.

---

