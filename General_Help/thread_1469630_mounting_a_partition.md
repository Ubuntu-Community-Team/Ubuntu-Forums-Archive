---
title: "mounting a partition"
date: 2010-05-02
forum: General Help
---

### Post by Scunnered on 2010-05-02
I am having great difficulty in establishing a separate /home partition.  When reading my latest edition of Linux Format they make reference to manual partitioning stating :

"*You just need to create another partition alongside root and swap, give it a file system and assign a mount point of **/home***" 

and when attempting to do so I am totally unable to mount the partition that I created.

Currently there are /dev/sda1 an ext4 partition with a mount point of / and sda3 again an ext4 partition and this has no mount point.  It is the /dev/sda3 that I wish to make my** /home**

Having checked the information about /dev/sda1 it displays the status as Mounted on / but when checking sda3 it is not shown as mounted.

How do I establish the mount point on /dev/sda3?

It appears to me that this is the rock that I am perishing on. I am keen to have the ability to check further issues of Ubuntu without having to loose my data.  

Your kind assistance will be appreciated

---

### Post by spiky001 on 2010-05-02
hi i take it you hav'nt just installed ubntu then?

---

### Post by Scunnered on 2010-05-02
Not too sure what you are asking about.

I have Lucid up and running  mainly to my liking but as I intend to run it until the next LTS edition comes up I had wanted to establish a separate /home partition.

So far everything that I have tried does not work and it was the magazine article that prompted me to ask about mounting as there was no mount point identified against /dev/sda3.

I hope this will clarify matters and that you will be able to assist further.

---

### Post by spiky001 on 2010-05-02
if you type in terminal
```
ls
```

you get a list of Dirs eg Downloads Documents etc? If so this is your home if so have a look at this [link]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by ajgreeny on 2010-05-02
I am not sure from what you say, but were you trying to make the /home partition at install time, or after having an up and running installation?

If the former have a look at [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

If you already have ubuntu but now wish to add /home look at [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by dino99 on 2010-05-02
> **Scunnered said:**
> Not too sure what you are asking about.

I have Lucid up and running  mainly to my liking but as I intend to run it until the next LTS edition comes up I had wanted to establish a separate /home partition.

So far everything that I have tried does not work and it was the magazine article that prompted me to ask about mounting as there was no mount point identified against /dev/sda3.

I hope this will clarify matters and that you will be able to assist further.

a all in one step: [http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

you may install MountManager for your ease and tweak devices and partitions as you need ( system admin mountmager)

---

### Post by Scunnered on 2010-05-02
My thanks to you all for your contributions.

I am getting more confused by the minute and would ask that you please take pity on me as my level of knowledge with Linux is one of learner.  Anything that I know and feel confident to work with is down to all the kind assistance given on this forum.

From what I have read in magazines and in the Ubuntu documentation I have to create space on my hard drive to accommodate a separate / home partition.  I understand that by using Gparted that I can re-size my drive.  Initially I downloaded Lucid on the complete HD.  Subsequent to that I then used my previous Karmic DVD to run as live and then re-sized my /dev/sda1 ext4 partition.

Having done so I then created a new ext4 partition which when established displayed as /dev/sda3.

Comparing both of these partitions I find when looking at the information about the partitions that /dev/sda1 shows the status as : Mounted on /.  However dev/sda3 shows as not being mounted.

Again when highlighting each partition and the partition button is clicked on sda1 it is possible to unmount but on sda3 the option is greyed out.

Following the link provided by Spiky 001 when I attempted to mount the new partition using mkdir /mnt/newhome the following displays:

 &#8220;**cannot create directory `/mnt/newhome': File exists**&#8221;

which only confuses me further.

Can anyone please offer further guidance?

Thanking you in anticipation

---

### Post by dino99 on 2010-05-02
wonder why newbies always choose the hardest way :(, by the way this is how they learn :P

" Can anyone please offer further guidance? "

for sure, follow my post and dont tweak by hand when devs have fine tuned tools for our ease, mountmanager is your friend, have you meet it ?

then you may take time to dig the existing menu and their settings

---

### Post by Scunnered on 2010-05-02
**dino99**

I could respond with why do newbies receive so many different instructions, but as that is part of the way Linux works I shall have to live with things. 

It does however cause no end of confusion.  I looked at mountmanager and was having great difficulty in understanding what was needed.  Eventually I hit on a mount button and in a text box entered /home.  This seemed to take OK so I closed the file and had a look at GParted where it showed up on my ext4 sda3 with the /home in the mount point.  This seemed to be fine so I had a look at Places / home folder and at this point discovered that what ever was done caused the system to display the default appearance theme.

Decided to remove mountmanager and reboot.  This resulted in everything reverting back to where I started.

Went and had a look at the offering from spiky001 but when using:-

"find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/"

ended up with a barrowload of error messages advising that it could not be found. 

Gave up on this and went to see AJs guide.  Got as far as the fstab but when asked to enter the additional lines found that I did not understand and gave up totally on this.

Now my dev/sda3 partition shows a mount point of /mnt/newhome.

Where do I go from here?

She who must be obeyed came into the room took one look at me and decided that I needed strong drink. Brought some wine (the good stuff not the nonsense to make Windows offerings work) so hope this restores me to a better frame of mind.

I hope that by every ones kind assistance things will improve and a positive result will ensue. 

Again my thanks to all

---

### Post by WorMzy on 2010-05-02
As far as I know, you can't mount a partition onto a folder which is not empty; so first off, is your /home folder empty? (in a terminal: 'ls /home')

If no, then you need to move the contents of /home somewhere else before you do anything else.

Once home is empty, you can then mount your new partition as /home (you can do this by making an entry in fstab, then running in a terminal: 'mount -a')

Let me know which part of this you're currently up to and having trouble with, and I'll try to explain things in more detail.

---

### Post by Scunnered on 2010-05-02
**WorMzy**

As instructed I have copied all my /home folder to a USB drive. Using your instruction displays as :

ian@ian-laptop:~$ ls /home
ian
ian@ian-laptop:~$ 


Firstly can you please advise that on sda3 the mount point of mnt/newhome is acceptable? If so if I then open the fstab what do I enter into this area.

I have identified the UUID for my drives so that part I know it is how all the things go together.

I am positive that you will no what I should be doing and would suggest that you treat this as an IDIOTS GUIDE which is most appropriate in my case.

Many thanks for your kind assistance

---

### Post by spiky001 on 2010-05-02
ok I hav'nt done this this way ,You have copied all yor stuff to USB? have you removed the old home?

---

### Post by WorMzy on 2010-05-02
No, /mnt/newhome is not the right place to mount it permanently, your home directory should always be /home (unless you want to do a lot of fiddly configuration which I advise against!) However, if you have already mounted it there, then you can copy the contents of your current home folder there now. If you haven't mounted your partition there yet, do so now with:
```
sudo mount /dev/sda3 /mnt/newhome
```Then copy files across to it with:
```
sudo cp -p -r /home/ian /mnt/newhome
```This might take a while.After that, check /mnt/newhome to see if everything copied over correctly. Once you're sure that it has, you then need to claim ownership of the copied folder by  running:
 ```
sudo chown ian:ian /mnt/newhome
```

Once you've done the above, you can clear your /home folder with:
```
sudo rm -r /home/*
```Then add an entry to fstab to mount /sda3 to /home with default settings. So:
```
/dev/sda3 /home ext4 defaults 0 0
```Once that's done, you can need to unmount /dev/sda3 before you can remount it in the right place, so run:
```
sudo umount /mnt/newhome
```Then run:
```
sudo mount -a
```to remount it.

---

### Post by WorMzy on 2010-05-02
See above

---

### Post by WorMzy on 2010-05-02
see above

---

### Post by Scunnered on 2010-05-02
**WorMzy**

Many thanks for your posts.

I attempted to follow your instructions starting with **#13** but only got as far as the first line as I was informed that /dev/sda3 was mounted or that /mnt/newhome was in use.

As you had stated that /mnt/newhome was not the right place I decided to delete that partition and start again.

I ran a live CD and using GParted deleted /dev/sda3.  Having done so I created a new partition which shows up as dev/sda3 an ext4 file system.  It does not show a mount point nor does it appear to be mounted when I click on the partition details.

When I shut down the live CD and re-booted all my earlier settings were removed from the system and I therefore assume that my home folder is totally empty.

I am struggling on how I achieve setting up the /home and would ask that you please advise how it is achieved.  Firstly where do I issue the instructions that you provide, is it in Lucid or via a live CD?  Secondly what is the sequence to achieve this end.

I appreciate your efforts in directing me to my goal and hope that with kind assistance that we will get there at last.

---

### Post by spiky001 on 2010-05-02
whats the output of ls now? so we can see what is there



```
ls
```

---

### Post by WorMzy on 2010-05-02
Could you do a ls of /mnt/newhome? It appears that it isn't empty (hence the error: "can't mount /mnt/newhome is in use"). If there are files in there, and they're not important, remove them with:
```
sudo rm /mnt/newhome/*
```

All these commands should be done while booted into Lucid, not the Live CD. If you do them while on the Live CD, the changes won't be permanent and will disappear after you restart.

---

### Post by Scunnered on 2010-05-02
**spiky001**

As requested ls produced :-

ian@ian-laptop:~$ ls
Desktop  Documents  Downloads  Music  Pictures	Public	Templates  Videos
ian@ian-laptop:~$ 

I have not loaded any data into the documents, music pictures and videos. I assume templates will be a default and contain something.

**WorMzy**

As advised I started afresh and my partitions are as the screen shot.  Again I assume that the 900 MiB is the data needed to create this partition.

I hope this assists.

---

### Post by WorMzy on 2010-05-02
Okay. I've merged post #13 with my other two posts, so the instructions should be right now. But before you try them, did you check the contents of /mnt/newhome and remove any files?

---

### Post by linuxonbute on 2010-05-02
We know it is difficult to understand Linux when you have been used to the way Windows does things. Remember though that Windows protects you AND limits you whereas Linux will let you own your PC.

I don't want to add to your problems but, on the other hand, we all tend to work on problems in different ways as we have different levels and kinds of experience. Do not give up. You can get this solved and in the process become more skilled yourself.

You could give us information which would help us to help you.

For example :

sudo fdisk -l /dev/sda   ( That is lower case L )

will give information on the current state of your disc.

From that we can see better what you have and maybe ask you to try further commands.

---

### Post by Scunnered on 2010-05-02
**linuxonbute**

Here is the output from your request

"ian@ian-laptop:~$ sudo fdisk -l /dev/sda 
[sudo] password for ian: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00043dd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1298    10426153+  83  Linux
/dev/sda2           19088       19458     2972673    5  Extended
/dev/sda3            1299        7738    51729300   83  Linux
/dev/sda5           19088       19458     2972672   82  Linux swap / Solaris

Partition table entries are not in disk order
ian@ian-laptop:~$ "

Trust this assists.

Dont worry about the learning problems.  I was prepared to have to work at things so from that point of view I am not over worried.  My biggest frustration is that my level of experience is limited and often responders give far too much credit than I deserve.  It is then that I turn to drink as yet again I have to display my ignorance and plead for further assistance/clarification.

---

### Post by WorMzy on 2010-05-02
Did you follow the instructions I gave you? If you got an error, post it here and I'll advise you how to avoid it.

---

### Post by Scunnered on 2010-05-02
**WorMzy**

It looks like we may both have been composing posts at the same time. In #19 I advised that I started again creating a new partition to allow for /home.

Should I use your #13 avoiding references to /mnt/home?

No sooner than I finish this post I find you have also posted. We will have to draw breath or one of us will expire prematurely

---

### Post by WorMzy on 2010-05-02
Ah, sorry, I missed that. If you run
```
sudo mkdir /mnt/newhome
```
and *then* follow the instructions, it should all work perfectly.
Afterwards, you can remove mnt/newhome with
```
sudo rmdir /mnt/newhome
```

:)

---

### Post by ajgreeny on 2010-05-02
Going right back to my post #5 in this thread, I suspect that the easiest way for you to proceed might be to start from scratch again and do a clean install following the first of the two links I put in that posting.  You already have your personal home files backed up onto a usb external drive, including the hidden folders, I hope, which contain all your emails and firefox bookmarks etc etc, so double check that.

I would then boot to the live CD, delete all the partitions on that hard drive with gparted, and then follow that first link I gave you earlier.  You could keep the current swap partition, or you could make sure it is not being used with a right click and choose "swapoff" if it is available and then delete that.  Then reinstall the whole system again and you may find everything becomes a lot clearer and easier than trying to move /home from a current install into a new partition.

---

### Post by Scunnered on 2010-05-02
**ajgreeny**

Many thanks for your post.

I had attempted earlier when initially installing Lucid to create the /home partition at the time but got into a fankle.

There is so many questions and answers that I feel that I am in an information overload.  In the circumstances I will sleep on things and will get back to everyone tomorrow.

Meanwhile my thanks to everyone for their kind assistance and patience with me in addressing the problem.

---

### Post by WorMzy on 2010-05-02
Ok, hopefully we can get this sorted tomorrow. My instructions work, I've carried them out myself, but I don't think I'm good enough at writing them down. So if you can follow them step by step and post here which step you're on  if you encounter a problem, I can try to explain that step in a more understandable way.

---

### Post by Scunnered on 2010-05-03
My sincere thanks to each and everyone who offered their assistance in this matter.

I am pleased to report that having slept on things that I have been able to resolve the problem.

**WorMzy**

Following your instructions in your last post I found that it was impossible to mkdir /mnt/home as the system kept informing me that there was already a file.  I made 2 or 3 attempts but each time was blocked at the first step.  On reflection I considered it better to start totally afresh.  I felt that one of us would have got demented carrying on the way we were and this was my main concern.  No doubt if we had struggled on **you** would have found the solution. 

I therefore followed the advice from **ajgreeny ** and paying close attention to the details found that everything worked perfectly. In fact it was so easy that I even managed it first attempt.

Once again my sincere thanks for all your kind assistance.

---

### Post by WorMzy on 2010-05-03
No problem, I'm just glad you got it sorted in the end.

That "file exists" error just meant that you'd already created the directory; the first time you ran mkdir /mnt/home probably worked, but it doesn't tell you that it worked, it just makes the directory and silently exits. I think you must have interpreted it's silence as an error and tried it again, which is when it really does encounter an error. If that wasn't the case, then just changing the name of the directory you're making would have worked. (So mkdir /mnt/abcdefg instead of /mnt/home).


Not that it matters now, but I just thought I'd explain in case you were curious. :)

---

### Post by Scunnered on 2010-05-03
**WorMzy**

Who ever that said a little knowledge is a dangerous thing I am sure had me in mind.
Once again my lack of Linux skills lets me down again.

I am happy with your explanation and hope that it will penetrate before I fall into the trap again.

Many thanks

---

### Post by ajgreeny on 2010-05-03
Great!  Glad you are now the proud owner of a separate /home.  I told you it was easy, didn't I.

You will never regret it, that's for certain, as it makes life so much easier in any future upgrading of you distro.

---

