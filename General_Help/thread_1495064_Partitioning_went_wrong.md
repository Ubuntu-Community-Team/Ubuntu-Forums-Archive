---
title: "Partitioning went wrong"
date: 2010-05-27
forum: General Help
---

### Post by Achilles124 on 2010-05-27
I had to reinstall ubuntu and I formatted my harddisk with Gparted.
Then I installed Ubuntu 10.04 and it was again formatted during install.

Now it looks like this:
[http://www.flickr.com/photos/11774983@N02/4645288848/sizes/o/](http://www.flickr.com/photos/11774983@N02/4645288848/sizes/o/)

(it is a screenshot of gparted). The 120 Gig space is designated as boot. But it doesnt work as boot. It boots on the /dev/sda5 space.

In short, it's a mess. A reinstall is an option but can it also be fixed with gparted?

---

### Post by chessnerd on 2010-05-27
That doesn't look good. I believe a reinstall is the only option. 

You could try booting into a GParted Live CD and messing with the partitions there, but I'm not sure that will work and it could break things more. You can't do anything with GParted while the drive is mounted.

Maybe someone else will know a solution, but I expect you won't find one and it would probably be quicker to just reformat and reinstall...

Good luck to you. I've also had partitioning issues before and I know it isn't fun...

---

### Post by oldfred on 2010-05-27
If you convert sda1 to /home everything is just fine. Root only need 10-20GB and you have 19 if it does not include root & all your data.

The boot flag is not used by Ubuntu but some BIOS think windows and want it on a primary partition so I would leave it.

If you want to make sda1 home you will have to move home.

I used this to move /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by srs5694 on 2010-05-27
> **oldfred said:**
> If you convert sda1 to /home everything is just fine. Root only need 10-20GB and you have 19 if it does not include root & all your data.

I'll second this suggestion. You'll need to create a fresh filesystem on /dev/sda1 and then use any of a number of methods to copy /home over to it. This configuration will greatly simplify some types of future upgrades or re-installations, since you'll be able to update or replace the OS files without affecting your user data files.

---

### Post by Achilles124 on 2010-05-29
I have taken a look at the suggestions of oldfred. And it was much too difficult for me. So I reinstalled.

Thank you for answering, all of you.:)

---

