---
title: "How can I add a Raid 1 array with GPT discs"
date: 2011-10-09
forum: General Help
---

### Post by tada on 2011-10-09
Hi!

I have an HP Microserver in it there is an 8Gb USB drive - now happily running Ubuntu server 10.04.
I have recently added two WD 2Tb drives which I would like to expose to Ubuntu as a 2Tb Raid 1 mirror.
Sadly, fdisk refuses to play with the new discs - complaining of GPT.
I've had a look around the dark corners of the internet looking for a fool-proof way to add these discs as a software raid 1 but I cannot see anything :-(

Is there a straight forward way to add these discs as a Raid 1 mirror?

---

### Post by prodigy_ on 2011-10-09
> **tada said:**
> Sadly, fdisk refuses to play with the new discs - complaining of GPT.
Use **parted** instead.

---

### Post by tada on 2011-10-09
Thanks - I've seen that parted can support these bigger GPT discs but nowhere seems to add that to the software raid 1 config.

Is there a parted enabled howto or other guide to help me through the process?

I'm surprised that this is not covered anywhere - I don't think my discs are that big and adding a raid array after installation must happen to loads more people.

Something that gently leads me to a new array on my ubuntu box is what I really need :-)

---

### Post by prodigy_ on 2011-10-13
Sorry for late reply. If you still need help, try [this HOWTO](http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html).

---

### Post by tada on 2011-10-13
Sadly this howto doesn't help me :(

Firstly I'm ssh'ing into a server that has no X
I guess I could put X and a monitor/keyboard on it - I may resort to this

Secondly, my discs are GPT discs and I am unsure if they need to be handled differently to this howto.

You don't happen to have a command line how-to that covers RAID-1 using >2Tb GPT discs on an ssh connection do you?

:-)

Thanks though - its nice to be remembered.

And, yes, I know - I'm all want want want :-)

I've taken a fuller look at the howto and its only step 2 that is missing a lot of detail.
What is parted doing with those discs - how is it formatting them etc. The rest of the raid bits are probably fine.

So can anyone explain how to properly prepare two GPT >2Tb discs in anticipation of their becoming part of a raid1 mirror?

---

### Post by tada on 2011-11-01
So with overwhelming support from the community I realised it just can't be as bad as I feared.  I rolled up my sleeves and...

Remember I'm working on a remote machine - no GUIs here oh no!

# First install mdadm (and check parted is installed)
sudo apt-get install mdadm parted

# Find what discs are installed - identify the ones for use in the raid array(mirror):
sudo fdisk -l

# You'll need to recognise them somehow - mine were the only 2Tb drives and were dev/sdb and /dev/sdc

# Prepare the discs
sudo parted /dev/sdb
	mklabel gpt
	mkpart primary ext4 1 -1
	quit
sudo parted /dev/sdc
	mklabel gpt
	mkpart primary ext4 1 -1
	quit

# Make the array - this will take an age
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sd[bc]1 > mdadm.log 2>&1

# Keep up to date with the status using
sudo mdadm --detail /dev/md0
or
sudo mdadm -D /dev/md0

# When finished take a note of the uuid from the above output
# And use it to update /etc/mdadm/mdadm.conf
sudo vi /etc/mdadm/mdadm.conf 
# Add this 'ARRAY' line after the "# definitions of existing MD arrays"
	ARRAY /dev/md0 devices=/dev/sd[bc]1 uuid=ad488ee7:fb3ae633:70b10ccb:e8f856d1

# Add a file system to the raw raid drive
sudo nohup mkfs.xfs -L 2tb /dev/md0 > mkfs.xfs.log 2>&1
# Make a mount point
mkdir /mnt/2tb
# Mount it
sudo mount /dev/md0 /mnt/2tb/

# Check it is mounted by first looking in /etc/mtab
cat /etc/mtab
# Then actually cd'ing to it and running df:
cd /mnt/2tb
df -h .

# To permanently mount this you need to edit /etc/fstab
# First you need the UUID for your raid device
sudo blkid
/dev/sdb1: UUID="ad488ee7-fb3a-e633-70b1-0ccbe8f856d1" TYPE="linux_raid_member" 
/dev/sdc1: UUID="ad488ee7-fb3a-e633-70b1-0ccbe8f856d1" TYPE="linux_raid_member" 
/dev/sdd1: UUID="88cfb5bb-ad5c-4600-9d5e-e174f5e9991d" TYPE="ext2" 
/dev/sdd5: UUID="CXZ6IJ-OU2M-lGo1-ZC3L-lVID-6Xje-MIVXag" TYPE="LVM2_member" 
/dev/mapper/Server-root: UUID="e7940d5d-e3fd-4c86-a7a2-53c10e62f260" TYPE="ext4" 
/dev/mapper/Server-swap_1: UUID="c5e81f3a-b466-4418-89a6-9598a5624400" TYPE="swap" 
/dev/md0: LABEL="2tb" UUID="727844b8-7e59-482f-aa24-eb0660b0e965" TYPE="xfs" 
# Copy the UUID for your raid device - /dev/md0
# Now edit /etc/fstab:
sudo vi /etc/fstab
# Append a line like this:
UUID="727844b8-7e59-482f-aa24-eb0660b0e965" /mnt/2tb xfs defaults 0 2

# Be very careful about that last line you added - missing one column out will stall your reboot which on a headless machine (like mine) this can be a pain.

# Reboot and check it has been automounted
sudo reboot
....
cd /mnt/2tb

# Hoorah

Enjoy!

---

