---
title: "Can't boot anymore; automount error for data partition; / is md0"
date: 2011-04-15
forum: General Help
---

### Post by streamsanddragonflies on 2011-04-15
My Lucid LTS Ubuntu Studio 64 (amd) won't boot anymore; / and /home each are software raid 0 partitions.

I have a Multimedia partition (also ext 4) which I attempted to chmod with a GUI program (I forget what its called now) to enable all users read/write access.  Looks like I inadvertantly fstabed that partition to be mounted at boot-time (normally my password was required in order to mount it).

I tried to logging out and back into my OS to see if the partition was now writable but it wasen't; instead a filesystem error was noted.  I realised then that my partition was IMPROPERLY labelled and I was in a tired state and didn't remember how to rename it & rebooted to make sure all was ok.  But it was not:

[I]An error occured when mounting /media/Ubuntu unknown filesystem type "Multimedia"
 
mountall: mount /media/Ubuntu [1334] terminated with status 32
mountall: filesystem could not be mounted /media/Ubuntu

Boot: recovering journal[/I]

From my generic Ubuntu system on a non raid partition, I finally removed the space in the 'offending' partition: Ubuntu Multimedia to UbuntuMultimedia. And I changed the permissions for it. 

But if I try to boot Ubuntu Studio via recovery;  booting in low res is unusable, and it gets stuck if I SKIP mounting. So I am left with manual boot or drop to a shell. I will have to use an editor like vi or nano and the command prompt.  I know that I likely only have to comment out a line in /etc/fstab but I am only familiar with nautilus or gedit for this type of operation. And since this OS is on a raid partition its not 'seen' on the live CD....

I would need someone to offer me clear steps to follow with the non gui editors otherwise I'm in trouble...

HELP! Anyone?

I just wanted to use that partition for video editing and now I am locked out of my system!

---

### Post by streamsanddragonflies on 2011-04-15
ok I somehow figured out how to find my fstab contents in the command line and to comment out the partition using nano after all!

cat /etc/fstab

sudo nano /etc/fstab


now I found out that my /home partition is a total mess!

[I]there is a problem with the configuration server:

/usr/lib/libg conf2-4/gconf-sanity-check-2 exited with status 256
/home/user/Desktop
/home/user/.nautilus 
[/I]
need to be recreated or was it chown? now I am too tired to reboot and review again...

also I think that my boot drive has low disk space or none left: (100mb) grub 2- ext3

another message I got is:* Could not update ICEauthority file /home/user/.ICEauthority*

but I couldn't fix it in shell cause it didn't seem to recognise my username...?!  this is what I tried:

[I]chown user:user /home/user/.ICEauthority
chmod 644 /home/user/.ICEauthority
exit
[/I]

So once again stumped!

---

### Post by streamsanddragonflies on 2011-04-15
Bump!
Anyone?

I don't know if I should start a new thread since I solved my first problem...I only realised that my /home partition has its permissions messed up afterwards.  Either I corrupted my /home during partial upgrade of pkgs which had failed: the latest linux pre-empt kernel couldn't install. Or is /home partition supposed to be in fstab? because it is not there now...

---

### Post by streamsanddragonflies on 2011-04-16
ok I'm starting a new thread because I solved the first issue of # out an entry in fstab using nano and ^X (exit) I beleive and chosing to save on exit.  But now I beleive that I actually had run a partial upgrade that failed and now my /home/user seems to have been wiped!

---

