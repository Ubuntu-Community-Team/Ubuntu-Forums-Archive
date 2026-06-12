---
title: "Partitioning of my fileserver is a little bit messy, advices?"
date: 2012-02-05
forum: General Help
---

### Post by Cyber1000 on 2012-02-05
Hi out there!
 
 
About me: I'm using linux for some years now (fedora, ubuntu), I'm using the cli quite often, in short terms I think I know a little bit of linux and how it works.
 
But I'm coming from windows world (actually at work I'm still with windows) and so I've partioned my linux-fileserver a little bit complicated some time ago. (at least I think so)
 
 
On my fileserver I have only 4 partitions:
/: 5,5 Gb
swap: 2 Gb
a raid partition: 500Gb
a not-raid-partion: 1000Gb
 
 
all, except "data" is on the root-partition, homedata and other data (git repos, ...) is somehow divided between the raid and the non-raid. Even in one userhome I have divided the data between non-raid and raid.
 
 
So what I mainly do:
1) created /srv/filesystem
2) created /srv/filesystem/RAID and mounted my raid here
2) created /srv/filesystem/NoRAID and mounted my non-raid here
2) created something in /srv/filesystem, for example /srv/home/users1/Music
3) bind mount a directory /srv/filesystem/NoRAID/Music on /srv/home/users1/Music
4) bind mount a directory /srv/filesystem/RAID/MyValueableData on /srv/home/users1/MyValueableData
5) rebind /srv/home on /srv/smb/home and /srv/filesystem/nfs4/home (in fstab with source-dest-rbind-0-0)
 

[LIST]
[*]So as you could imagine, I have quite a few entries in my /etc/fstab of binding and rebinding.
[*]I'm also not sure if I should divide my partitions more than this. For example on my raid reside my photos, but also my git repo. Photos are linked to my home, my git directly to /srv/git and hosted via gitolite.
[*]So normally I could make two partitions, but that said I would have to make a lot more partitions, so some time ago I decided to use one partition with directories on it and bind mounting them to other locations.
[*]And there is also the "problem" that some data resides on Raid and some on non raid.
[/LIST]
If you have gotten this far, thanks for reading, i tried to make it short, but somehow it didn't work. :-) I need just some advice, somehow I'm a little confused of my setup, what is mounted where.
 

questions:[LIST=1]
[*]Would you divide everything into single partitions or would you say a bind remount makes no difference?
[*]I have quite a lot of fstab entries, should I use symlinks instead? But I think this won't work all the time, for example if I want to link my home to my samba-folder, a symlink would be inaccessible to samba.
[*]As you see I'm bindmounting everything from raid and non-raid to my /srv dir and from there recursive bindmount to /home or wherever I need it in the system. I don't know if this is a "valid" setup. What do you say, any suggestions?
[/LIST]I know these are questions which won't have one "right" answer, but perhaps someone has a similar setup or has thought a lot of partitioning or the FHS. I hope someone may give me some good thought or share his setup.
 
Thanks,
Cyber1000

---

