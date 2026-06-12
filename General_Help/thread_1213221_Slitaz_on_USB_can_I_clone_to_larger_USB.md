---
title: "Slitaz on USB can I clone to larger USB"
date: 2009-07-14
forum: General Help
---

### Post by lindsay7 on 2009-07-14
I am running Ubuntu 9.04 and I also have the Slitaz OS on a 2 gig USB. I would like to move this over to an 8 gig USB.

My question is, how can I do this?

---

### Post by schmidtbag on 2009-07-14
Slitaz is so small, why don't you just reinstall it to the new flash drive, or, why would you even want it on a larger flash drive?  But, this is a fairly long process, you can look up how to migrate hard drives online with Linux but its a tedious process.  In Windows, I forget the name of the program but the company name is Paragon and it is a hard drive related program.  Its very professional yet easy and does work with Linux filesystems (you do have to pay for it)

---

### Post by lindsay7 on 2009-07-14
One of the cool things about Slitaz on a USB is that you have the option to same your root file whenever you exit with any changes that you have made to the system. So, apps, pictures, music, etc, and my dropbox files can be saved. That is why I want the extra space.  I have Acronis but it does not want to work with the usb drive only hard drives. It would be a lot easier to clone it then going back and re-doing the apps that I have on it.

---

### Post by schmidtbag on 2009-07-14
well like i said, there are tutorials on hard drive migration online.  i'm not sure if slitaz uses the UUID (i would think it wouldn't) so its very possible you could just make the larger flash drive flagged as bootable in gparted and just copy everything to it.

another thing you can do is keep the flash drive you have now, and mount the larger one.  then, your music, pictures, dropbox, etc will be linked to the larger drive.  this is incredibly easier than copying everything and you actually get more space out of this

---

### Post by lindsay7 on 2009-07-14
Good Idea, thanks for the help.

---

### Post by snowpine on 2009-07-15
SliTaz has its own very cool USB utility called tazusb. I'm sure you could use that to set up the new USB stick with your old rootfs.gz.

---

### Post by lindsay7 on 2009-07-15
Thanks Snowpine, I did set up a new 4gig usb stick with tazusb but it did not automatically carry over my rootfsgz file. I did not think of doing that at the time so I just set it up again.  The first go at the original usb had a problem getting Dropbox setup and I ended up setting it up from source code.  But on the 4gig set up I just installed it from the repos and it worked like magic.

I love this distro, easy, has everything, and the save rootfs function (auto on exit if you choose), is great. Setting up the usb system is fast and leaving the password and username to the defaulf make it easy to work.

---

