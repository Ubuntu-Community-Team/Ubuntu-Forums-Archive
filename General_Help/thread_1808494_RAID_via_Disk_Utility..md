---
title: "RAID via Disk Utility."
date: 2011-07-20
forum: General Help
---

### Post by Roasted on 2011-07-20
Has anybody ever used Disk Utility to set up software RAID? Here I am running terminal commands (I'm a terminal junkie) and I just happen to stumble across instructions that indicate "Or you can just set it up through Disk Utility."

Sure enough in disk utility, it looks like all of the configurable options are there. It makes me wonder, though... is this kind of GUI functionality something that isn't really solid? Or does it operate predictably and effectively? Just trying to get some insight on anybody who may have done this already. Thanks!

---

### Post by Cybie257 on 2011-07-20
I've used the GUI Disk Utility RAID front end a few times. I find it very reliable and functional. If you want to test it, best suggestion I can give is to create a virtual machine with a few virtual disks attached and create, monitor, etc., within a virtual environment to get the feel for it. But, if you've been using the command line version, you shouldn't have any issues figuring out the GUI.


-Cybie

---

### Post by Roasted on 2011-07-20
> **Cybie257 said:**
> I've used the GUI Disk Utility RAID front end a few times. I find it very reliable and functional. If you want to test it, best suggestion I can give is to create a virtual machine with a few virtual disks attached and create, monitor, etc., within a virtual environment to get the feel for it. But, if you've been using the command line version, you shouldn't have any issues figuring out the GUI.


-Cybie

I hear ya. The GUI looks very simple. In fact, I thought the command line way was simple with how few commands it was to set up. But hey, guess that's just more beneficial to me if I ever set up a gui-less box...

I know some GUI tools tend to be lackluster, though, which is why I wanted to ask about this one just to make sure it's not a train wreck. But the more I read, the more it sounds like it does the job well.

---

### Post by dcstar on 2011-07-21
> **Roasted said:**
> Has anybody ever used Disk Utility to set up software RAID? Here I am running terminal commands (I'm a terminal junkie) and I just happen to stumble across instructions that indicate "Or you can just set it up through Disk Utility."

Sure enough in disk utility, it looks like all of the configurable options are there. It makes me wonder, though... is this kind of GUI functionality something that isn't really solid? Or does it operate predictably and effectively? Just trying to get some insight on anybody who may have done this already. Thanks!

I recently went through the process for the first time setting up Mirror partitions on my spare machine (with 2 500GB drives) as an experiment and while it can be a bit of a learning curve, it seemed to do the job once I figured out what order to do things.

Have a read of the various HOWTOs around and it should get the job done.

---

### Post by Roasted on 2011-07-22
> **dcstar said:**
> I recently went through the process for the first time setting up Mirror partitions on my spare machine (with 2 500GB drives) as an experiment and while it can be a bit of a learning curve, it seemed to do the job once I figured out what order to do things.

Have a read of the various HOWTOs around and it should get the job done.

What process are you referring to? Doing mdadm by hand at terminal or using disk utility?

---

