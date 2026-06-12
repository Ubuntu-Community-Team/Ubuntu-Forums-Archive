---
title: "Installing distro from one computer to another"
date: 2011-11-10
forum: General Help
---

### Post by rmcellig on 2011-11-10
I have Ubuntu Studio installed in a partition on laptop #1. What is the best way to install that distro to my other Linux laptop (laptop#2). What steps are involved?

---

### Post by Mark Phelps on 2011-11-10
I don't know about the "best" way ... but one way that might work is to use Clonezilla to image off the setup on laptop #1 to an external drive, plug that drive into laptop #2, boot from the Clonezilla CD, and "restore" that image to laptop #2.

You can get Clonezilla by going to the distrowatch.com website, downloading the ISO file, and burning that to a CD.

The reason I say "might" instead of "will" is that while Linux distros are not nearly as sensitive to hardware changes when migrating from PC to PC as MS Windows, there is no real guarantee that an install from one PC will simply startup and work on a different PC.

For example, say the first PC had an ATI card and the second an Nvidia card (for video) -- and the first PC had the ATI restricted video drivers installed.  Most likely, when you migrated that to the second PC and then booted it, you would get no display -- because the wrong video drivers are being loaded.

But, if you're using the open-source drivers, you should be able to make this migration without any problems.

---

### Post by rmcellig on 2011-11-10
I set up a new 100GB partition on my second laptop and then used Clonezilla to restore the image I created from Laptop1 partition to the new 100GB laptop 2 ext4 formatted partition. This is the error that appeared:

Failed to restore partition image file /home/partimag/2011-11-10-13-imgubuntustudio1110/sda7* to /dev/sda7! Maybe this image is corrupt or there is no /home/partimag/2011-11-10-13-imgubuntustudio1110/sda7*! If you are restoring the image of partition to different partition, check the FAQ on Clonezilla website for how to make it. Press "Enter" to continue......

---

### Post by RJarvis on 2011-11-10
A more appropriate way to transfer all your personal data to an external storage device, and then do a clean install on your new unit.

If you want to transfer all your installed packages as well, this tutorial can help you [http://www.howtoforge.com/record-installed-deb-packages-in-a-text-file-ubuntu-debian]("http://www.howtoforge.com/record-installed-deb-packages-in-a-text-file-ubuntu-debian").

Then just put your files back.

I did this when I migrated my Ubuntu distro from my piece of crap to my custom machine. Doing a clean install will help minimize any conflicts between installed drivers from one hardware setup to the other.

---

### Post by rmcellig on 2011-11-10
This is how I have my laptop so that I can put the partition from my source laptop to this my destination laptop. sda7 is the partition I created. I made an image backup of my source partition using Clonezilla and saved it on my external USB drive. At this point, I need help in how to put the backed up partition in sda7.

I made sure that sda7 is large enough to accommodate the partition from the source laptop that I backed up to my external USB drive.

If there is an app I can use GUI preferable that would make this process easy, that would be great. If not, options please. Thanks!!

---

### Post by rmcellig on 2011-11-10
Hi RJarvis,

The problem with doing a clean install is that it took me over an hour to install the fully loaded version of Ubuntu Studio 11.10. I would like to be able to put it on my other laptop without having to reinvent the wheel.

---

### Post by RJarvis on 2011-11-13
I think a Windows program I know of might be appropriate here. It's called EASEUS Partition Manager, which I always use to create partitions for my Ubuntu machines. ([[COLOR="Blue"]Here[/COLOR]]("http://www.partition-tool.com/download.htm"))

It can move partitions, but only into un-allocated space if I remember correctly. Found it very useful when making Windows/Ubuntu dual-boot machines. Let us know if that doesn't work.

---

### Post by Miljet on 2011-11-13
Let me see if I understand this right. It took over an hour to do a clean install of a fully loaded version of Ubuntu Studio 11.10. But you are willing to invest 3 days figuring out how to do it the "easy" way?

---

### Post by Rodney9 on 2011-11-13
Here is a good [Lifehacker]("http://lifehacker.com/5517688/how-to-upgrade-your-tiny-hard-drive-to-a-spacious-new-one-and-keep-your-data-intact") article and How-To on using Clonezilla and a new drive.

Rodney

---

### Post by rmcellig on 2011-11-14
> **Miljet said:**
> Let me see if I understand this right. It took over an hour to do a clean install of a fully loaded version of Ubuntu Studio 11.10. But you are willing to invest 3 days figuring out how to do it the "easy" way?

You're right. It's easier for me to just re install ubuntu studio. Why it took me so long to install was because I was following a recent article on how to do a full install of ubuntu studio including everything but the kitchen sink. The more I use Linux the more I realize how easy it is to just reinstall the os. Right now I am trying lucky backup to sync and backup my stuff.

---

