---
title: "Ubuntu first timer"
date: 2010-09-20
forum: General Help
---

### Post by Fredundant on 2010-09-20
I have 2 HDD's on my Windows 7 machine (drives c and d)
 
On drive D i created a 25 gig partition for ubuntu. Im on my laptop at the moment, On my desktop Im running ubuntu from the USB. I'm trying to install ubuntu into the 25 GB partition. It tells me it is unusable. (ts not formatted in wondows - it told me if i formatted it, i would not be able to have an OS on that partition).
 
Im recieving the error:
 
"No root system is defined.
Please correct this from the partitioning menu"
 
In very simple terms, how do i get ubuntu to install on the partition.
 
Thanks in advance

---

### Post by finny388 on 2010-09-20
You will need two partitions to install linux.

one for root (OS, program, files)
and one for swap

Create a second partition of say 2GB using space from your 25GB partition.

there is a dropdown for each partition during installation to choose root, swap or others.

choose "/" (this is root) for the 23GB partition

and 

"swap" for the 2GB partition

hope that helps

---

### Post by zealibib slaughter on 2010-09-20
Are you doing a manual partition? If so then when you specify the partition for ubuntu in the partition editor dialogue then you should see a drop down menu for mount points. In the drop down menu for mount points select the one with a forward slash (/).  That will be where your root partition installs at.  You also need another partition for the swap file so divide your partition up first with one section for boot and the other can be small ( around 512 mb to 1 gb ). the small one specify for linux swap under use as. see [http://www.techhamlet.com/2010/05/how-to-install-ubuntu-10-04/](http://www.techhamlet.com/2010/05/how-to-install-ubuntu-10-04/) for some good screen shots.

---

### Post by Fredundant on 2010-09-20
Thanks guys for your help. 
I will create the second partition, but I'm not seeing what you say I should be.
 
In the install menu Ive chose time, and keyboard layout. now in on step 4 of 7.
 
Prepare disk space
 
This computer has several operating systems on it
 
then shows me in colours what is where and how much etc with the 25GB at the end.
 
Then...
 
Where do you want ubuntu 10.04.1 LTS?
 
(Check box) rease entire disk
 
(check box) specify partitions manually (advanced)
 
 
I secify partitions manually then Im in step 5
 
There is a table that looks like this....
 
Device  |  Type| Mount point | Size | Used
 
Mount point ins empty
 
Down device is... dev/sda dev/sda1 dev/sda2 dev/sda3 dev/sda4 amd unusable
 
type is blank for first one (dev/sad) then ntfs for 1-4 and blank for unusable
 
there is also a check box in each dev/sad1-4
 
I'll create the partion now, but I cant see how that will help
 
 
I would appreciate more guidence.

---

### Post by zealibib slaughter on 2010-09-20
Mount point should have a drop down menu associated with it see screen shot below click the arrow button and choose /. This will be at the create partition dialogue in step 5

[http://ubuntuforums.org/album.php?albumid=2023&pictureid=6754](http://ubuntuforums.org/album.php?albumid=2023&pictureid=6754)[IMG]http://ubuntuforums.org/album.php?albumid=2023&pictureid=6754[/IMG]

---

