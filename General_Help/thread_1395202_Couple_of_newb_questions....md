---
title: "Couple of newb questions..."
date: 2010-01-31
forum: General Help
---

### Post by trhoresh on 2010-01-31
Ok, I'm more or less brand new to Ubuntu and I've got a couple of questions. 

System Info: I am running 9.10 and Win XP dual booted on an ASUS eee 1005HA. I have a single 160GB hard drive that I partitioned using Gparted. It now has 50GB for windows, 90GB for ubuntu, 9GB for Win PE, and a sliver for the boot boster function. 


                          1. When I first completed the dual boot, the only Ubuntu boot option was "Ubuntu, Linux **2.6.31-14**" but after an update I now have the option of the original or "Ubuntu, Linux **2.6.31-17**" (along with the Windows boot option, etc.) 
Q: How can I get rid of the original boot option? 

I prefer to just use the updated version (-17) and really don't have a use for the original version (-14). Though, I have been told it's good to keep it around.


2. Palimpsest Disk Utility shows my only hard drive, 160GB. When I boot Windows, I only see the Windows partition (C: in Windows). When I boot Ubuntu, I can see every single partition. This is not a huge problem, but I would prefer to see only the Ubuntu partition. I do not want to erase it permanently, but I want it removed from my list of filesystems in ubuntu. I sorta understand the mounted/unmounted thing, but even after I unmount the Windows partition it remains visible. Even though it's entirely under my control, I don't really like being able to edit files on the Windows partition from Ubuntu, though that could prove useful in the future.
Q: How can I hide the Windows partition? 


3. Palimpset also shows the wrong partition sizes. Windows is shown as 54GB filesystem, Ubuntu is shown as 97GB extended,  then the 9.7GB PE, and a 49MB sliver for boot booster. So, the numbers add up to my 160GB drive, but they are different sizes than what I set using Gparted.
Q: Why?



4. Under "Places" at the "Computer" section is the Windows partition. I do not want this partition accesible, especially from this location. 
Q: How can I remove this icon and replace it with the Ubuntu partition?


5. The Windows partition has the "bootable" option selected, but the Ubuntu partition does not. 
Q: How is this possible?




I apologize if this is in the wrong section. I searched for awhile last night on these topics and didn't really come up with anything. 



Thanks,


-Travis

---

### Post by espressobeanie on 2010-01-31
I can't answer it all, but for 

#1 - Administrative/Computer Janitor
IF that doesn't work, google ubuntu remove old kernels

#2 and #4 are the same
Ubuntu has the ability to see every partition. It may be because of the filesystem it uses, but you can't change it to seeing only Ubuntu partitions. Welcome to Linux.

#3 - Stick in your Ubuntu CD, hit install, and when the partition manager shows up, verify that with the partition manager. Your Palimpsest program may have an incompatibility with Linux partitions I guess.

#5 - Describe this bootable option and how it affects you. Bootable means able to boot into. So, maybe the default boot option is Ubuntu grub, and it's saying that Vista is an option to boot into.

---

### Post by t0p on 2010-01-31
The simplest way to remove old kernels from the grub menu is to use Synaptic.  Open Synaptic (**System > Administration > Synaptic Package Manager**), click on Search, and do a search for "Linux-image-2.6.31".  That will pull up all the kernels.  Delete the ones you don't want.  As they are removed, Synaptic will edit the grub list for you.

It is a very good idea to keep an old kernel just in case the latest kernel gives you problems.  Not essential, but definitely a good idea nevertheless.

---

### Post by Leppie on 2010-01-31
1. the best thing to do is to skip the 14 kernel when genrating the menu. it's the default stock kernel so it's least likely to give any issues with your system. this is why it's best to keep it.
you will have to edit your 10_linux script for this. open it with your text editor:
```
gksudo gedit /etc/grub.d/10-linux
```look for the following section and add the part in red:
```
while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

[COLOR=Red]# skip the default stock kernel
  if [ ${version} = "2.6.31-14-generic" ] ; then
    break
  fi[/COLOR]
```
save and exit, then regenerate your grub.cfg:
```
sudo update-grub
```

---

### Post by trhoresh on 2010-01-31
Ok,

1. I have to overcome my slight OCD for order and minimalism and just deal with it. Though, I have the option to delete old kernels if need be.

2. Same as #1. 

3. Still don't understand why there is a difference in partition sizes, but oh well. 

4. I can deal with having the 54GB filesystem (Windows) partition under Places, but still don't understand why my 97GB extended (Linux) partition doesn't show up. Since this is the partition that Ubuntu is installed on, wouldn't it make sense that this is the default drive to show up under places?

Edit: Here are two pictures to further illustrate my point...

In this picture, about halfway down the drop down menu, you will see "Computer" followed by "54GB filesystem." This "54GB filesystem" is my windows partition, why does it show up here and not the 94GB filesystem that is my Ubuntu partition? Clicking on "Computer" will bring me to a folder that shows: "160GB harddisk: 54GB filesystem" and "filesystem." I do fully understand the first; it is my Windows partition, but "filesystem" turns out to be my Ubuntu partition.
[IMG]http://img.photobucket.com/albums/v723/travis8798/random/P1310001.png[/IMG]

This pictures shows all of the partitions that I have mentioned previously.
[IMG]http://img.photobucket.com/albums/v723/travis8798/random/palimpsest.png[/IMG]

5. As for the bootable thing, under the disk utility you have:
Partition Label
Type
checkbox for "bootable"

The windows boot partition has bootable selected, the ubuntu partition does not. It doesn't seem to be affecting anything, I was just confused by it. 


Thank you very much for the quick and helpful replies!

-Travis

---

### Post by oldos2er on 2010-01-31
I think the boot flag is a leftover of DOS/Win days, and is only meaningful to or required by those OSes.

Ubuntu's root partition should show in Places as 'Computer'.

Maybe this thread will help with editing 'Places': [http://ubuntuforums.org/showthread.php?t=1001206](http://ubuntuforums.org/showthread.php?t=1001206)

---

### Post by towheedm on 2010-01-31
> 3. Palimpset also shows the wrong partition sizes. Windows is shown as 54GB filesystem, Ubuntu is shown as 97GB extended, then the 9.7GB PE, and a 49MB sliver for boot booster. So, the numbers add up to my 160GB drive, but they are different sizes than what I set using Gparted.
Q: Why?Palimpset shows the partition sizes in Gigabytes (GB) while GParted shows it in Gibibytes (GiB).  Since computers operate in binary, the GiB is a more accurate indication of the actual sizes.  Refer to the following link for more info: [http://en.wikipedia.org/wiki/GiB.]("http://en.wikipedia.org/wiki/GiB")

---

