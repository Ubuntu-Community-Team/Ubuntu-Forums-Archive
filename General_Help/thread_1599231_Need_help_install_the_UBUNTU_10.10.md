---
title: "Need help install the UBUNTU 10.10"
date: 2010-10-17
forum: General Help
---

### Post by dineshchaturvedi on 2010-10-17
Hi,
    I am new to UBUNTU 10.10 mostly being a windows user with some experience (basic navigation and executing scripts) on Linux. I have started liking Linux and feel UBUNTU can be the perfect thing to have, also my friends are crazy about UBUNTU so thought it will be good.

I have to make it dual boot since my wife and kids needs windows and we just have 1 laptop.

I have created the UBUNTU CD and Widows recovery CD.
When I try to install UBUNTU, I am getting stuck with choosing the partition. 

I see the following there
/dev/sda1 8 GB appox
/dev/sda2 53 GB approx
/dev/sda3 107 GB approx
/dev/sda5 80 GB approx

Too me it seems like all partition are looking little bigger then what they look in windows.

Here is what I have on Windows

C Drive 50 GB
H Drive 100 GB
U drive 75 GB (I created this for just UBUNTU).

Now I think the sda5 might be U drive but I am not sure.

Also I need to created root,space and home partition as I read.

Can someone help me get started with UBUNTU, I will really appreciate you guys.

I know the real programmers are on Linux.:)

---

### Post by hal8000 on 2010-10-17
> **dineshchaturvedi said:**
> Hi,
    I am new to UBUNTU 10.10 mostly being a windows user with some experience (basic navigation and executing scripts) on Linux. I have started liking Linux and feel UBUNTU can be the perfect thing to have, also my friends are crazy about UBUNTU so thought it will be good.

I have to make it dual boot since my wife and kids needs windows and we just have 1 laptop.

I have created the UBUNTU CD and Widows recovery CD.
When I try to install UBUNTU, I am getting stuck with choosing the partition. 

I see the following there
/dev/sda1 8 GB appox
/dev/sda2 53 GB approx
/dev/sda3 107 GB approx
/dev/sda5 80 GB approx

Too me it seems like all partition are looking little bigger then what they look in windows.

Here is what I have on Windows

C Drive 50 GB
H Drive 100 GB
U drive 75 GB (I created this for just UBUNTU).

Now I think the sda5 might be U drive but I am not sure.

Also I need to created root,space and home partition as I read.

Can someone help me get started with UBUNTU, I will really appreciate you guys.

I know the real programmers are on Linux.:)


Drive letters in windows are just that- a drive letter. They tell you nothing about the partition or where it is.
Luckily you have posted the how linux shows your drive and this says much more about your drive than windows.

/dev/sda1 8G is a hidden (in windows) recovery partition, your C drive is primary partition 2 and your other windows partition is also primary. You can swap drive letters around in windows which is why they are meaningless.

You created a single 80G logical drive for Ubuntu, this is ok, but you now need to split this into root (/)   home  (/home) and swap /(swap)

To do this use the Ubuntu install CD and at the point of partitioning, choose manual partitioning.

Yo are now going to delete /dev/sda5 and then re-create it.
After choosing delete, there will free space.
Click in the free space then create new partition.
Choose filesystem ext4. mount point / and size 20G
Now create another partition, filesystem type swap and set its
size to 2G.
Finally create a new partition type ext4 mount point /home and use 
remaining space for it

This creates new partitions:
/dev/sda5  ext4 /
/dev/sda6 swap
/dev/sda7  /home

This is a start for you and you can install Ubuntu. You
may get some more suggestions regarding filesystem types
to use and partition sizes but these suggested scheme gets you to
a working system
Hope that helps

---

### Post by psycho5 on 2010-10-17
You should put in the ubuntu live cd, go to the live desktop, and then open up Places

you should see all the disks over there as you partitioned them, check the 80GB one by opening it, if it is indeed the one you created for Ubuntu, then you're good to go.

Just double click install system icon on the desktop.

During installation, at disk setup, just click Manual allocation.

select the 80GB partition, and set it as / and format it as ext4. 

during installation, if it asks where to install grub, then install it at /dev/sda on the MBR. Normally, it should not ask you since you only have one disk and it will be done automatically. 

Good Luck. 

You can take a look at the community documentation also

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by dineshchaturvedi on 2010-10-22
I got all setup with UBUNTU and now I am finding new software, it is very good operating system I must say this. I am learning the software, I do not know how apt-get gets the software.

---

### Post by Quackers on 2010-10-22
It gets software from the repositories in your Software Sources list.

---

