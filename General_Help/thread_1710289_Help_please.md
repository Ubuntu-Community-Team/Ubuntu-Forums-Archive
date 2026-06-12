---
title: "Help please"
date: 2011-03-19
forum: General Help
---

### Post by srinibv on 2011-03-19
I installed Ubuntu for net book 10.10 with partition from USB port. after installation, I cannot find my windows files. The system is not showing me options to boot from windows 7 at the start up. 

How can I get my files please. New to Ubuntu so please be patient with me.

---

### Post by TeoBigusGeekus on 2011-03-19
Can't you see the windows' partitions from the places menu?
They should show up as 100gb partition, or 100gb volume or something.

---

### Post by srinibv on 2011-03-19
All I see is 250 GB Harddisk and file System on my computer in the files & folders. I cannot find my files!

---

### Post by TeoBigusGeekus on 2011-03-19
Can you post us the output of the command
```
sudo fdisk -l
```
? (that's L not 1)

---

### Post by srinibv on 2011-03-19
Thank you for the prompt reply:
it gave 
/dev/sda1 linux
/dev/ sda2 extended
/dev/sda5 linuk swap /solaris
/dev sda 6 linux
/dev sda 7 linux swap/solaris

with start end blocks

on top it is showing disl /dev/sdav250.1 gb

---

### Post by Topsiho on 2011-03-19
"
/dev/sda1 linux
/dev/ sda2 extended
/dev/sda5 linuk swap /solaris
/dev sda 6 linux
/dev sda 7 linux swap/solaris
"

This means that Windows has been removed from your disk. And why do you have two swap partitions?

I am very sorry to say this :(

Topsiho

---

### Post by TeoBigusGeekus on 2011-03-19
I think you can have my condolences; you've lost windows.

How did this happen? How did you install ubuntu?
Did you by mistake choose "Use the entire disk" upon installation?

---

### Post by srinibv on 2011-03-19
I installed ubuntu from USB and I remember saying use the partition. I got the second partition because I installed it again to see what i did was correct. So it created the second swap i guess.

Did the windows get wiped out, is there no way i can get my working files into ubumtu?

I will cry if you say no please.

---

### Post by TeoBigusGeekus on 2011-03-19
Stop using the pc right now to prevent further damage to your deleted files.
Next, search the net for recovering tools and software.
Don't expect too much though... Sorry.

---

### Post by srinibv on 2011-03-19
The net book I am working on is on Ubuntu and it has dual boot with windows and ubuntu. All my files are good. Seeing this and the struggle my other friend is going through I tried installing ubuntu for him to make the net book faster and friendly. Then this happened.

Thanks a lot for helping me. I will see if I can get files recovery from the hard disk at least the working files.

May be it is always better that people take back up of thier files before installing. If the installing instructions mention it may be good. I had the thought of taking back up but since I did the set up on my machine I ignored it.

Thanks. Please keep me posted if there is some way to get my files back

---

### Post by TeoBigusGeekus on 2011-03-19
Always backup before making such radical changes to a system and never, ever choose anything else than manual partitioning in the ubuntu installer.

I hope your friend isn't stronger than you...

---

