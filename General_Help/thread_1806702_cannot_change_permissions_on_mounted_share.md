---
title: "cannot change permissions on mounted share"
date: 2011-07-18
forum: General Help
---

### Post by Ballzac on 2011-07-18
Hi,
I'm having a problem changing permissions on a network share. The share is mounted on my server using cifs. It has been working perfectly for a week or more. I use a bash script to copy files from a temporary folder on the server to folders on my HTPC that are mounted on my server.

The server is Ubuntu Server 10.04 and the HTPC is XBMC Live Dharma.

The problems began when I added chmod lines to my bash script to temporarily change permissions. I had the entire mounted share set to 777 on the server, and I was worried that I might accidentally delete the files or something, so I set it to 555 and then modified my script. This was not intended to be a permanent solution, but I wanted to use it as a band-aid solution until I figured out how to do it properly. The mounted folder is called "tabitha" and it is mounted in the home folder of the user "turvy" on the server. The script looks like this:


```
#!/bin/bash

#chmod -R 777 /home/turvy/tabitha/hd2/TV
#chmod -R 777 /home/turvy/tabitha/hd3/Movies

MOVDIR="/home/turvy/temp/movies"
TVDIR="/home/turvy/temp/tv"

if [ "$(ls -A $TVDIR)" ]; then
tvdetails=$(mv /home/turvy/temp/tv/* /home/turvy/tabitha/hd2/TV)
STRA="Your television shows have been moved. "

else
    STRA="No new television shows were found. "
fi

if [ "$(ls -A $MOVDIR)" ]; then
moviedetails=$(mv /home/turvy/temp/movies/* /home/turvy/tabitha/hd3/Movies)
STRB="Your movies have been moved. "
else
STRB="No new movies were found. "
fi

echo -e $STRA $STRB \n$tvdetails\n $moviedetails| mail -s "Moving files from Steve to Caitlin has Finished" my.email@address

#chmod -R 555 /home/turvy/tabitha/hd2/TV
#chmod -R 555 /home/turvy/tabitha/hd3/Movies
```

The extra lines I added are commented out here, so you can see what the change was. When I ran this new script, I got
```
chmod: cannot access `<filename>': No such file or directory
```
for every <filename> in the directories.

I commented out the chmod lines in the script so that it looked like it does above, and expected to be able to change the permissions back to how they were, but then I kept getting these errors even when running chmod from the command line.

I have no idea how running a command that I have used plenty of times in the command line can be so disasterous in a bash script. This is the second time I have screwed things up by running a bash script, and I don't get why things seem to work in the terminal, but not in a script.

Initially, the mounted shares were owned by root:root and I ran the script with sudo to copy things over. This had worked perfectly prior to me adding the chmod lines.

The relevant line in /etc/fstab is
```
//192.168.1.7/tabitha/ /home/turvy/tabitha cifs guest,_netdev  0 0
```

but I have since changed it to

```
//192.168.1.7/tabitha/ /home/turvy/tabitha cifs guest,_netdev,gid=users,dmask=777,fmask=777,rw  0 0
```

in an attempt to regain permissions. Unfortunately it doesn't work. The filesystem of the network share is ext4. I changed the owner of the share to turvy:turvy (the user on the server) in another attempt to be able to change permissions. I had to do this via the recovery mode on the live cd as I could not chown the share on my system.

I could probably change the permissions this way too, but I wan't to figure out what's causing the problem, otherwise I will just continually run into problems whenever I try to change permissions, especially if using a script.

If I run chmod recursively, I get the errors I described above. If I run it without -R, there is no error, but when I check the permissions, they have not changed.

Hopefully I've given enough information for someone to be able to help. I've googled extensively, and it generally seems that this problem is caused by a mounted FAT or NTFS filesystem, but this is ext4 over cifs. Also, in all threads I've found about the issue, it was when the person had just set it up, whereas this was working fine before I ran chmod in the script.

Thanks in advance for your help.

EDIT: I'm also happy to post the relevant parts of smb.conf on the HTPC, but because nothing was modified on the HTPC prior to this problem arising, I don't see how it could be an issue, and I wanted to avoid cluttering up this post with unnecessary information considering it's already a fairly long post.

---

### Post by Ballzac on 2011-07-18
It's weird, because I've noticed that the permissions are all set to 755, which I've never actually set via chmod, and can't find a force_create_mode or something similar set to 755 anywhere. They were originally set to 777, but somehow ended up being 755 and unchangeable after being changed to 555. Still, it's quite workable, because as the owner, 755 allows me to write, and other users on other systems still have all their permissions, so there's really no problem. Still, I'd like to know what's causing it and how I can get my ability to chmod back again if anyone has any ideas.

---

### Post by Morbius1 on 2011-07-18
> //192.168.1.7/tabitha/ /home/turvy/tabitha cifs guest,_netdev,gid=users,dmask=777,fmask=777,rw  0 0You need to bring that up to date:
> //192.168.1.7/tabitha/ /home/turvy/tabitha cifs guest,_netdev,gid=users,[COLOR=Blue]dir_mode=0777,file_mode=0777,nounix[/COLOR],rw  0 0There is no dmask / fmask it's dir_mode / file_mode and it's values have to be in 4 digits not 3.

---

### Post by Ballzac on 2011-07-18
Thanks for the help

I made the changes you suggested, and remounted, but still no luck. I'm not sure exactly what those options do, but I'm guessing they just do what I already have in my smb.conf on the HTPC:

```
[global]
workgroup = FUNKSTUDY
   netbios name = caitlin
   server string = xbmc
   log file = /var/log/samba/log.%m
   max log size = 50
   map to guest = bad user
   socket options =TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   local master = no
   force create mode = 777
   unix extensions = no

[tabitha]
path = /home/tabitha
public = yes
guest ok = yes
writable = yes
browseable = yes
force user = tabitha
read only = no
inherit permissions = yes
write list = tabitha guest

```

Actually I guess the smb.conf sets this stuff as seen on caitlin when something is added by turvy, whereas fstab on the server sets this stuff as seen by turvy on the mounted share. Either way it hasn't solved the problem.

---

### Post by Morbius1 on 2011-07-18
Actually I was narrowly focused on your cifs mount expression. Now that I read your post again I'm confused as to what you are trying to do.

You mounted on the server a remote share located at //192.168.1.7/tabitha to a mount point located at /home/turvy/tabitha on the server.

Now you are trying to move files from /home/turvy/temp to /home/turvy/tabitha ?

This has nothing to do with Samba or cifs, nothing to do with how your share is defined or how how it is mounted in fstab.

But bottom line this statement:
> I had to do this via the recovery mode on the live cd as I could not chown the share on my system.If you cannot chown or "sudo chown" a file /directory on your own system then there is a bigger issue here.

Am I missing something?

---

### Post by Ballzac on 2011-07-18
> **Morbius1 said:**
> Actually I was narrowly focused on your cifs mount expression. Now that I read But bottom line this statement:
If you cannot chown or "sudo chown" a file /directory on your own system then there is a bigger issue here.

Am I missing something?
That's not a *bigger* issue, that *is* the issue. I cannot chmod or chown any subdirectories or files on the mounted share. I'm not actually having any trouble moving files, I'd just like to have the ability to alter permissions.




> **Morbius1 said:**
> Actually I was narrowly focused on your cifs mount expression. Now that I read your post again I'm confused as to what you are trying to do.

You mounted on the server a remote share located at //192.168.1.7/tabitha to a mount point located at /home/turvy/tabitha on the server.

Now you are trying to move files from /home/turvy/temp to /home/turvy/tabitha ?

Well I can still move files, but I can't change permissions on /home/turvy/tabitha. I posted the script, because moving files is the only thing I use the mounted share for on the server. See, the HTPC is on wireless g, and it takes a while to copy stuff over, so I tend to put things on /home/turvy/temp from any one of my wired computers in the house, or the server itself, and then periodically run the script to copy stuff over to tabitha. But yeah, with the chmod lines commented out, the script works fine again (because the user turvy has write permission on /home/turvy/tabitha and its subdirectories. I just want control over my own system. i.e. I want to be able to change permissions if/when I need to, and at the moment they're locked to 755 on all subdirectories and files in /home/turvy/tabitha.

> **Morbius1 said:**
> This has nothing to do with Samba or cifs, nothing to do with how your share is defined or how how it is mounted in fstab.

Well I only have problems with this one folder, and it's the only one that has a network share mounted on it. I can chmod and chown any folder that has a local drive/partition mounted on it, so I assumed that it must have something to do with either the way it's mounted or samba.

Thanks again for your help.

---

### Post by Morbius1 on 2011-07-19
This is my latest attempt to understand how you are set up. 

* You have a SERVER that is mounting a remote share at /192.168.1.7/tabitha. It's share is defined like this:
> [tabitha]
path = /home/tabitha
public = yes
guest ok = yes
writable = yes
browseable = yes
force user = tabitha
read only = no
inherit permissions = yes
write list = tabitha guestWith a global "force create mode = 777"
And you are mounting it on the SERVER with this line in fstab:
> //192.168.1.7/tabitha/ /home/turvy/tabitha cifs guest,_netdev,gid=users,[COLOR=Black]dir_mode=0777,file_mode=0777,nounix[/COLOR],rw  0 0 * The SERVER is downloading files to /home/turvey/temp

* You are moving files from /home/turvy/temp to /home/turvey/tabitha

So, from the SERVER's perspective all files added will have owner/group = root/users and permissions of 777. Even if you could do a chmod 777 on a mounted cifs share it would have no affect since the files are already at 777.

However, from 192.168.1.7/tabitha's perspective the files have permissions that are nowhere near 777. 

My suggestion is to remove the line "inherit permissions = yes" from the "tabitha" share definition at 192.168.1.7 so that your "force create mode" can do it's thing without being overridden.

---

### Post by Ballzac on 2011-07-19
but when I 
```
ls -l
```
on tabitha, I see that everything is 777, whereas on turvy everything is 755, so it sounds the opposite way around to what you're saying.

I think the 
```
force create mode = 777
```
on tabitha's smb.conf is doing its job

and you say that chmod 777 would not do anything because they are already at 777, but as I said above, when I 
```
ls -l
```
on turvy, I see that everything is 755.

---

### Post by Morbius1 on 2011-07-19
I have reproduced your set up with a VBox machine as tabitha and my own machine as the server using the assumptions I stated above - the items marked with an "*".  With that setup I cannot reproduce your symptoms. Sorry.

From the servers perspective with that mount command in fstab it's acting just like an NTFS would mount. All files = 777, all folders = 777, and just like an NTFS partition a chmod has no affect.

---

### Post by Ballzac on 2011-07-19
Thanks heaps for the lengths you've gone to to try to figure this out for me. Given that it's not actually preventing me from doing what I need to do at this stage, it's probably not worth spending any more time on.

I'm going to continue to tweak things because I'm trying to learn more about permissions and how to set everything up, so it's concievable that I'll stumble across a solution at some stage.

Thanks again :)

---

### Post by neba on 2011-07-19
I don't know if this will help much, but I had the same problem once. The share drive I have was formatted to ext3, I reformatted to to NTFS and never had permission problems after that

---

### Post by Ballzac on 2011-07-19
Thanks for your input. That's really weird, because in most of the threads I've read about this, it turns out that the person was using FAT or NTFS, and formatting in ext fixed it.

---

