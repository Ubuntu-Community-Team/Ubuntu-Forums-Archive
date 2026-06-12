---
title: "HDD changing name not working"
date: 2011-01-27
forum: General Help
---

### Post by ephexeve on 2011-01-27
I have 5 HDD on my computer. 

[http://img203.imageshack.us/img203/66/screenshotpzt.png](http://img203.imageshack.us/img203/66/screenshotpzt.png)

As you can see at the photo, all names are like : 640 GB Hard Disk: Bratu and so on.
I want to remove this and just leave it Bratu, Data and so on. 
If I try to change the name at the proprieties but then Ubuntu says I can't do that, I get this error: 

> Sorry, could not rename "640 GB Hard Disk: Bratu" to "Bratu": Operation not supported by backendAny Ideas how?

Cheers

---

### Post by coffeecat on 2011-01-27
You need to change or add partition labels. It is the partitions you need to label, not the drives themselves, even if there is only one partition on a particular drive.

Open Disk Utility (System > Administration). Highlight the partition you want to relabel and click on 'Edit Filesystem Label'.

---

### Post by ephexeve on 2011-01-27
Did not work. I tried umounting my files, but It wont unmount, I get an error.
Any other ideas ?

[http://img191.imageshack.us/img191/3117/screenshot1rn.png](http://img191.imageshack.us/img191/3117/screenshot1rn.png)

---

### Post by coffeecat on 2011-01-27
That's very curious. Have a look at my screenshot for what you should be seeing. (By the way, please use the forum's manage attachments utility for images and not a 3rd party image hosting site.) In my screenshot you'll see 'Edit Filesystem Label' between 'Format Volume' and 'Delete Partition'. I can only think of two reasons why the label option should not appear in your Disk Utility, namely:

1 - If you do not have the application ntfsprogs installed you cannot label NTFS partitions.

2 - Possibly (just a theory) if the partition is not already labelled you cannot re-label it in Disk Utility. If so, this would be a major flaw in the Disk Utility design so I'm not inclined to believe this is possible - just yet.

So - check you package manager (either Synaptic or Software Centre) and check that ntfsprogs is installed. It should be, for the last year or so it's been part of a default install, but if it isn't install it and try Disk Utility again.

If Disk Utility still isn't co-operating, try installing Gparted. You can set partition labels with that.

Lastly, so long as you have ntfsprogs installed there is a terminal command you can use to set a NTFS partition label. I can give you that but see if any of the above works first.

---

### Post by ephexeve on 2011-01-28
Cheers for your answer. But none of them worked, I still got the same problem. Cant unmount so I can't label. 

Give me the other options them, thank you .

---

### Post by coffeecat on 2011-01-28
> **ephexeve said:**
> Cant unmount so I can't label. 

How do you mean, you can't unmount? You mean that Disk Utility won't unmount it for you? Is your 640GB hard disk mounted by /etc/fstab? If so, you need to unmount it as root from a terminal:

```
sudo umount /media/Bratu
```

---

### Post by Morbius1 on 2011-01-28
@coffeecat, I don't know about you but this is getting curiouser and curiouser. Do you think it's time we get back to basics, forget about all these GUI's and see if we can find out how the system really sees these partitions. I'm thinking providing the output of:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```It's possible that fstab is completely discombobulated.

Just an idea.

---

### Post by coffeecat on 2011-01-28
> **Morbius1 said:**
> @coffeecat, I don't know about you but this is getting curiouser and curiouser. Do you think it's time we get back to basics, forget about all these GUI's and see if we can find out how the system really sees these partitions. I'm thinking providing the output of:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```It's possible that fstab is completely discombobulated.

Just an idea.

That's a good idea. Thanks for the thought.

I'm still puzzled about the appearance or non-appearance of the label button in Disk Utility. I've been doing some further experiments and sometimes the button is there with a mounted partition and sometimes not. You can't run ntfslabel from a terminal on a mounted partition but that doesn't explain the Disk Utility discrepancy - I think. :?

All very odd.

---

### Post by ephexeve on 2011-01-28
Something even worse happened. 
> How do you mean, you can't unmount? You mean that Disk Utility won't  unmount it for you? Is your 640GB hard disk mounted by /etc/fstab? If  so, you need to unmount it as root from a terminal:

 	Code:
 	sudo umount /media/Bratu 


I tried that using my Bratu_II, not Bratu. It did unmount. 
So then I went back to Disk Utility, and this is what I got.

[http://img689.imageshack.us/img689/5437/screenshotzd.png](http://img689.imageshack.us/img689/5437/screenshotzd.png) 

The same thing as before.
So i tried to mount again, and look what I got 

[http://img560.imageshack.us/img560/695/screenshot1rt.png](http://img560.imageshack.us/img560/695/screenshot1rt.png)

I tried doing what [Morbius1]("http://ubuntuforums.org/member.php?u=982144") said. This is what I got. 

[http://img204.imageshack.us/img204/6785/screenshot2jh.png](http://img204.imageshack.us/img204/6785/screenshot2jh.png)

Yes, it is written in fstab. Look

[http://www.mediafire.com/?4bqq8f4dbgd4mx2](http://www.mediafire.com/?4bqq8f4dbgd4mx2)

So I can't mount my Bratu_II anymore =(

Any ideas now ? 

Thanks again guys

---

### Post by coffeecat on 2011-01-28
> **ephexeve said:**
> So then I went back to Disk Utility, and this is what I got.

[http://img689.imageshack.us/img689/5437/screenshotzd.png](http://img689.imageshack.us/img689/5437/screenshotzd.png) 

The same thing as before.

What do you mean, "the same thing as before"? Do you mean you tried to label the partition and you got an error message? If so, please post the error message.

For the rest:

> **ephexeve said:**
> I tried doing what [Morbius1]("http://ubuntuforums.org/member.php?u=982144") said. This is what I got. 

[http://img204.imageshack.us/img204/6785/screenshot2jh.png](http://img204.imageshack.us/img204/6785/screenshot2jh.png)

Yes, it is written in fstab. Look

[http://www.mediafire.com/?4bqq8f4dbgd4mx2](http://www.mediafire.com/?4bqq8f4dbgd4mx2)



No I'm not going to download anything from mediafire and trying to read your terminal output in an imageshack image is giving me a headache. Please use forum facilities whenever you can. If you wish to post an image, use the forum "manage attachments" button below the message field - or you can click on the paperclip icon for the same - to upload an image to the forum. For terminal output please enclose it in [noparse]```

```[/noparse] tags - you can use the # icon in the message toolbar for this. By using code tags...

> [noparse]```
Your terminal output
```[/noparse]...comes out looking like this:

```
Your terminal output
```So - post the output of...

```
sudo blkid
```and

```
/etc/fstab
```... as Morbius1 suggested, but IN CODE TAGS, and we can see what's going on.

---

### Post by Morbius1 on 2011-01-28
Luckily I have to run but I have two suggestions:

(1) Stop using Disk Utility

(2) If you want to post the output of a command from a Terminal:

Run the command then in the Terminal:
Edit > Select All  > Edit > Copy

Then do a paste to your next post preferably around quote tags. All of this imageshack stuff is giving me a headache. 
[COLOR=Blue]
EDIT[/COLOR]: Sorry coffeecat - like minds it seems

---

### Post by coffeecat on 2011-01-28
> **Morbius1 said:**
> Luckily I have to run but I have two suggestions:

(1) Stop using Disk Utility

I absolutely agree with this.

@ephexeve, I've had some more thoughts. Labelling partitions should be one of the easiest jobs to do and I think it must be Disk Utility which is the problem here. Perhaps there's a bug. Whatever, try this.

Install Gparted as I suggested before. After installation you can find it in System > Administration. Open it and highlight the partition you want to relabel. If it's already mounted, unmount it by right-clicking on it and choosing 'Unmount'. Then, from the Partition menu, choose 'Label' and edit the label. After OK'ing that you have to apply the change by clicking on the Apply button - the big green tick in the toolbar. If that doesn't work then something is seriously wrong.

---

### Post by ephexeve on 2011-01-28
@[coffeecat]("http://ubuntuforums.org/member.php?u=129087"),
Sorry for the imageshack, I ain't used to post here a lot. Now I get it. You are right, labeling a HDD is very easy, but like I said, isn't working at the moment. 

> What do you mean, "the same thing as before"? Do you mean you tried to  label the partition and you got an error message? If so, please post the  error message.
I meant about my third post I posted, I said I had an error, when unmounting a HDD, that was my error. I will be posting the error I got when mounting or unmounting a HDD, they are all the same for other HDD too. 

Here is the result of the first thing you asked me.

```

root@Ephexeve:/home/ephexeve# blkid 
/dev/sda1: LABEL="Data" UUID="01CBBA1D22BFBC80" TYPE="ntfs" 
/dev/sdb1: LABEL="Data II" UUID="0827AC91779178C1" TYPE="ntfs" 
/dev/sdc2: UUID="39f1f9e9-6870-4f87-957c-703ab83733b8" TYPE="ext4" 
/dev/sdc3: UUID="3e624be2-fb4b-4eed-b084-91244d0d520a" TYPE="swap" 
/dev/sdd1: LABEL="Bratu" UUID="08E4C799E4C78780" TYPE="ntfs" 
/dev/sde1: LABEL="Bratu II" UUID="7D9600E146DD491A" TYPE="ntfs" 
/dev/sdf1: LABEL="Bratu Ext" UUID="01CBAF8A1736B500" TYPE="ntfs" 

```and the second thing.

```

UUID=3e624be2-fb4b-4eed-b084-91244d0d520a swap swap sw 0 0
UUID=39f1f9e9-6870-4f87-957c-703ab83733b8 / ext4 defaults 0 1
UUID=08E4C799E4C78780 /media/Bratu ntfs-3g defaults 0 0
UUID=7D9600E146DD491A /media/Bratu_II ntfs-3g defaults 0 0
UUID=0827AC91779178C1 /media/Data_II ntfs-3g defaults 0 0
UUID=01CBBA1D22BFBC80 /media/Data ntfs-3g defaults 0 0
```@[Morbius1]("http://ubuntuforums.org/member.php?u=982144"), 
I tried Gparted already, and when I click on Label Drive, I write Bratu  and save it, then I mount it again and go to My computer and it still  says: 640 GB Hard Disk: Bratu. I will upload the screenshot of my computer, so you can see how it looks like.

---

### Post by coffeecat on 2011-01-28
> **ephexeve said:**
> then I mount it again and go to My computer and it still  says: 640 GB Hard Disk: Bratu. I will upload the screenshot of my computer, so you can see how it looks like.

No, don't worry. The screenshot in your first post shows it nicely.

My apologies. I must admit I misread and therefore misunderstood your first post. If you look in the left pane of that screenshot, you'll see that the partitions are listed by label. If they do not have a partition label, then they are listed by filesystem size. Ditto in the Places menu. But in the main pane of the Nautilus 'Computer' window you will always get the disc size preceding the partition label. That is by design and is meant to be helpful and I do not know how (or if) you can change this.

Sorry about the mixup but at least we've both learnt that Disk utility is not be relied upon for labelling partitions, and you've learnt something about the forum facilities. :)

The disk size in Computer has never concerned me, but I don't like the way it puts the total disc size rather than the partition size against the partition label. But, again, I don't think you can change that.

---

### Post by ephexeve on 2011-01-29
Hmm, alright then, thanks for your help

---

