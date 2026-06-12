---
title: "&quot;An error occured while mounting /var/cache&quot;"
date: 2012-07-07
forum: General Help
---

### Post by eulu on 2012-07-07
In my ongoing attempts to figure out why I get random lockups, I switched video cards, and now recently swapped out my OS driver (WD Raptor Sata drive) for an SSD. 

Once the lockups started happening (same day) with the SSD installed, I decided to try some 'suggested' changes to my fstab that I found online to (at least hypothetically) improve SSD performance.. (I am not knowledgeable about this stuff, just experimenting)...

So after making the changes, I get this error while the system boots, but I can skip it and then system runs as normal (with the usual random lockups every now and then)..

I still kind of suspect the lockups are due to video card issues (I run a nvidia 7950 and a dual monitor config that I am not willing to give up and have had a lot of fun trying to get/keep it stable)..

Any ideas about this boot up message/error? Here are my fstab lines:
```
proc                                       /proc         proc     nodev,noexec,nosuid  0  0  
#Entry for /dev/sda1 :
UUID=81ffc3ff-fa40-4cb7-8375-b379517fc848  /             ext4     discard,noatime,nodiratime,errors=remount-ro    0  1  
#Entry for /dev/sdb1 :
UUID=08D23A42D23A33F2                      /media/Data1  ntfs-3g  defaults,uid=1000    0  0  
#Entry for /dev/sdc1 :
UUID=EA3491A6349175F3                      /media/Data2  ntfs-3g  defaults,uid=1000    0  0  
#Entry for /dev/sda5 :
UUID=c034762a-840c-446d-80e7-104b847b8eb0  none          swap     sw                   0  0  
# Uncomment these after all server based applications installed - eg. apache
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
tmpfs /var/log/apt tmpfs defaults,noatime 0 0
none /var/cache unionfs dirs=/tmp:/var/cache=ro 0 0
```

---

### Post by Paddy Landau on 2012-07-08
I don't know about your lock-up issues, but your /var/cache looks a bit strange. May I ask why you are using unionfs for it?

I notice that the last five lines of your fstab are supposed to be commented out, and I'd agree with that. I don't see any reason to have them, apart from /tmp if you intend to hold it in RAM. It could be that your RAM is filling up, causing the lock-ups.

Comment out those last five lines, reboot and see what happens.

---

### Post by eulu on 2012-07-08
> **Paddy Landau said:**
> I don't know about your lock-up issues, but your /var/cache looks a bit strange. May I ask why you are using unionfs for it?

I notice that the last five lines of your fstab are supposed to be commented out, and I'd agree with that. I don't see any reason to have them, apart from /tmp if you intend to hold it in RAM. It could be that your RAM is filling up, causing the lock-ups.

Comment out those last five lines, reboot and see what happens.

I was having lock ups before I added those lines. I have been having lock ups since I installed ubuntu 12.04 back in March (but never before that when I had Windows 7 in the same hardware config)... 

Since I first installed ubuntu, I've switched video cards and hard drives trying to see if I can bring more stability. When the SSD drive didn't prove to help (it locks up a little more often than my WD raptor drive does), I started looking at suggestions for configuring the SSD with Ubuntu, which led me to adding those lines, which are supposed to move the logs into ram and decrease writes to the drive. I've noticed no difference in performance but this is supposed increase life span of SSD drives... 

As I understand, I would only want to comment out those lines if I didn't want to have those logs in ram anymore.

The 'unionfs' line is also part of this moving of the logs to ram, as it was suggested to me [here]("http://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds")...

---

### Post by Paddy Landau on 2012-07-09
I understand what you are getting at. Indeed, the SSD will last longer when you are using RAM for your temporary files.

However&#8230;

You have to have sufficient RAM. You have not said how much RAM you have, but have a look at the space currently used on my machine by [FONT=Lucida Console]/var/cache[/FONT]: 1.3Gb. That would be a hefty chunk of RAM.

If you have at least 4Gb RAM, that probably would be OK.

However, also think about [FONT=Lucida Console]/tmp[/FONT]. If you are (say) manipulating with audio, video or photographs, your [FONT=Lucida Console]/tmp[/FONT] may well grow to a significant size.

The result would be that your memory would be moving in and out of swap. Where is your swap: on your SSD?

It is possible &#8212; not certain, but possible &#8212; that this is what causes your lock-ups.

How much RAM do you have; how large is your swap partition; and where is your swap located?

**EDIT**: I have decided to experiment with unionfs, and on my  system, at least, it is not installed. Nor can I find any way to install it (I have installed unionfs-fuse, which is a command-line utility as opposed to a file system that mount can use directly). Have you installed anything to  get unionfs to work?

---

### Post by eulu on 2012-07-10
> **Paddy Landau said:**
> I understand what you are getting at. Indeed, the SSD will last longer when you are using RAM for your temporary files.

However…

You have to have sufficient RAM. You have not said how much RAM you have, but have a look at the space currently used on my machine by [FONT=Lucida Console]/var/cache[/FONT]: 1.3Gb. That would be a hefty chunk of RAM.

If you have at least 4Gb RAM, that probably would be OK.

However, also think about [FONT=Lucida Console]/tmp[/FONT]. If you are (say) manipulating with audio, video or photographs, your [FONT=Lucida Console]/tmp[/FONT] may well grow to a significant size.

The result would be that your memory would be moving in and out of swap. Where is your swap: on your SSD?

It is possible — not certain, but possible — that this is what causes your lock-ups.

How much RAM do you have; how large is your swap partition; and where is your swap located?

**EDIT**: I have decided to experiment with unionfs, and on my  system, at least, it is not installed. Nor can I find any way to install it (I have installed unionfs-fuse, which is a command-line utility as opposed to a file system that mount can use directly). Have you installed anything to  get unionfs to work?

Thanks for the input Paddy!
- I have 4GB ram.
- The swap is still on SSD and it is 4.3GB. I thought about moving/disabling but as of yet have not done anything with it.
- I don't know how to determine where my swap is located (other than on the SSD somewhere) and don't have time at the moment to figure out how to find out where on the drive it is.. 
- I admit that it's possible that any of this is causing lock ups, but as I've said, I've been getting lock ups all along, before SSD, and before I made any changes to the config for SSD. The lock ups are more frequent right now than before SSD. (I am about to move this SSD and ubuntu load into a laptop tonight and take it on a vacation so we'll see how it performs there...)
- I have not installed anything to get unionfs to work, which must be at least part of the problem with the mount error I get. I didn't know that anything was necessary as the instructions I found didn't mention it. I assumed it was a command tool that was included with ubuntu....

---

### Post by Paddy Landau on 2012-07-10
> **eulu said:**
> The swap is still on SSD and it is 4.3GB.
I thought as much; your [FONT=Lucida Console]fstab[/FONT] implies that is is on [FONT=Lucida Console]/dev/sda5[/FONT]. The size is perfectly fine. I wouldn't bother moving it unless you have a hard drive in the machine.

> **eulu said:**
> … as I've said, I've been getting lock ups all along, before SSD, and before I made any changes to the config for SSD.
Ah, sorry, I seem to have missed that. My apologies.

Make one change to your fstab. Delete the line for [FONT=Lucida Console]/var/cache[/FONT]. (Firstly, the existing [FONT=Lucida Console]unionfs[/FONT] is pointless as it merges [FONT=Lucida Console]/var/cache[/FONT] with [FONT=Lucida Console]/tmp[/FONT], which is in RAM. Secondly, [FONT=Lucida Console]unionfs[/FONT] appears to be non-functional in 12.04, which would mean that the line is probably ignored anyway.)

> **eulu said:**
> The lock ups are more frequent right now than before SSD. (I am about to move this SSD and ubuntu load into a laptop tonight and take it on a vacation so we'll see how it performs there...)
Try commenting out all of your new [FONT=Lucida Console]fstab[/FONT] lines (the ones beginning with [FONT=Lucida Console]tmpfs[/FONT]) and see what happens. However, reading your comments, I wonder if either there is a hardware fault, or a driver is missing or unavailable for some part of your hardware?

Open Additional Drivers and see whether or not anything is listed there (you need to be connected to the Internet  when you do this).

> **eulu said:**
> I have not installed anything to get unionfs to work, which must be at least part of the problem with the mount error I get. I didn't know that anything was necessary as the instructions I found didn't mention it. I assumed it was a command tool that was included with ubuntu....Yes, it looks like it, doesn't it? An easy mistake to make! There is a command, [[FONT=Lucida Console]unionfs-fuse[/FONT]]("apt:unionfs-fuse"), but it does not work with the [FONT=Lucida Console]mount[/FONT] command. You have to run it separately.

---

### Post by eulu on 2012-07-10
> **Paddy Landau said:**
> I thought as much; your [FONT=Lucida Console]fstab[/FONT] implies that is is on [FONT=Lucida Console]/dev/sda5[/FONT]. The size is perfectly fine. I wouldn't bother moving it unless you have a hard drive in the machine.

I do have two other hard drives mounted (both ntfs as you can see in my fstab).

> **Paddy Landau said:**
> Make one change to your fstab. Delete the line for [FONT=Lucida Console]/var/cache[/FONT]. 

Will do. 

> **Paddy Landau said:**
> Try commenting out all of your new [FONT=Lucida Console]fstab[/FONT] lines (the ones beginning with [FONT=Lucida Console]tmpfs[/FONT]) and see what happens. However, reading your comments, I wonder if either there is a hardware fault, or a driver is missing or unavailable for some part of your hardware?

I will and I was already planning to do this as I am going to use this SSD /ubuntu load in a laptop on my two week vacation that starts tomorrow (family trip to Northern Cal/Oregon). I'll report back either after or during the trip (if I'm bored lol) on whether or not I get lock ups on the laptop...

> **Paddy Landau said:**
> Open Additional Drivers and see whether or not anything is listed there (you need to be connected to the Internet  when you do this).

Nothing in there.

---

### Post by Paddy Landau on 2012-07-11
> **eulu said:**
> I do have two other hard drives mounted (both ntfs as you can see in my fstab).
Indeed, you are right. They are /dev/sdb and /dev/sdc.

If you like, you can choose one of them, shrink its partition by (say) 4.3Gb, and add a swap there, deleting your swap off the SSD. If you don't know how to do that, we can talk you through it. However, I'd first wait until your current problem is solved.

---

### Post by JohnAreBee on 2013-03-23
I know this thread is old but I am replying just to update in-case people stumble upon this.
I use the same modifications in the lower part of my fstab except for your last line:
```
none /var/cache unionfs dirs=/tmp:/var/cache=ro 0 0
``` 
I added it to my fstab to check and my system also did not mount it. So i would just get rid of that part.

The purpose for the code under:```
# Uncomment these after all server based applications installed - eg. apache
```
is to enhance your system if it run on a SSD, that means if your / is on a SSD partition, it mounts those dirs into ram instead of file system. The reason for that is because the tmp and log dirs are constantly being accessed with allot of very small read/writes and for a SSD that will decrease the life of your drive. That being said the last line of that config i would not recommend because i like to have "/var/cach/apt" on disk and that current dir in my system is almost 1GB, and there is no need to have that much memory being wasted in your ram.
The reason it says to Uncomment these after all server based applications installed - eg. apache, is because it will leave logs on your disc until you uncomment the code below, so if anything happens you can refer to the logs even after a reboot.

So if you need log files to survive after reboot all you have to do is comment them out again and it will be loaded back on disc after reboot and will look like this:
```
#Ram Disk Edits#
# Uncomment these after all server based applications installed - eg. apache
#tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
#tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
#tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
#tmpfs /var/log/apt tmpfs defaults,noatime 0 0
```

If you don't (This is what mine looks like):
```
#SSD Tweaks#
# Uncomment these after all server based applications installed - eg. apache
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
tmpfs /var/log/apt tmpfs defaults,noatime 0 0
```

Many guides say to add this to your fstab:
```
[COLOR=#000000][FONT=Ubuntu Mono]tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0[/FONT][/COLOR]
```
This is up to you, but this tmp dir is the one that is supposed to survive reboots. So up too you.

And if you run into trouble with system stability you may want to comment out:
```
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
```
So the logs survive reboot/power loss, so you can go through them to find the issue.

---

