---
title: "URGENT: need help recovering files from unbootable partition"
date: 2010-05-02
forum: General Help
---

### Post by not1 on 2010-05-02
Hi guys

After realizing 10.04 Final doesn't support Intel 855 graphics card the hard way (upgrading to 10.04 from 9.10), I did some very silly things and now cannot even choose past kernals or go into failsafe graphics mode (which had worked prior to this).

Long story short I screwed up GRUB. Because I am an amateur end user.

I still have the 10.04 live cd. Can I reinstall this to put GRUB back to the original state?

I am downloading a 9.10 live cd. Can I move my /home folder out of the partition and start afresh on the old distro?

Thankyou.

---

### Post by Ginsu543 on 2010-05-02
Are there any files on your 10.04 install that you must recover? If so, you can boot into a live session using the 10.04 live cd (using the "Try without Installing" option), and you should be able to access the hard drive partition from there.

If not, you can just to a clean reinstall. I've messed up my GRUB plenty of times. There are ways to reinstall just the GRUB, but as a newb myself, I've reinstalled the entire OS many, many times. But each time has been a learning experience, so I feel much more confident about my knowledge of computers in general and Ubuntu Linux in particular. If 10.04 won't support your graphics chip, you should do a clean install of 9.10. As you can see in my signature, I dual-boot both Lucid and Karmic. Karmic has served me very well the past 6 months, though now I'm using Lucid primarily.

One more thing... If you are going to do a fresh install, I suggest that you create two partitions on the hard drive onto which you're installing, one for the / partition and the other for the /home partition. Putting / and /home on separate partitions is handy because it allows you to install the OS (whether because you borked something or you are upgrading) without worrying about your data on the /home partition. This will also make upgrading much faster because your personal settings will all be maintained.

---

### Post by not1 on 2010-05-02
Thanks for responding kind sir.

I've been through hell and back trying to get 10.04 "*final*" working on this machine. I will feel very comfortable going back to Karmic.

Unfortunately however I have some 30 GB of data very important to me on the broken 10.04 partition in /home/music and /home/video because I have been upgrading the ubuntu distros for years now.

I NEED to retain this data. Sure I can get to it on the liveCD but how do I back it up with a CD in the drive?

I need to keep /home somehow and then install 9.10.

How?

---

### Post by not1 on 2010-05-02
Although I may infact have a workaround to my graphics problem in 10.04 if i can just get GRUB back to the state it was in at installation.

Can my liveCD fix GRUB?
Can my liveCD destroy and rebuild everything except /home?

---

### Post by Ginsu543 on 2010-05-02
To clarify, you have one partition with both / and /home on it, yes? If so, you must save your precious data somewhere else before you can repartition the drive. With 30 GB of data you're trying to save, I really recommend you take this as an opportunity to invest in a second internal hard drive or an external backup drive.

I personally have one of _[these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136540")_ as an external backup. Since it uses a usb 2.0 interface, it is easy to back up all my important data. Like you, I have over 1 TB of music and video files. I would be devastated if I lost all that. I don't know how much drives like this go for in Australia, but perhaps you can find one within your budget. Even a 500 GB drive would be quite serviceable.

---

### Post by Ginsu543 on 2010-05-02
You can fix GRUB from your live CD. Check _[this]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")_ out.
If your /home directory is not on a separate partition, reinstalling the OS using the live CD WILL destroy everything, including your /home directory.

---

### Post by not1 on 2010-05-02
yes / and /home are on the same partition.

So it is an impossibility to move a directory (ie /home) from one broken partition to a newly created one, resizing the original partition to make room for the newly created one and then doing all this without being able to boot 10.04 or using DVDs?

An external HDD is the ONLY way to get my data?

How about I use LiveCD to get to my /home directory and then move it half by half onto a 15GB usb device then to another PC?

---

### Post by not1 on 2010-05-02
> **Ginsu543 said:**
> You can fix GRUB from your live CD. Check _[this]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")_ out.


Thanks ill try this :)

---

### Post by Ginsu543 on 2010-05-02
> **not1 said:**
> 
So it is an impossibility to move a directory (ie /home) from one broken partition to a newly created one, resizing the original partition to make room for the newly created one and then doing all this without being able to boot 10.04 or using DVDs?

The problem is that you can't create a new partition on the same drive without destroying the data because the partitioning process itself rewrites the hard drive.

> **not1 said:**
> 
How about I use LiveCD to get to my /home directory and then move it half by half onto a 15GB usb device then to another PC?

Yes, this can work. You just have to get the data off your hard drive onto some other medium (preferably another hard drive). Using a 15 GB USB drive will definitely do the job (it'll just take a while). You can then copy the data back to your hard drive once you have repartitioned it and reinstalled the OS.

---

### Post by not1 on 2010-05-02
Would you know anywhere I could pick up some code to make this happen? I am an absolute newbie.

Would it involve mounting, using chroot and then gksudo nautilus? then moving it using the file manager from the HDD to my iPod?

I'm most willing to do this out of all solutions. It might be a cop-out but I don't care.

---

### Post by zaphod777 on 2010-05-02
> The problem is that you can't create a new partition on the same drive without destroying the data because the partitioning process itself rewrites the hard drive.


I am about 99% sure you can first shrink the current partition then create a new partition in the empty space without wiping the drive. However it is best to get a backup of important data first.

---

### Post by not1 on 2010-05-02
[SIZE="5"]HOLD THE PHONE[/SIZE]

I used the grub solution you linked me to, used a workaround because of my incompatible Intel graphics chipset and booted into the old partition.

Of course - there was no splash screen and it took about 6 minutes to boot.

BUT I AM NOW USING 10.04!

Maybe it would be safe to backup /home now and go back to 9.10.

Thanks for all your help!

---

### Post by Ginsu543 on 2010-05-02
@zaphod77
Actually, I do believe you are right. I didn't think of that. But like you said, one really should back up sensitive data before doing anything to the drive.

@not1
If you can get 10.04 working on your computer, then I suggest you back up /home now and do a fresh install of 10.04 (not an upgrade). If that doesn't work, you can always do a fresh install of 9.10 at that point.

---

### Post by not1 on 2010-05-02
> **Ginsu543 said:**
> @zaphod77
@not1
If you can get 10.04 working on your computer, then I suggest you back up /home now and do a fresh install of 10.04 (not an upgrade). If that doesn't work, you can always do a fresh install of 9.10 at that point.

I will back up /home, but a fresh install of 10.04 will do nothing. I have a known bug that came with the distribution regarding certain intel graphics cards like mine.

Thanks for your help!

---

