---
title: "Automatically mount multiple cd iso images on boot"
date: 2012-04-29
forum: General Help
---

### Post by Cuddy Stone Fist on 2012-04-29
Hello I'm a user with limited linux skills and my cli and script fu is to put it simply absymal.  

But I do have a problem or should I say a specific way I want to use ubuntu, and dont know how.

I have on many many cd's all sorts of data, photos, 3dmodels, etc...  To keep my originals in prime condition and scratch free over the years I've taken to making iso files and mounting those in windows.  Now even using those isos is becoming a tedious task to find the correct iso and mount it.  So what I want to do and have begun the process for is:

run Ubuntu in VirtualBOX (check)
share my main iso repository on network (check)
access said share on my windows pc with my virtuaBuntu installation (check)
mount isos in Ubuntu (check only one at a time though)

  So I'm some way along the path already. Now I need to be able to share a root mount point on the ubuntu machine that I can access with my windows machine.  Under that root point all other isos will eventually be available.

So lets say I have a folder named lets say *data* this would be the common mounting point.  Under it would be folders like *photos, 3dmodels, 3dscenes, textures, etc...*. and under each, folders based on specific iso name automatically generated (hopefully).

So instead of mounting photo200712b.iso in my virtual cdrom, I'd go to x:\data\photos\Photos_2007_dec\ and find the same data I'd find on the iso.

I have the isos roughly arranged this way on my windows pc but I see no way to be able to solve this problem through windows.  The share I have enabled and works is in the root of my iso data tree.

Now what I need is a script that mounts them somehow automatically on boot.  Or a script that can run through the shared folder and generate data for fstab.  Like go into photos folder run script it finds all .iso files and generates the info for a fstab file and creates proper folders on the linux side.  Or something along those lines.  And then make those folders available by sharing the mounting root with windows again.

I have done a lot of googling and I can nowhere find limits to how many mounts linux systems can have and since they'd be mounted in folder and not drive letters it would be much easier to work with them. And potentially pretty futureproof as my cd collection expands, close to 50 cds to work with now.

So if anyone has info or can somehow help me make this possible I'd be very grateful.

Best regards
Cuddy

---

### Post by Cuddy Stone Fist on 2012-05-01
Ok it seems like nobody has a solution for doing this automatically.  I tried adding to fstab manually but on boot it says that the files are not available.  I'm guessing that has to do with the ethernet connection not being available when fstab in run on boot.  When I try running "sudo mount -a" after boot it runs out of loop devices since they seem to be limited to 8.

I found a post that shows how to change number of available loop devices. [max loop]("http://http://www.howtoforge.com/forums/showthread.php?t=21303")

In that post it says:

[I]Add this to /etc/modules:
Code:

loop max_loop=64

Then reboot the system. [/I]

This works.  Using mknod I can create a new loop device but it disappears on reboot. So I created a simple script to run manually after boot. And that is my problem it's not working.  (not surprising since I've never really learned any scripting)  That script is as follows:

[I]for (( i = 8 ; i <= 150; i++))
do 
	mknod -m660 /dev/loop$i b 7 8
done
exit 0[/I]

That doesnt work because it demands root access.  And I cant figure out how to run the script as root. So I am stuck I can add the directories to mount the iso files in manually (although that will be a major pain)  But then I need a script to mount them and there I will run into the same problem as adding the loop devices. Anyone have some ideas how to proceed?

---

