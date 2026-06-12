---
title: "Copying my Partition to External then Copying it back later?"
date: 2009-08-15
forum: General Help
---

### Post by razorboy5 on 2009-08-15
Hi

I'm taking my Laptop into shop next week and i'm afraid they will turn it back to factory defaults (which unfortunately is back to Vista)

main thing i'm trying to do is copy this partition onto my External hard drive and copy it back after i get my laptop back. is there a way to do this process? I have alot of customization on my ubuntu and i dont want to do a fresh install again

thx

---

### Post by SoftwareExplorer on 2009-08-15
Is [COLOR=Green][this]("http://ubuntuforums.org/showthread.php?t=581680")[/COLOR] the type of thing you are looking for? It could be used to make a perfect image of your hard drive, compress it, and put it as a file on another drive. Then when you got it back you could overwrite Vista with your backed up data. 

Let me know what you think, and I'll try to help you customize the commands. It would be close to the Example B in the step 3 section.

PS:I 'stole' a part of your signature and modified it in true open source fashion.

---

### Post by razorboy5 on 2009-08-15
yes that looks like something i'm trying to do
seems very complicated

also i did some research and gparted has a "copy" option
my ubuntu partition is dev/sda1 if i just copy this partition and format my external to ext3 then copy it there would i be able to copy it back onto the hard drive?

---

### Post by Vunutus on 2009-08-15
Somebody already mentioned how to clone your data, but I'd just like to ask you why you think your data is at risk?

For starters, there isn't really a "factory defaults" button you can hit on laptops like with routers and such. They would have to consciously choose to erase your data, which is a blatant breach of trust and probably illegal.

---

### Post by razorboy5 on 2009-08-15
maybe i'm being paranoid 

but would seem logical for them to get it back to vista since they're more comfortable fixing machines under it rather than using a foreign OS

didn't know it was considered breach of trust or maybe even illegal

never dealt with a big company tech help before, always went to the smaller local computer places. Got warrenty so i figure i might as well use it rite now

---

### Post by Vunutus on 2009-08-15
Yeah I'm pretty sure erasing customer's data is a big no-no. 

From what you've said I'm thinking there's a large probability that they are doing a hardware fix, in which case they shouldn't even need to power on the machine.

Being paranoid isn't always a bad thing, though.

---

### Post by razorboy5 on 2009-08-15
well it's not important data or anything i just dont wanna reinstall OSS4, Swiftweasel, Flash player, Banshee, Conky, and everything else .... again

and i'm not sure if it's a hard fix, my system's overheating and alot of other people from this forums suggested that it's probably a dust problem that machine's not getting enough air.

---

### Post by SoftwareExplorer on 2009-08-15
> **razorboy5 said:**
> maybe i'm being paranoid 

but would seem logical for them to get it back to vista since they're more comfortable fixing machines under it rather than using a foreign OS

didn't know it was considered breach of trust or maybe even illegal

never dealt with a big company tech help before, always went to the smaller local computer places. Got warrenty so i figure i might as well use it rite now
No, your completely right to be 'paranoid'. It was recommended by HP to back up my data before I sent my laptop in for repair. Sure enough, if they've warned you (it could be fine print if they wanted to be mean) it could happen. In the end, they did re-image my hard drive to the factory default of vista with all its crapware trials and 'helpful additions' to boot when they were repairing it. Oh, and did I mention, they were just replacing a wireless card, not trying to fix a hard drive or O/S issue.

---

### Post by razorboy5 on 2009-08-15
alright thx i'll probably check the fine print... may take a few hours lol...

and took another look at the link again SoftwareExplorer and realized that u dont need to put in all the codes and just 3-4 out of all those codes should do it lol...

the previous post i was overwhelmed seeing like 30 lines of code

seems worth a try :P

and if i'm making a image of my OS would it save all my music and videos? or just the installed programs?

thx

also i'm honoured u 'stole' my siggy :D go open source!

---

### Post by SoftwareExplorer on 2009-08-15
If you use the commands with sda1 for example, you will get a perfect image of sda1. Anything on sda1 would be saved--ubuntu, installed programs, files, music--whatever is stored on the partition would be saved. Now if you used sda (notice-without a number), it would make such a image of the entire disk. Then it would include everything on that disk--all the partitions and everything in them. Now if you just have one disk on the computer you can be sure you got everything when you use the commands without a number.

---

### Post by SoftwareExplorer on 2009-08-15
> **razorboy5 said:**
> yes that looks like something i'm trying to do
seems very complicated

also i did some research and gparted has a "copy" option
my ubuntu partition is dev/sda1 if i just copy this partition and format my external to ext3 then copy it there would i be able to copy it back onto the hard drive?
Sorry, I didn't see that post. Then I read my email and I was like where did he say that?  Anyways: It would take about 3 commands to back up a partition. The page I linked to would give you the benefits of taking less space (it's compressed) and that the backup is held in a file which is easier to move around in comparison to a partition. You would give your external drive a file-system if it doesn't have one (ext3 is fine) and then save it as a file on it. So, does your external drive have a partition and filesystem on it yet?
Second, you could also use partimage. It's in the repositories and has a graphical interface that you navigate with a keyboard and does what we are trying to accomplish if you aren't using NTFS or EXT4.

---

### Post by razorboy5 on 2009-08-15
yup got a NTFS filesystem on it but can easily format to ext3 if needed

also i only have one partition so it would be easier

thx for all the help :P

---

### Post by SoftwareExplorer on 2009-08-15
NTFS on the external drive is great. I was just saying that partimage can't backup NTFS or EXT4(yet). However, it can save the backup file to ntfs or ext4 just fine. The commands on the page I linked to can backup NTFS and ext4. So take your pick of partimage or commands and we'll get started. [COLOR=Blue]If you are going to use partimage then you will have to boot into the liveCD. Then install the partimage package. Mount your external disk if it isn't already and find out where it is mounted if you don't know. Then you can run [/COLOR]```
sudo partimage
```[COLOR=Blue] in a terminal to get into the program.[/COLOR]
[COLOR=Green]If you are doing the commands method, then you can do this one while you are still booted into the hard disk installed ubuntu. ```
sudo dd if=/dev/zero of=/tmp/zerofill.tmp&&sudo rm /tmp/zerofill.tmp
``` This will fill the free space on your partition with zeros that will compress down to about zero size when we backup. Then it will try to delete the file full of zeros. If it doesn't delete it, then you can run [/COLOR]```
gksudo nautilus 
```[COLOR=Green]and go /tmp and delete the file  yourself. Once you're done with that then you can boot into the liveCD and mount your external drive.[/COLOR] 

I used colors to differentiate what steps belong to which procedure

---

