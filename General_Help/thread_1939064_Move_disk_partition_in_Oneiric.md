---
title: "Move disk partition in Oneiric"
date: 2012-03-10
forum: General Help
---

### Post by Ralph L on 2012-03-10
I am trying to install Oneiric.  I clicked Install on the desktop.  It allowed me to shrink some disk partitions to make room for an Oneiric partition.  However, the space is scattered is pieces between partitions.  I need to move these partitions to gather all the free space together.  How do I do that?  It is rather useless to have an install procedure that allows repartitioning the disk, but doesn't allow the paritions to be moved.  Under Lucid I used gparted to move partitions.

---

### Post by dcstar on 2012-03-10
> **Ralph L said:**
> I am trying to install Oneiric.  I clicked Install on the desktop.  It allowed me to shrink some disk partitions to make room for an Oneiric partition.  However, the space is scattered is pieces between partitions.  I need to move these partitions to gather all the free space together.  How do I do that?  It is rather useless to have an install procedure that allows repartitioning the disk, but doesn't allow the paritions to be moved.  Under Lucid I used gparted to move partitions.

Boot into run mode and use gparted, then install.

---

### Post by Ralph L on 2012-03-11
Is gparted installed on the Oneiric CD or do I have to get the Internet to work when running on the CD.  This is a problem for me.  I looked for gparted on the Oneiric CD, but couldn't find it.  Maybe that is because I don't know how to use Unity.  Any help appreciated.

Ralph

---

### Post by grahammechanical on 2012-03-11
1) Load the Oneiric live CD. I have just run this test to find how do what you want without using my memory.

2) At the desktop click the Ubuntu icon on the top of the Launcher running down the left side of the screen. Or, press the super key (the key in between Ctrl and Alt}

3) The Dash will open. Type gparted and either click the icon for Gparted Partion Manager or press Enter. Gparted will load.

4) Select the partition you wish to move. Go to the Partition menu in the application's top panel. Select Resize/Move.

5) A Dialogue box will appear with a representation of the partition. Place the mouse pointer in the centre of partition and the pointer will change to a fist. Left click and move the partition to the left or right.

6) Click the Resize/Move button and this operation will be placed in the bottom panel as a pending operation. Repeat for the other partitions until you have a list of pending operations. Or,

7) Go to the Edit menu and select Apply All Operations. Then repeat to move other partitions.

Wait for operations to be completed. And do not cancel.

Regards.

---

### Post by Ralph L on 2012-03-13
Thank you very much for your help.  I found gparted and it moved my partitions as necessary.  Guess I just don't know how to use Unity.

---

