---
title: "Partition Manager: Unable to resize linux partition to use free space BEFORE partitio"
date: 2011-05-29
forum: General Help
---

### Post by iclestu on 2011-05-29
Hey guys.

I have around 30gb of free space in my partition table immediately before the Linux partition. I want to resize my linux partition to take up this space.

I tried booting with live cd, sucessfully umounted the hard drive but found I could not resize the partition. On clicking the 'edit size' button, partition manager recognised the free space before the partition but when i reduced this, the 'ok' button was greyed out. (it was not greyed out for the windows partition so I could, in theory, increase the windows partition to take up the free space but this is not what i wanted to do).

I am pretty sure that I had managed to unmount the drive correctly as the padlock symbol had dissapeared (I took the attached screenshot, which does show the lock symbol, after rebooting into my normal system).

Anyone got any ideas as to why it wont allow this? There is no reason why i can resize the partition to take up the free space BEFORE it is there?

Would be grateful for any advice or suggestions....

---

### Post by Irihapeti on 2011-05-29
Resizing a partition always carries a certain amount of risk, but usually changing the right-hand end is fairly safe.

Not so with the other end. I understand that trying to move the beginning of a partition is very risky. I know that I managed to mess up one partition that way (fortunately with nothing important on it). It's a while since I did that and I don't remember exactly how I did it.

Probably a safer way is to backup whatever is on the partition - a good security move anyway - and then delete it and create a new one. Then you can restore the data.

Of course, if your Linux partition is inside an extended partition, and Windows isn't, then you'd have to change the extended partition as well. That could get complicated if you have more than just the Linux partition and a swap.

---

### Post by wildmanne39 on 2011-05-29
> **iclestu said:**
> Hey guys.

I have around 30gb of free space in my partition table immediately before the Linux partition. I want to resize my linux partition to take up this space.

I tried booting with live cd, sucessfully umounted the hard drive but found I could not resize the partition. On clicking the 'edit size' button, partition manager recognised the free space before the partition but when i reduced this, the 'ok' button was greyed out. (it was not greyed out for the windows partition so I could, in theory, increase the windows partition to take up the free space but this is not what i wanted to do).

I am pretty sure that I had managed to unmount the drive correctly as the padlock symbol had dissapeared (I took the attached screenshot, which does show the lock symbol, after rebooting into my normal system).

Anyone got any ideas as to why it wont allow this? There is no reason why i can resize the partition to take up the free space BEFORE it is there?

Would be grateful for any advice or suggestions....
HI, I found this great thread that will help. If the free space is in the wrong place you have to move your partition before you can resize it, but this leads to reinstalling the grub. [http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by iclestu on 2011-05-29
thanks guys.

Still not entirely sure why it wont resize but maybe im persueded not to b other for time being.. :)

---

### Post by ankspo71 on 2011-05-29
> **Irihapeti said:**
> 
Of course, if your Linux partition is inside an extended partition, and Windows isn't, then you'd have to change the extended partition as well. That could get complicated if you have more than just the Linux partition and a swap.

This is probably what it could be. The extended partition is the partition that was automatically created to contain the logical partitions.

If their was a 30gb logical partition that got removed previously, then I am sure that there is still an extended partition containing 30gb space that needs to be resized first, before you can resize the partition you want to resize. 

If the partition you want to resize IS a logical partition, then you might need to resize its own extended partition first, otherwise the logical partition you want to resize might already be at its own maximum size due to the size of it's own extended partition.

Whatever you need to do, make sure you do all of your necessary backups first.

If you look at this screenshot, you can see a light blue colored box surrounding the logical partitions. That would be the extended partition.
[http://gparted.sourceforge.net/larry/resize/big/resize-4.1-b.gif](http://gparted.sourceforge.net/larry/resize/big/resize-4.1-b.gif)

Here is more info on how to resize partitions using gparted:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
(section 3 talks about resizing an extended partition)

---

### Post by iclestu on 2011-05-29
> **ankspo71 said:**
> This is probably what it could be. The extended partition is the partition that was automatically created to contain the logical partitions.

If their was a 30gb logical partition that got removed previously, then I am sure that there is still an extended partition containing 30gb space that needs to be resized first, before you can resize the partition you want to resize. 

If the partition you want to resize IS a logical partition, then you might need to resize its own extended partition first, otherwise the logical partition you want to resize might already be at its own maximum size due to the size of it's own extended partition.

Whatever you need to do, make sure you do all of your necessary backups first.

If you look at this screenshot, you can see a light blue colored box surrounding the logical partitions. That would be the extended partition.
[http://gparted.sourceforge.net/larry/resize/big/resize-4.1-b.gif](http://gparted.sourceforge.net/larry/resize/big/resize-4.1-b.gif)

Here is more info on how to resize partitions using gparted:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
(section 3 talks about resizing an extended partition)

Thanks for your help on this.

I'm pretty sure that the extended partition was full and that the empty space is outside it. I was expecting to be able to change the size of the extended partition using partition manager.... Im away from my desktop pc just now but will be sure to check when I return home.

Thanks again

---

### Post by iclestu on 2011-05-31
yeah - as i remembered.

The extended partition is full but I had hoped to be able to increase the size of the extended partition to take up the free space. I can then increase the logical partition accordingly?

Screen shot of partition manager is attached. 1st pic shows main view. 2nd and 3rd shows greying out of 'ok' button when trying to resize the extended partition. It looks like it SHOULD be an option and i dont know why it wont allow it?

Interestingly (well, maybe ;) ) it would appear to allow me to extend the windows partition (sda2), tho as i mentioned above that was not what i had wanted....

Suppose I got plenty space on there anyways so its no biggie but it is a bit irritating.

---

### Post by srs5694 on 2011-05-31
First, that doesn't look like GParted, which is what most people use for this task. OTOH, perhaps it is, but just using a theme that makes it look different. If it's not GParted, though, and if the below suggestion doesn't help, you might try using GParted rather than whatever it is you're using.

Second, I notice that in your second and third screen shots, although you've changed the "Free space before" field, the "Size" field hasn't changed. This can sometimes happen if, as it appears you did, you change one field by typing its entry and don't click in another field. Clicking in another field registers your change and usually causes the program to recompute anything it needs to recompute. Thus, I suggest you do that. Alternatively, try using the graphic at the top of the dialog box to resize the extended partition. You can do this in GParted; when you move your mouse over the left end, the pointer should change to an arrow to indicate that you can click and drag to resize the partition.

---

### Post by iclestu on 2011-05-31
> **srs5694 said:**
> ......that doesn't look like GParted, .....

No, its partition manager. Hence the name of my post and the tags in the thread. No doubt you are correct about GParted being the prefered option of the majority of users but then Gnome is the prefered desktop environment of most users. I use KDE and therefore I am trying to alter my partition with KDE's tool which is, I am sure, up to the job. I dont think it is the tool that is the issue here....

> **srs5694 said:**
> 
Second, I notice that in your second and third screen shots, although you've changed the "Free space before" field, the "Size" field hasn't changed. This can sometimes happen if, as it appears you did, you change one field by typing its entry and don't click in another field. Clicking in another field registers your change and usually causes the program to recompute anything it needs to recompute. Thus, I suggest you do that. Alternatively, try using the graphic at the top of the dialog box to resize the extended partition. You can do this in GParted; when you move your mouse over the left end, the pointer should change to an arrow to indicate that you can click and drag to resize the partition.

This isnt it.... It is greyed out no matter where i click. 

Thanks for taking the time to response and for trying to help but Im afraid this isn't the issue.

---

### Post by jerrrys on 2011-05-31
you first have to shrink the primary partition

---

### Post by iclestu on 2011-05-31
> **jerrrys said:**
> you first have to shrink the primary partition

The primary partition?

Im not sure I understand what you mean: sda1 contains the bootloader, etc, yeah? not sure shrinking that is possible and how it would help.

sda2 is the windows partition and is already 'shrunk' in that the appx 30gb of space i want to utelise shows as 'unallocated', partition manager (and windows for that matter) already shows the windows partition at the 'reduced' size.  

Can you elaborate??

---

### Post by jerrrys on 2011-05-31
Can you elaborate??  yes i can, but first let me fire up my test box and make sure about this.  be back

---

### Post by jerrrys on 2011-05-31
ok, here goes

[ATTACH]193734[/ATTACH]
[ATTACH]193735[/ATTACH]
[ATTACH]193736[/ATTACH]
[ATTACH]193737[/ATTACH]

i recreated your setup with the 100M primary free space

and then NOT the primary but the extended partition resized

and now i am betting that all you are doing wrong is not turning swap off :)

EDIT:  and now i just realized in my hast that i mess up on my pics, but i think your getting the idea.

---

### Post by iclestu on 2011-05-31
> **jerrrys said:**
> ok, here goes

[ATTACH]193734[/ATTACH]
[ATTACH]193735[/ATTACH]
[ATTACH]193736[/ATTACH]
[ATTACH]193737[/ATTACH]

i recreated your setup with the 100M primary free space

and then NOT the primary but the extended partition resized

and now i am betting that all you are doing wrong is not turning swap off :)

EDIT:  and now i just realized in my hast that i mess up on my pics, but i think your getting the idea.

Swap was 'turned off'. I successfully unmounted the partition from the live CD. 

I appreciate you taking the time to try to help but I am sorry to say that I cannot make sense of your pics or your point. 

I still do not know what you mean by 'shrink the primary partition first'. Sorry if i am missing the point but im not sure if the pics were intended to elaborate or explain that point or if you moved onto something else??

---

### Post by jerrrys on 2011-05-31
ok, my pics are crap.  

forget what i said about the primary partition.  that was wrong.

resize the extended partition forward. that would be your sda4

---

### Post by iclestu on 2011-05-31
> **jerrrys said:**
> resize the extended partition forward. that would be your sda4

how?

thats kinda been the point of my thread. It wont allow it.

---

### Post by jerrrys on 2011-05-31
your pics indicate that your trying to resize sda5 and not sda4

---

### Post by iclestu on 2011-05-31
> **jerrrys said:**
> your pics indicate that your trying to resize sda5 and not sda4

No, sda4 contains sda5 and a swap partition. Look at the title bar of the pic. It IS sda4 im trying to change. I realise I cant increase the size of sda5 until sda4 (the extended partition containing sda5) is increased. 

The pic is perhaps misleading because it shows sda5 in the diagram (although, the title bar does show sda4, as i said and you can see the swap partition at the right hand side of the diagram thats not part of sda5) but, I assure you, it IS sda4 i am trying to amend. 

Thanks for your endeavors.

---

### Post by jerrrys on 2011-05-31
should of worked, sorry.  maybe someone can see what is missing.  again sorry

---

### Post by Irihapeti on 2011-05-31
Having trashed a partition through trying to move it, I think that the safest way would be as follows:

Backup the contents of the ext4 partition (sda5) - a good idea anyway.

Then delete the swap partition, sda5 and the whole extended partition.

Then you can re-create the extended partition in the free space, and the re-create the two logical partitions.

To backup the contents of sda5 (ext4), I suggest using something like TAR. See [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR) for details. Rsync might be another option, though it' not one I've used.

If you are using UUIDs in /etc/fstab, you'll need to alter them because the new partitions will have new UUIDs, but that's not very difficult to do.

---

### Post by srs5694 on 2011-05-31
> **iclestu said:**
> No, its partition manager. Hence the name of my post and the tags in the thread. No doubt you are correct about GParted being the prefered option of the majority of users

Your use of an obscure program that few people on this forum use is causing a lot of problems. Jerrys' posts, in particular, have been based on a mental model of GParted, and have therefore not helped you.

> but then Gnome is the prefered desktop environment of most users. I use KDE and therefore I am trying to alter my partition with KDE's tool which is, I am sure, up to the job.

Apparently it's not. Based on your description of its behavior, it seems to have a user interface bug that's preventing it from doing what it should be doing. I haven't looked at KDE's partitioning tools in a while, but the last time I did, they lagged GParted by quite a lot. If this is an offshoot of KParted, it seems that it still lags behind GParted.

Also, you should *not* get hung up on KDE vs. GNOME issues, particularly not when it comes to the utility of specific programs for specific tasks that aren't particularly related to the desktop. Personally, I use Xfce for my desktop; but I run GParted (loosely associated with GNOME), Konqueror (part of KDE), KDevelop (associated with KDE), NEdit (associated with no desktop environment), and other tools as necessary. Restricting yourself to just the tools that are associated with your chosen desktop environment is counterproductive. The bottom line:

Use what works.

> I dont think it is the tool that is the issue here....

I won't go so far as to say that I'm certain the tool is the issue, but the evidence is leaning heavily in that direction.

> [quote=srs5694]although you've changed the "Free space before" field, the "Size" field  hasn't changed. This can sometimes happen if, as it appears you did, you  change one field by typing its entry and don't click in another field.  Clicking in another field registers your change and usually causes the  program to recompute anything it needs to recompute.This isnt it.... It is greyed out no matter where i click.[/QUOTE]

This is why I now think you're dealing with a program with a user interface bug: That value *should* change. Changing correlated values when you update one in a dialog box is a job of the user interface code in the program. I can't see how such a problem could arise because of damaged partition table information, but I *can* see how it could arise because of a user interface bug. (BTW, I've programmed both simple GUI tools and moderately complex [partitioning](http://www.rodsbooks.com/gdisk/) [programs,](http://www.rodsbooks.com/fixparts/) so I understand the coding issues involved and where bugs are likely to creep in.)

The only reason I'm not *certain* it's a user interface bug is because I haven't interacted with the program on your computer. It's conceivable that you've misunderstood how to use the user interface -- or, looked at another way, that the user interface is so poorly designed that its intended method of use is very unclear. In that case, it might not be a bug, just a poor/obscure user interface.

Along those lines, have you tried:


[list]
[*]Clicking the up and down arrow symbols on the right edges of the fields?
[*]Clicking the image in the top of the dialog box to see if you can change the partition's size by a drag operation?
[/list]

---

### Post by jerrrys on 2011-05-31
ARRRRRR  i will learn to read, i will learn to read, i will learn to read, i will learn to read and i will write this a 1000 more times on the blackboard

---

### Post by iclestu on 2011-06-01
> **srs5694 said:**
> Your use of an obscure program that few people on this forum use is causing a lot of problems

Jerrys' posts, in particular, have been based on a mental model of GParted, and have therefore not helped you.



Apparently it's not. Based on your description of its behavior, it seems to have a user interface bug that's preventing it from doing what it should be doing. I haven't looked at KDE's partitioning tools in a while, but the last time I did, they lagged GParted by quite a lot. If this is an offshoot of KParted, it seems that it still lags behind GParted.

Also, you should *not* get hung up on KDE vs. GNOME issues, particularly not when it comes to the utility of specific programs for specific tasks that aren't particularly related to the desktop. Personally, I use Xfce for my desktop; but I run GParted (loosely associated with GNOME), Konqueror (part of KDE), KDevelop (associated with KDE), NEdit (associated with no desktop environment), and other tools as necessary. Restricting yourself to just the tools that are associated with your chosen desktop environment is counterproductive. The bottom line:

Use what works.



Hey there. Thanks for taking the time to respond.

I think some of the above is perhaps a little unfair. 

The TITLE of my original post described the program I am trying to use. 

It is the default partitioning utility that ships with kubuntu (the prefix to my thread) so it is questionable to say it is obscure and imply that this obscurity is causing problems. I am sure you would agree that the kubuntu project team would expect/hope/want their utility to work. Therefore, as an end user, I think it is fair game to bring support issues with that program to these forums? I made the point of giving my thread an appropriate title including the name of the utility to make a distinction between "I can't alter the partitioning of my hard drive" from "I am having trouble using the Partition Manager utility".

I am not hung up on KDE vs Gnome. Not at all. If resizing this partition was critical I would have looked at Gparted long ago. That, and any other utility I could find on google. If that didnt work my support request would have sounded much more like - help! I cant change the partitions on my hard drive, I have tried, xyz utilities with no success. 

The reason for using partition manager rather than gparted in first instance is simply that this is the utility that is on my (kubuntu) live cd.... Admitedly, my response to Jerry's post earlier could have made this point much clearer.

I don't think that it is in my interest, or in the interest of the community at large, to not investigate and discuss issues I have using supplied software for its intended purpose. Maybe I am getting the wrong end of the stick but, to me, the tone of your post seems to imply that I should simply have installed gparted and used that to accomplish my task. Would it not be better to post my issues here, discuss them with more knowledgable members, then if I find the problem is indeed in the software and not my setup (or indeed in my understanding) I can post a bug to launchpad to alert the appropriate project teams?? 

> **srs5694 said:**
> 
I won't go so far as to say that I'm certain the tool is the issue, but the evidence is leaning heavily in that direction.

This is why I now think you're dealing with a program with a user interface bug: That value *should* change. Changing correlated values when you update one in a dialog box is a job of the user interface code in the program. I can't see how such a problem could arise because of damaged partition table information, but I *can* see how it could arise because of a user interface bug. (BTW, I've programmed both simple GUI tools and moderately complex [partitioning]("http://www.rodsbooks.com/gdisk/") [programs,]("http://www.rodsbooks.com/fixparts/") so I understand the coding issues involved and where bugs are likely to creep in.)


:) this is exactly what i mean. As a (fairly) novice user I do not have your experience to confidently make that distinction between my errors, the applications errors and problems with my hardware. I am very grateful that you have given me these details because now I can file the bug report with confidence that im not wasting the project teams time.

> **srs5694 said:**
> 

The only reason I'm not *certain* it's a user interface bug is because I haven't interacted with the program on your computer. It's conceivable that you've misunderstood how to use the user interface -- or, looked at another way, that the user interface is so poorly designed that its intended method of use is very unclear. In that case, it might not be a bug, just a poor/obscure user interface.

Along those lines, have you tried:


[LIST]
[*]Clicking the up and down arrow symbols on the right edges of the fields?
[*]Clicking the image in the top of the dialog box to see if you can change the partition's size by a drag operation?
[/LIST]


I have attempted the first of these to no avail. I will give the second one a shot when I am back at my desktop pc later on and post my results.

Is there any way i can confirm that my partition table is ok? In your experience, is there any output that the guys at launchpad would want to see?

---

### Post by Irihapeti on 2011-06-01
It might be worth your while to get a liveCD with GParted. [Parted magic]("http://partedmagic.com/doku.php?id=start") is one I keep on hand, and GParted itself has a [liveCD]("http://gparted.sourceforge.net/livecd.php") version.

If one of these works where Partition Editor doesn't, then it does start to look like a problem with the latter.

---

### Post by glene77is on 2011-06-01
> **Irihapeti said:**
> It might be worth your while to get a liveCD with GParted. 
[SIZE=2][Parted magic]("http://partedmagic.com/doku.php?id=start")[/SIZE] is one I keep on hand, and GParted itself has a[SIZE=2] [liveCD]("http://gparted.sourceforge.net/livecd.php")[/SIZE] version.
. . .


Iri,
Good idea.
Parted-Magic Live-CD will load into RAM,  
then work on the HD totally un-mounted. 

Ice,
With gParted-Magic running in RAM,   
and the HD Linux system totally un-mounted,  
there is no inter-action between the running OS (on the HD) and the gParted routines.  :P

IMHO,
Good step in the right direction. 
I have used Parted-Magic Live-CD to  RESIZE  and  to  MOVE  partitions on several computers.
Patrick Verneer is the developing engineer for Parted-Magic, with website and forums for the programs. 
In reading, it is evident that there are LIMITATIONS on what you can do to a partition, and possibilities.  
First, I bought a Parted-Magic Live-CD from OSDisc,   
but   down-loaded later versions to burn. 
HTH, :)

---

### Post by srs5694 on 2011-06-01
> **iclestu said:**
> The TITLE of my original post described the program I am trying to use. 

"Partition Manager" sounds like a generic name, and without a clear identification that it's *not* GParted, it would be the assumption of most readers of this forum that you meant GParted, simply because GParted is so dominant in this realm.

> It is the default partitioning utility that ships with kubuntu (the prefix to my thread) so it is questionable to say it is obscure and imply that this obscurity is causing problems.

I certainly didn't mean to say that the program's obscurity was the source of its bugs, although now that I think about it, that might be true -- a program with few users will collect few bug reports and attract few developers, both of which are required to fix bugs.

My use of the word "obscure," and the "problems" I said it caused, were instead in reference to the miscommunication here.

> I am sure you would agree that the kubuntu project team would expect/hope/want their utility to work. Therefore, as an end user, I think it is fair game to bring support issues with that program to these forums?

Sure; but if you get consistent responses that the program you're using is buggy, or if nobody knows anything about it, and everybody suggests you use another program, you are well-advised to use that other program.

> I don't think that it is in my interest, or in the interest of the community at large, to not investigate and discuss issues I have using supplied software for its intended purpose. Maybe I am getting the wrong end of the stick but, to me, the tone of your post seems to imply that I should simply have installed gparted and used that to accomplish my task.

That's not the *tone* of my earlier post, that's the *major point* of my earlier post. That's not meant to be insulting or offensive; it's meant to be helpful and practical.

Two distinct motivations have emerged from in thread, and it's important to distinguish between them:


[list]
[*]As a practical matter to solve your problem now, it's best to switch to a partitioning program that works. This is the goal of most people posting to this forum, and so it's the default mindset of most people who offer suggestions. It's also the point of departure for my own previous posts to this thread.
[*]As a matter of improving the open source software ecosystem generally, and for KDE Partition Manager specifically, filing a bug report (or, better yet if you have the skill, locating the bug and submitting a patch to the developers) is the best approach. Unless you can fix the bug yourself, though, this will not solve the problem immediately, but it might help to improve the program in the future.
[/list]


Applying these two motives produces different responses to specific questions, such as "what should I do?" Most of the responses people have made have been biased toward the first motive; but it's becoming apparent that you're at least as concerned with the second. If so, you should certainly file a bug report in the hopes that the KDE Partition Manager will be improved in the future.

> Is there any way i can confirm that my partition table is ok? In your experience, is there any output that the guys at launchpad would want to see?

There are two good ways to test the validity of a partition table, in my experience:


[list]
[*]Run GNU Parted (command name "parted") or GParted on the disk. These utilities tend to flake out and report no partitions when the partition table has the slightest error. This seems to be a bug in libparted, upon which the utility you used is also based, but it might react differently, so I'd still advise using GNU Parted or GParted. If they show partitions, then the partition table is fine.
[*]Use fdisk to examine the partitions with sector precision, as in "sudo fdisk -lu /dev/sda". You can then examine the partition table data manually to locate overlapping partitions, partitions that extend beyond the end of the disk, and other problems. This requires you to understand some of the things that can go wrong, though. The KDE Partition Manager developers might want to see this output, but I suspect you'd have a hard time identifying errors in it.
[/list]

---

### Post by iclestu on 2011-06-01
> **srs5694 said:**
> Big post

Yeah - fair enough.

You are absolutely correct about the 2 motivations and although you  don't explicitly state it in your post (perhaps forum etiquette and good  manners prevented you? :smile:  ) you would have been correct to assert that the lack of clarity as to  which was motivating me at any one time is, for the most part, my fault  :wink: My apologies. I hope I have not caused offense.

I am grateful for the suggestions (feeding BOTH motivations) and as soon  as I get the opportunity I will post the next steps from both.

---

### Post by iclestu on 2011-06-01
> **srs5694 said:**
> 
Along those lines, have you tried:


[LIST]
[*]Clicking the up and down arrow symbols on the right edges of the fields?
[*]Clicking the image in the top of the dialog box to see if you can change the partition's size by a drag operation?
[/LIST]


:)

The latter of these worked! (well, to an extent!). The gui allowed me to do it and proceed (which wasnt happening before). Adjusting the 'free space before' field definetely SHOULD work though? The little arrows didnt work either.

Ok, so that got me as far as trying to commit the changes to my drive and I got this error:

-------------------------------------------------------------------------------------------------------------
**KDE Control Module: Operation Report**

    Date: 06/01/11 03:31 PM   Program version: 
  LibParted version: 2.3   KDE version: 4.5.2 (KDE 4.5.2)   Machine: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686   User ID: 0   
  **Move partition ‘/dev/sda4’ to the left by 28.98 GiB and grow it from 92.82 GiB to 121.80 GiB**    **Job: Check file system on partition ‘/dev/sda4’**  
**Check file system on partition ‘/dev/sda4’: Success**
 
    **Job: Set geometry of partition ‘/dev/sda4’: Start sector: 351,775,305, length: 255,433,500**   Could not set geometry for partition ‘/dev/sda4’ while trying to resize/move it.   

  **Set geometry of partition ‘/dev/sda4’: Start sector: 351,775,305, length: 255,433,500: Error**
 
   Moving extended partition ‘/dev/sda4’ failed.   

  **Move partition ‘/dev/sda4’ to the left by 28.98 GiB and grow it from 92.82 GiB to 121.80 GiB: Error**

--------------------------------------------------------------------------------------------------------------------------

Sooooo - I installed Gparted with the live cd! :) lol.

Seems there are two unrelated things at work as Gparted shows an error with the Windows partition. See attached. in retrospect, i notice that neither utility showed the free space in this partition..... I am guessing this is what is causing the above error and that the gui bug is unrelated?

So next up I file a bug report for the gui issue anyways, yeah? and separately I boot into windows (groaaannnn - i KNOW how many updates its waiting on, been a while!) and do a couple of chkdsk's as suggested by Gparted then see if I can change it?

---

### Post by iclestu on 2011-06-01
In the meantime........

> **Irihapeti said:**
> It might be worth your while to get a liveCD with GParted. [Parted magic]("http://partedmagic.com/doku.php?id=start") is one I keep on hand, and GParted itself has a [liveCD]("http://gparted.sourceforge.net/livecd.php") version.

If one of these works where Partition Editor doesn't, then it does start to look like a problem with the latter.

sounds like a really handy thing to have lying around!  |  DONE!

---

### Post by iclestu on 2011-06-01
Bug report filed for the GUI issue:

[https://bugs.launchpad.net/ubuntu/+source/partitionmanager/+bug/791474](https://bugs.launchpad.net/ubuntu/+source/partitionmanager/+bug/791474)

---

### Post by iclestu on 2011-06-01
desktop pc is 'applying pending operations' as we speak and moving the partitions. Thanks to all of you for your help.

Hope it all goes ok.....

---

### Post by glene77is on 2011-06-01
> **iclestu said:**
> In the meantime........
sounds like a really handy thing to have lying around!  |  DONE!

Iclestu, 
You have demonstrated much courage in the face of critical suggestions.  :KS

Installed the Parted-Magic subdir in my XP C:/pmagic, and pointed my grub/grub.cfg to it.
. . . boots just like  Verneer said it would.  
Installed the Parted-Magic subdir in a simple (hd0,sd0) base directory controlled by grub4dos ..
. . . boots just like  Verneer said it would.  
Has been a good utility.

---

### Post by glene77is on 2011-06-01
> **iclestu said:**
> desktop pc is 'applying pending operations' as we speak and moving the partitions. Thanks to all of you for your help.

Hope it all goes ok.....

Thanks for marking this thread [solved].
Please return to the forum as a valued contributor.   :)

---

### Post by Irihapeti on 2011-06-01
> **iclestu said:**
> desktop pc is 'applying pending operations' as we speak and moving the partitions. Thanks to all of you for your help.

Hope it all goes ok.....

Please let us know how it went, and what you used in the end to do the task.

---

### Post by srs5694 on 2011-06-01
> **iclestu said:**
> My apologies. I hope I have not caused offense.

No apologies are necessary and no offense was taken. Miscommunication can and does occur, and as such things go this wasn't a huge one.

> **Job: Set geometry of partition ‘/dev/sda4’: Start sector: 351,775,305, length: 255,433,500**   Could not set geometry for partition ‘/dev/sda4’ while trying to resize/move it.   

This sounds like a bug in the program's handling of CHS addresses vs. LBA addresses. If you don't know what that means, it's the ancient and (today) useless mode of identifying sectors vs. the newer mode. Both modes are built into MBR partition tables, but CHS mode is useless today because it tops out at a bit under 8 GiB. Nonetheless, both need to be computed.

Another possibility is that it's an issue related to partition alignment -- on "cylinder" boundaries (obsolete and useless today) vs. on 1 MiB boundaries (which optimizes performance for some modern disks). These two possibilities could actually be related -- if the program requires that partitions start and end on cylinder boundaries, it might not like existing partitions that don't do so, and might issue an error like the one you've quoted.

Either way, it's a bug that's deeper than the user interface. It *might* be possible to work around it by leaving a small gap between your partitions -- but as you've moved on to GParted, I guess you won't be testing that.

> Seems there are two unrelated things at work as Gparted shows an error  with the Windows partition. See attached. in retrospect, i notice that  neither utility showed the free space in this partition..... I am  guessing this is what is causing the above error and that the gui bug is  unrelated?

No, the Windows partition (/dev/sda2) problem is unrelated to the error in adjusting /dev/sda4 -- the two are on different partitions and can't be related.

Yes, the GUI bug is unrelated to either of these other issues.

In sum, you've found two distinct bugs in the program and an unrelated bit of data corruption on one partition.

> I boot into windows (groaaannnn - i KNOW how many updates its waiting  on, been a while!) and do a couple of chkdsk's as suggested by Gparted  then see if I can change it?

Running CHKDSK from Windows is the only way I know of to fix problems on NTFS. Linux has no good NTFS maintenance tools. (There is one called ntfsfix, but it just does a few very simple tests and then flags the filesystem as requiring further checks under Windows.)

---

### Post by iclestu on 2011-06-02
> **srs5694 said:**
> 

No, the Windows partition (/dev/sda2) problem is unrelated to the error in adjusting /dev/sda4 -- the two are on different partitions and can't be related.



No?? DOH!

Lol - i just assumed that this was THE problem. I ran chkdsk to fix it as suggested but thought that, as it was solved anyways I'd try out that livecd **Irihapeti** suggested..... LOL - after all my grand posturing I used Gparted to get around the issue after all!! In my defence thats NOT what I thought I was doing. I thought I had identified only that Gparted gave a more meaningful error message and just kinda assumed that now I fixed it with chkdsk that either utility would do it and wanted to play with my new toy (that livecd). It sounds so pathetic now as I type..... 

Somebody open a window my 'moral high horse' needs to learn to fly.....

Lol - nevermind. At least I put in a bug report for that gui thing....

```
fdisk -l
```(after reorganising)  gives

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93c7cf00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
**[COLOR=Red]Partition 1 does not end on cylinder boundary.[/COLOR]**
/dev/sda2              13       19880   159581152+   7  HPFS/NTFS
/dev/sda3           37798       38914     8964096    7  HPFS/NTFS
/dev/sda4           19880       37798   143921152    5  Extended
/dev/sda5           19880       37210   139199488   83  Linux
/dev/sda6           37210       37798     4719616   82  Linux swap / Solaris

Partition table entries are not in disk order

```which seems to support your cylinder boundaries hypothesis...

No sense trying to fix that now as everything works ok though (right?)....

---

### Post by Irihapeti on 2011-06-02
From the output of fdisk, It looks as though you've succeeded in doing what you set out to do. Good one.

As for the cylinder boundary thing, I'd leave it alone if everything is working.

Yes, the liveCD is a very useful thing to have handy. It's got all sorts of other recovery programs that can get one out of a mess. It's saved my bacon a time or two.

---

### Post by srs5694 on 2011-06-02
> **iclestu said:**
> ```
**[COLOR=Red]Partition 1 does not end on cylinder boundary.[/COLOR]**

```which seems to support your cylinder boundaries hypothesis...

No sense trying to fix that now as everything works ok though (right?)....

Correct. No modern OS cares about cylinder boundaries any more. Linux's fdisk just complains about it out of habit, I think, or perhaps to alert people who *do* still run ancient OSs that might not like that sort of setup.

---

