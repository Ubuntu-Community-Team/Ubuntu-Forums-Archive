---
title: "cp files to a network shared folder"
date: 2010-12-06
forum: General Help
---

### Post by Clive McCarthy on 2010-12-06
I'm attempting to write a simple BASH shell script to copy some files from one of my Ubuntu machines to another Ubuntu machine's shared folder. I've searched the forums but I haven't found anything on simply using **cp** across a network.

Since Nautilus can do it I presume I should be able to do it from the terminal or from a BASH script -- this might be my first mistake?
I have tried the obvious: 

**cp**   My_local_file     //Name_of_other_ubuntu_computer/shareddocs
and
**cp**   My_local_file     smb://Name_of_other_ubuntu_computer/shareddocs

but those don't work. Sharing is enabled for the shareddocs folder.
I have tried mounting the remote shareddocs folder but it seems I need to install some other package to do this? If this is true, how does Nautilus manage to do it without an additional package?

This seems like a really basic question. Sorry...

---

### Post by argedion on 2010-12-06
to copy files over a network use

rsync it is most recommended at command prompt type man rsync > rsyncmanual and read all about how to use this wonderful tool

---

### Post by Clive McCarthy on 2010-12-06
Thank you for your quick response. I can see that things are about to get messy.

I was hoping for a simple trick because I also want to be able to create directories on the remote shared folder. It seems that **cp** **mkdir**** rm **etc. etc. won't be the way. I have half-a-dozen Ubuntu machines and I want to be able to 'distribute' files to any one of them and manage these files from a *master* Ubuntu machine. These *slave* machines are all mine but I want to do the least amount of configuring of these machines.

Any other approaches?

I've just read that NFS is the normal way for Xnix-to-Xnix sharing and that Samba is used for Windows to Ubuntu sharing. I have a mix of XP and Ubuntu systems (it's a slooow migration) so maybe I should use SMB throughout? Does SMB work for Ubuntu-to-Ubuntu transfers? Can I gain full r/w control of things in the shared folders? Can I do a SMB mount of a shared folder on another Ubuntu machine and get on with life? Tell me how, please.

Lastly, why does this forum think that Ubuntu is a spelling mistake?

---

### Post by sgosnell on 2010-12-06
Samba is the way to go if you want to be able to change directory structures on other machines, I think.  Just make sure the shared folders have the proper permissions.

---

### Post by Clive McCarthy on 2010-12-07
Yep, I can now see that SMB is the way to go but for some reason I can't get it to work. I run:

[INDENT][COLOR="Blue"]mkdir target_mount
sudo mount -t cifs //artshow16/shareddocs /target_mount -o rw,nocase,workgroup=WORKGROUP,username=clive,password=xxxxxx[/COLOR]
[/INDENT]
but get:

[INDENT][COLOR="Red"]mount error: could not resolve address for artshow16: No address associated with hostname
No ip address specified and hostname not found[/COLOR]
[/INDENT]
What's up? The artshow16 machine is visible on the network and it's shareddocs directory is present.

All the examples on the web look _just_ like mine :rolleyes:

Clearly it can't figure out the hostname but how do I give it a clue? Don't say the IP address because those will be all over the place since the DHCP server will do what it wants and I don't want to hard-wire the IP adresses of a bunch of machines...

Clearly Nautilus can figure it out... I've changed a /etc/nsswitch.conf entry to read
[COLOR="SeaGreen"]hosts: files wins dns[/COLOR]
and
ran [COLOR="SeaGreen"]sudo apt-get install windind[/COLOR]
and this now allows me to ping by UNC computer name, so things are getting closer.

If I install resolveip and run [COLOR="Blue"]resolveip -s[/COLOR] I can get the ip address of a machine and then I can assign it to a variable and use it in the mount command in my BASH file. Boy this is hard work.

I'm still having hideous problems. I found that mount needs the IP address of the machine that has the shared folder and I found, through a VERY long trail, that I can get it from resolveip (have to install my_sql) and have it sent to mount. The permissions of the mount target directory have to be set too otherwise it fails. From sundry posts it is clear that mount and mount cfis and all of this smb sharing is a mess. So many people have failed to mkdir the mount point before trying the mount and even if you do it then needs the permissions set.

I managed to ping my target machine after editing /etc/nsswitch.conf to enable wins dns and then install winbind... it just goes on.

Still mount couldn't resolve the hostname to an IP address. How the hell does nautilus accomplish all of this?

My target test machine is now in trouble because the shareddocs folder has become unshared and I get a failed to execute child process "testparm" error message...

I'm digging a deeper hole. Help!!

---

