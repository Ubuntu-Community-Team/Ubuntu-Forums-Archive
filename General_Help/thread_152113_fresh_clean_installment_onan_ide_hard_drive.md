---
title: "fresh clean installment onan ide hard drive"
date: 2006-03-29
forum: General Help
---

### Post by snooker on 2006-03-29
Hi ... I am going to do a clean installment of 5.10 and I am curious if there is a guide as to how its done ? I heard that I should set up different partition for swap and my home folder ? On this hard drive that I am going to use , Its only going to have Ubuntu OS on it , So could someone show me a guide with steps as to what is the best way to install this OS on its own hard drive ? Thanks :cool:

---

### Post by j_b_seguin on 2006-03-29
I've been doing the same thing and am not getting much information anyware.
I partitioned my drive to Three drives and wound up with files and folders scattered scattered across all the drives. Soooo I created one drive leaving the rest to be partitioned later, everything installed to one drive **GREAT!!** After installing I partitioned the rest of the drive.  and although the drives work just fine, they don't show up in the file browser. Ohhh I'm having so much fun.

I hope your experience goes a lot better

---

### Post by PBK on 2006-03-29
It depends on what you want. I would (and did) go with the defaults. When installing, it will suggest a setup which you can override. For my home installation I have all but the swap on one partition. You might want to create a seperate partition for your /home directory. One reason I would do this is if the information under the /home directory is very important relative to the operating system installation. If the operating system installation gets hosed somehow, it would be easier to reclaim the information under the /home directory if it had its seperate partition. If thier is a hardware problem with the drive this wouldn't help, though. I think swap partitions, generally speaking, should be about 3 times your physical memory amount.

  For me, at home, my ubuntu installation is as important than the information I am creating under my home directory (which I backup to another server anyways) that my /home directory is on the same partition as the root. 

  I think you could get many "recommondations". Diff'rent Strokes kind of a thing, IMO. Another good idea I have heard of is to keep a 10 Gig (or so) partition blank, if you have it available, for future installations. That way you could install a later release and still have a current release available for a backup. I've done this at work.

  Just my opinion. YMMV

Paul

---

### Post by snooker on 2006-03-29
[QUOTE=PBK]It depends on what you want. I would (and did) go with the defaults. When installing, it will suggest a setup which you can override. For my home installation I have all but the swap on one partition. You might want to create a seperate partition for your /home directory. One reason I would do this is if the information under the /home directory is very important relative to the operating system installation. If the operating system installation gets hosed somehow, it would be easier to reclaim the information under the /home directory if it had its seperate partition. If thier is a hardware problem with the drive this wouldn't help, though. I think swap partitions, generally speaking, should be about 3 times your physical memory amount.

  For me, at home, my ubuntu installation is as important than the information I am creating under my home directory (which I backup to another server anyways) that my /home directory is on the same partition as the root. 

  I think you could get many "recommondations". Diff'rent Strokes kind of a thing, IMO. Another good idea I have heard of is to keep a 10 Gig (or so) partition blank, if you have it available, for future installations. That way you could install a later release and still have a current release available for a backup. I've done this at work.

  Just my opinion. YMMV

Paul[/QUOTE]

Hi ... Thats what I want to do , I want to set up my hard drive to have a swap partition . A partition for the /home , Just for upgrading purposes , A partition for Ubuntu and A empty/blank  partition for future upgrade versions,  Is there any graphic type steps that shows how its done ? Or even a text description as to how to set it up ? Thanks

---

### Post by PBK on 2006-03-29
I don't know of anything other than during the installation, but I've just started using ubuntu about a month ago, too. Since 1994 I've used Slackware and that was all character based with fdisk. So, coming from there, I thought ubuntu's was is pretty nice. I do have a Partition How-to doc that kind of explains what you may already know. I'll see if I can attach it here. If that doesn't answer your questions let me know.

Paul

---

### Post by snooker on 2006-03-29
Hi ...  Thanks for that file but , what program can I use to open it with ? Thanks

---

### Post by PBK on 2006-03-29
Try this one. You'll have to rename it Partition.exe after you get it (File size limitation issue). After that, it should self extract to a directory of your choice. It then is just a simple .txt file.

TTUL

---

### Post by snooker on 2006-03-29
Hi ... No that still didn't work , why don't I just use a program that opens zip files for ubuntu , Does anyone know of a program that does just that ? Thanks

---

### Post by PBK on 2006-03-30
OK. Try this...

---

