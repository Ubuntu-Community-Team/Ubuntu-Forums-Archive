---
title: "A couple of questions about backing up and restoring"
date: 2009-09-14
forum: General Help
---

### Post by Sun Confusion on 2009-09-14
Hi!

As you can tell I'm very new here. This place seems packed with great people offering great information although it can at times seem daunting to find the answer to a specific question using just the search function. So.... I needed to make this post. Sorry for the long intro.

Questions:

1. How do I determine the exact amount of hard disk space my current install is taking up on my hard-drive?

2. How do I back up my present system (which I've customized, installed apps on, and have gotten very used to) so that I can re-install it after a full format of my hard-drive or , say, install it on a brand new , larger, hard drive? 

I sure hope my last question is not impossible to answer and relatively easy to accomplish for a complete noob. Please be patient with me! :)

Thanks!

---

### Post by chessnerd on 2009-09-14
For finding out how much space your current install takes up, go to Applications>Accessories>Disk Usage Analyzer

For making a backup you should look into [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")

---

### Post by NoaHall on 2009-09-14
Well, under System -> Admin -> System Monitor there's a tab showing how much disk space is being used. This is the more friendly version.

You could use either clonezilla, or do

"sudo cp / /media/disk"

---

### Post by Sun Confusion on 2009-09-14
Thank you both for such quick replies!

I will look into both Remastersys and the clonezilla tools. Hopefully they will do what I'm aiming for. 

See, the thing is that I want to  install a completely different system on this itty bitty hard drive I have and there really is no room to fit both. So I'm forced to figure out (with all of your gracious help) how to go about doing it without having to re-install/re-configure/re-everything once I go back to ubuntu.  

Thanks again!

Oh! And if anyone else has some awesome ideas please add them to the post! :)

BTW, my system is a little over 11gb so Remastersys seems like it won't be the best option from its' descriptions????

Sorry about that last edit , seems i'm 11gb+ because of a virtual machine! I'm going to give Remastersys a try tonight!

---

### Post by buntunub on 2009-09-14
The easiest way to go about what your talking about is to have a seperate /home, and /usr partition and possibly even /var and then you can just remap those to your new Linux install, whatever that may be and your good to go with no loss of data. Its basically just a drop in place install. If your thinking to completely wipe your drive for say a Windows install and want to go back to Linux later with no data loss then yea, your best bet is to backup those partitions onto external media of some type and then just copy it back in later. Thats the "easy way" anyway.

---

### Post by ajgreeny on 2009-09-14
You can also use the terminal ```
df -h
``` to get figures for the disks mounted at that time.  A lot of virtual file systems are alos noted in the output, but it is the **/dev/sdx#** you are most interested in.

---

### Post by Sun Confusion on 2009-09-15
I have to say that Clonezilla worked perfectly. It was easy and fast and just what I was looking for!

But I have another question in response to buntunub. I've read about this partitioning scheme in the slackware book but unfortunately it doesn't go into much detail about how to go about it and how it all works. I was wondering if you or someone else has a link to a good tutorial on the process? Also, is it possible to do this AFTER a "full disk" install?

Thanks

---

