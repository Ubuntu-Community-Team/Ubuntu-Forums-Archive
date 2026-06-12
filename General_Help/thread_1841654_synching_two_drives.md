---
title: "synching two drives"
date: 2011-09-09
forum: General Help
---

### Post by rmcellig on 2011-09-09
Here is my situation. I have two FAT formatted external drives. Drive one contains my mp3 files that I use for my radio show (over 52,000 of them). Drive two will be an exact copy of drive one. I always want drive two to be an exact copy of drive one.

I would also like to schedule the synching between these drives. What is my best, quickest and easiest method to use? If possible, I would like a GUI solution. If none is available, I have an app called Scheduled tasks which allows me to run cron jobs. I would like a set it and forget it solution that I can easily maintain.

Thanks so much!! I googled this and found many options. I would like to hear from people on this forum for their expert opinion. :)

---

### Post by oldfred on 2011-09-09
I use rsync for backups, but have not used grsync which is the gui tool that sets some of the parameters.

Do you have to have FAT for some compatibility reason?

I used to backup to a FAT partition not realizing all the issues. My backups were always 4GB so some odd reason no matter how much my system grew. I thought it was efficent, but then learned that FAT has a max file size of 4GB and most software just does not tell you that the file was truncated since it was copied.

Also FAT is not journalized so chkdsk takes forever and may not be able to repair all issues that NTFS might be able to repair.

FAT is fine for small devices where a journal does not add much but I stopped using it on my Hard drive.

NTFS and Fat info:
FAT 4GB file max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
[http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)

---

### Post by rmcellig on 2011-09-09
This is my situation. The computer at the radio station is a PC, so I formatted my drive as FAT 32. Could I format it NTFS? I just want to make sure that when I go to the radio station that their XP Pro machine can read my drive, when I go to do my show. This seems like the only option I have (to go NTFS?)

---

### Post by oldfred on 2011-09-09
5 years ago or so when I first started dual booting I used FAT as the NTFS had some reported issues. Three years later I converted to NTFS and have shared that with my XP install. But I now rarely use XP.

I think with some devices like Xbox and a few others (may even Mac) you have to use FAT32, but if it is windows I would consider converting to NTFS for a better file system. Good backups are required either way. And I do not think you can just convert without destroying data, but maybe Windows offers something. I just used a new partition and copied everything to it. I think I still have the old FAT partition but have not even mounted it in a couple of years. New hard drive with lots of room made the small partition on an older drive not worth reusing (yet).

---

### Post by rmcellig on 2011-09-10
I just remembered that as much as I would lke to use NTFS because I use a mac (for now) I need to have a drive that I can save my songs to. I don't thnk there is a way to save to NTFS on a mac. I use Os x lion as my mac Os. If I could find an audio editor that is simple to use other than audacity I would switch to linux. I use a feature in my softare for the mac called paste mix that audacity doesn't have.


On the Linux side is there a way I can write to NTFS drives?

---

### Post by oldfred on 2011-09-10
Ubuntu includes the NTFS drivers with a standard install. I do not think you can create NTFS during an install, but you can click on NTFS and use it. Permissions and ownership can be an issue since NTFS does not support either. You have to set as a default the permissions you want as you mount the NTFS partition. 

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

more info on fstab & mounting in general:
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by rmcellig on 2011-09-10
I formatted one of the drives NTFS on my Ubuntu machine. No problem so far. I plugged the drive1 into a USB hub and then plugged the other drive2 (still FAT 32 formatted into the hub as well. I started copying some files from drive2 to drive1. It started copying but then came up with a message that drive1 was unavailable. Same thing happened in Ubuntu on my iMac. I tried different hubs, no dice. Worked fine on my other computer running Windows7 through the same usb hub I was using on my ubuntu laptop. Did I miss something when formatting the drive in Ubuntu? Are there specific steps I have to do in disk utility to format the drive correctly as NTFS so that I can read/write to it in Ubuntu?

---

### Post by Hugh971 on 2011-09-10
you'll probably want to stick with FAT32 for now as a vanilla OS X install won't write to NTFS.

In answer to your original question you can use rsync to sync the disks. To do that use the following command.

```
sudo rsync -a /path/to/source/disk /path/to/destination/disk
```

If you want to do this as an automated job you can set up a cron job to do this. To access cron run

```
sudo crontab -e
```

and add a line for your sync. Crontab reads it's lines like minute hour day-of-month month day-of-week command. So for example if you wanted to do a backup at half one in the afternoon every day add the following line.

```
30 13 * * * rsync -a /path/to/source/disk /path/to/destination/disk
```

Hope this helps.



Hugh

---

### Post by rmcellig on 2011-09-10
Thanks! I have the app automated tasks that I use for cron jobs so I would imagine it would only be a case of me copying this into in.

30 13 * * * rsync -a /path/to/source/disk /path/to/destination/disk

Regarding my external drives. I am moving everything of my fat32 formatted drive, reformatting it as NTFS and then copying everything back over. What I find really cool is that I am dual booting on my iMac with Ubuntu so I just have to restart my iMac into Ubuntu, format the drive as NTFS, copy the stuff that was on the fat32 drive over to the newly formatted NTFS drive and that's it. I love it!!

I am spending about 80% of my time in Linux and less and less on my Mac because I find that I can get things done quicker in Linux for some reason. And that, I like very much!!

---

### Post by JC Cheloven on 2011-09-10
> **rmcellig said:**
> This is my situation. [COLOR="Red"]The computer at the radio station is a PC[/COLOR], so I formatted my drive as FAT 32. Could I format it NTFS? I just want to make sure that when I go to the radio station that their XP Pro machine can read my drive, when I go to do my show. This seems like the only option I have (to go NTFS?)

Just to be precise, please read [here]("http://www.gnu.org/philosophy/words-to-avoid.html") (scroll down till you find "PC"). A Personal Computer is a piece of hardware with a particular purpose, it may be running gnu-linux, macOS, windows, BSD, ...  ;)

> If I could find an audio editor that is simple to use other than audacity I would switch to linux.  Are you informed about the choices? There are quite a lot, from the simple MHWaveEdit to the mature and polished Ardour, half way in between Jokosher or Traverso (the one in my signature), some audio+sequencers like rosegarden, muse, LMMS... all in the repos! 

Best
JC

---

### Post by rmcellig on 2011-09-11
I was aware of some of the other audio editors out there and was going to try them out. I have never heard of Traverso. I am really looking forward to trying it out! I now have both of my external drives formatted NTFS. I copied all the music from my old drive to the newly formatted drive and will try it out today when I go to the radio station to do my show. When I get home I will try using grsync to sync up the drives. Like I said before, I am spending less time in Mac OS X and more time in Linux. Love it!!

---

### Post by rmcellig on 2011-09-11
I tried synching my drives and right off the bat I am getting errors. I tried a straight copy/paste of some folders on radio1 drive to the radio2 drive. Same thing. Attached is an example of the errors I am receiving. Both drives are formatted NTFS. When I copy the same folders to the internal HD of the laptops I am using, there is no problem. What do I need to do to resolve this problem. What information do you need from my end to help me out?

---

### Post by YesWeCan on 2011-09-11
What does the "Show more details" say?

---

### Post by rmcellig on 2011-09-11
It's the error that is shown in the pic I posted. The problem seems to happen in Ubuntu on both machines as well as win7. Both drives were formatted NTFS in Ubuntu 11.04.

---

### Post by YesWeCan on 2011-09-11
Oh I see, the details are being shown already.

Let me understand this. You originally had Radio 1 and Radio 2 external drives in FAT32 with identical files on them. Then you converted both to NTFS and put the files back on them (by some means).

You tried rysnc from R1 to R2 and got errors. What were they and what program generated them? Are these rsync errors or something else?

You tried a file browser copy & paste from R1 to R2 and got errors. What were they and what program generated them?

When you copied a folder from R1(?) to an internal drive they are readable without errors.

And are you using OS X to do all this? So that error window is a Mac file browser error window?

---

### Post by YesWeCan on 2011-09-11
Would you please post the output of
sudo blkid
and
sfdisk -luS

Also, exactly what volume names have you given the two external drives?
I take it you reformated these drives using Ubuntu 10.04 rather than Windows.


There is a bunch of stuff here [http://ubuntuforums.org/showthread.php?t=1500384](http://ubuntuforums.org/showthread.php?t=1500384) about this symptom. I suspect most is not the specific issue you are having but it is worth eliminating obvious things like duplicate UUIDs and bad volume names and bad partition tables.

Did you say how big these external drives are?

---

### Post by rmcellig on 2011-09-11
home@home-HP-Pavilion-dv6-Notebook-PC:~$ sudo blkid
[sudo] password for home: 
/dev/sda1: LABEL="System Reserved" UUID="CA7C78727C785AE1" TYPE="ntfs" 
/dev/sda2: UUID="CC3A7E773A7E5F00" TYPE="ntfs" 
/dev/sda5: UUID="ac467b2b-8d20-4aca-8e1d-dbbb4f352a2e" TYPE="ext4" 
/dev/sda6: UUID="2238a5ca-cc46-4781-95fc-a5a8eda9e716" TYPE="swap" 
/dev/sdb1: LABEL="radio1" UUID="0D2F93382927AE81" TYPE="ntfs" 
/dev/sdc1: LABEL="radio2" UUID="08F888E16AD434C5" TYPE="ntfs" 
home@home-HP-Pavilion-dv6-Notebook-PC:~$ 
home@home-HP-Pavilion-dv6-Notebook-PC:~$ sfdisk -luS
home@home-HP-Pavilion-dv6-Notebook-PC:~$

---

### Post by rmcellig on 2011-09-11
Let me understand this. Your originally had Radio 1 and Radio 2 external drives in FAT32 with identical files on them. Then you converted both to NTFS and put the files back on them (by some means).

Yes. That's correct and when I did my radio show today using radio 1 formatted as ntfs, everything worked fine. I did my show with no problems.

You tried rysnc from R1 to R2 and got errors. What were they and what program generated them? Are these rsync errors or something else?

I can't remember what the rsync errors were because I didn't take any screenshots.

You tried a file browser copy & paste from R1 to R2 and got errors. What were they and what program generated them?

The only error that appeared is the pic i attached to my previous post.

When you copied a folder from R1(?) to an internal drive they are readable without errors.

yes. that's correct.

---

### Post by rmcellig on 2011-09-11
Let me understand this. Your originally had Radio 1 and Radio 2 external drives in FAT32 with identical files on them. Then you converted both to NTFS and put the files back on them (by some means).

Yes. That's correct and when I did my radio show today using radio 1 formatted as ntfs, everything worked fine. I did my show with no problems.

You tried rysnc from R1 to R2 and got errors. What were they and what program generated them? Are these rsync errors or something else?

I can't remember what the rsync errors were because I didn't take any screenshots.

You tried a file browser copy & paste from R1 to R2 and got errors. What were they and what program generated them?

The only error that appeared is the pic i attached to my previous post.

When you copied a folder from R1(?) to an internal drive they are readable without errors.

yes. that's correct.

---

### Post by rmcellig on 2011-09-12
Both drives are 320GB in size. They are names radio1 and radio2. Both drives were formatted NTFS using Ubuntu 11.04.

My Rsync errors:

file has vanished: "/media/radio1/In Transition Archives/younglesterPolka Dots And Moonbeams.m4a"
file has vanished: "/media/radio1/In Transition Archives/younglesterandteddywilson_prisoneroflove.m4a"
file has vanished: "/media/radio1/In Transition Archives/zentnermichaelTears and Spheres.m4a"
file has vanished: "/media/radio1/In Transition Archives/zentnermichaelzentnermichaelChapter Seven.m4a"
file has vanished: "/media/radio1/In Transition Archives/zetterlundmonicaIt's Alright With Me.m4a"
file has vanished: "/media/radio1/In Transition Archives/zetterlundmonicaMore Than You Know.m4a"
WARNING: bebopandbeyondCon Alma + I Waited For You.m4a failed verification -- update discarded (will try again).
rsync: read errors mapping "/media/radio1/In Transition Archives/bebopandbeyondCon Alma + I Waited For You.m4a": Input/output error (5)
ERROR: bebopandbeyondCon Alma + I Waited For You.m4a failed verification -- update discarded.
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]
Rsync process exit status: 23

---

### Post by rmcellig on 2011-09-12
I think I may have solved the problem. I plugged radio1 directly into the usb port on my laptop. radio2 was plugged into the usb hub. So far, Grsync is working fine. I will post back with the end result but what I want to know is why I have to plug radio1 into the usb port on the laptop and not the hub. Is there something wrong with my radio1 drive? my radio1 drive is one I built myself. I bought an external case and put a 2.5 inch drive in it.

---

### Post by rmcellig on 2011-09-12
Finally success synching!!


30 13 * * * rsync -a /path/to/source/disk /path/to/destination/disk

Could I add this code to the Grsync window so that the sync task is automated or do I have to use the Scheduled tasks application?
Now that I successfully completed my initial sync, is it just a matter of running the cron job above to make sure radio2 is always in sync with radio1 USB NTFS formatted drives? I want to keep this all as simple as possible.

---

### Post by YesWeCan on 2011-09-12
So it was something related to the USB hub, eh? Glad you got it working.

---

### Post by rmcellig on 2011-09-12
I think it is something related to radio1. I tried a test. I copied two small files to radio1. I then ran grysync. The files appeared on radio2 as was expected. When I deleted those two files from radio1 and re synched, the files were still on radio2. I would have expected them to be deleted after the re sync because they were deleted on radio1. What I am after is that radio2 to always be an exact mirror of radio1. How do I make sure this happens?

---

### Post by YesWeCan on 2011-09-12
See [http://linux.die.net/man/1/rsync](http://linux.die.net/man/1/rsync) under the '--delete' section.

---

