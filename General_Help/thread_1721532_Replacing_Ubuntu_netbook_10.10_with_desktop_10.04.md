---
title: "Replacing Ubuntu netbook 10.10 with desktop 10.04"
date: 2011-04-04
forum: General Help
---

### Post by Gen Vert on 2011-04-04
I have netbook 10.10 installed on a *Acer Aspire One* on part of the disk and Windows 7 on another part. (There is no information worth saving in the 10.10 "home" file.)

Can I just install Ubuntu 10.04 as if I were doing it for the first time (as I did with netbook 10.10)? Will 10.04 simply replace 10.10?

---

### Post by lithopsian on 2011-04-04
Yes.  Point the installer at the 10.10 partition and it will replace it completely.  Make sure you don't have anything on there you want to keep!

---

### Post by Dupointx on 2011-04-04
I can confirm that this will work also.

---

### Post by JRV on 2011-04-04
> **Dupointx said:**
> I can confirm that this will work also.

It will not only work, it will work better.
I have 10.04 on my EeePC and I love it.

---

### Post by Gen Vert on 2011-04-06
Thanks all for the encouragement.
lithopsian said: "Point the installer at the 10.10 partition and it will replace it completely."
Sounds simple but how do you do that when you get to the disk partition choice stage of the installation? Do you have to go to "Advanced"? I looked at that but it was beyond me so finally opted for "side by side" so now I see with "Disk utility" that I have netbook 10.10 **and** 10.04 installed (besides the orginal Windows which I want to keep). 
So how can I get rid of the 10.10?

---

### Post by Dupointx on 2011-04-06
> **Gen Vert said:**
> Thanks all for the encouragement.
lithopsian said: "Point the installer at the 10.10 partition and it will replace it completely."
Sounds simple but how do you do that when you get to the disk partition choice stage of the installation? Do you have to go to "Advanced"? I looked at that but it was beyond me so finally opted for "side by side" so now I see with "Disk utility" that I have netbook 10.10 **and** 10.04 installed (besides the orginal Windows which I want to keep). 
So how can I get rid of the 10.10?

It would have been better if you didn't install side-by-side, but I think I can help you with this.

Before you try to re-install again we need to fix the partitions that you have made.

Boot the Ubuntu live-cd.

Launch Gparted (this application lets us change the partitions)
System > Administration > Gparted

You should see 3 or more partitions on the table. We are going to delete the partitions that have Ubuntu on them.

You'll see a graphical representation of your hard drive at the top. The one that is formatted NTFS is Windows 7. _***LEAVE IT ALONE***_. The other partitions should be formatted ext(#).

Right click on both partitions that are ext4 (or ext3..I don't know Ubuntu's default).
Select delete from the menu.

Now there should be a big grey area where they were. Mouse over that area and right click. Select 'create new partition'.

There will be a window that pops up. In the window there will be a drop down list of formats for the partition. Select the type as 'ext4'. Click OK.
Now you should have one single ext4 partition and 1 or more NTFS partitions for Windows 7.

Make sure everything looks good. Hit the 'apply' button (green check mark). Gparted will now apply the changes to the hard drive.

Now we need to install Ubuntu again. 
This time when it gets to the partition screen where it asks 'erase entire disk', 'side-by-side', etc... you need to select "specify partitions manually", it should be the third choice at the bottom.

Right click on the partition that is formatted ext4 in the table that appears. 
Select 'use this partition'. 
Select it's type as 'ext4' from the drop down menu.
Select the check mark box that says "format".
Where is says "mount point" select "/" from the drop down menu.

click OK or next. 
Then you should be on your way to having a dual-boot system. :)

---

### Post by Gen Vert on 2011-04-06
Thank you Dupointx for the detailed help.

Some additional points for anyone else in the same predicament as me:

-  at the "Right click on both partitions that are ext4" stage, one has to  delete the partitions starting with the highest one (/sda8 in my case)  which happened to be "Swap".

- In order to delete it, one has to  first disable it by clicking on "Swapoff" in its dropdown menu. Ditto  with the other "Swap" (/sda6). Then one can delete the partitions in  order (/sda8 down to /sda5).

- In my haste I then hit the 'apply'  button (green check mark), thereby skipping over the  'create new  partition' step, and went straight to "Install Ubuntu".

- At the  partition screen there was an extra choice "largest continuous empty  space" so I chose that and the installer did the neccessary to make it  "ext4".

So I'm in business! Thanks again.

---

