---
title: "Mount a Win7 Drive NOT through Samba"
date: 2011-05-10
forum: General Help
---

### Post by UltraZone on 2011-05-10
Peeps, 

I've already set up my home network to work smoothly with Samba, mainly meaning that my HTPC running Win7 can share the user home folder.

So currently is simply have a Nautilus bookmark set to 'smb://win7server/users/username/' and it connects just fine.

Now, I want to use 'mount' to make a connection to this same folder spot such that it is seen as part of the native file system.  I've tried this:

sudo mount -t cifs //192.168.2.101/users/username/ /mnt/win7server

But I get a 'wrong fs type' warning.  WTF? I thought that windows was cifs?  You guys have any pointers to how to mount this?

BTW, I must absolutely mount this file system, as I'm running some programs built with Open Motif, which do not support Samba.

---

### Post by Morbius1 on 2011-05-10
> So currently is simply have a Nautilus bookmark set to 'smb://win7server/users/username/' and it connects just fine.

Now, I want to use 'mount' to make a connection to this same folder spot such that it is seen as part of the native file systemIt already is mounted to the native file system. It's mounted at:
```
/home/your-user-name/.gvfs/share-name at server-name
```It's in a hidden directory ( .gvfs ) so you will have to allow "show hidden files" in both Nautilus and one of your applications. Allowing "show hidden files" in one application allows it in all application. You can also create a symlink from the hidden directory to a non-hidden directory.

> I've tried this:
sudo mount -t cifs //192.168.2.101/users/username/ /mnt/win7server
But I get a 'wrong fs type' warning.My best guess is that you have a metapackage missing in your install and you should install it:
```
sudo apt-get install smbfs
```>  BTW, I must absolutely mount this file system, as I'm running some programs built with Open Motif, which do not support Samba.     Mounting it through Nautilus or by using "mount -t cifs" are both Samba so if you have an application that doesn't support Samba ( and I do not know what that means ) then neither will work.

---

### Post by UltraZone on 2011-05-13
huh, so as it turns out i did not have smbfs installed, which is weird because I had existing Samba capabilities.

At any rate, what I meant that the Open Motif doesn't support Samba, I meant that it does not allow the beginning of addresses in the "smb://" format, it can only open files in a folder seen in a traditional Unix directory.

Btw, the mount point in the .gvfs folder is just a shortcut to an "smb://" address, so it doesn't work for me.

Ok, so now that I successfully mounted it at the /mnt/Win7Server location, I need to enable read-write capability, right now it's read only.

I've typed:

sudo mount -r -t cifs //192.168.2.101/users/username /mnt/Win7Server -o username='username'

Theoretically the -r flag should enable read-write access, but it doesn't work.  Note that accessing the server through the "smb://" method is read-write enabled already, so how do I bridge the gap in the two methods?  Thanks for your input.

---

### Post by Morbius1 on 2011-05-13
> At any rate, what I meant that the Open Motif doesn't support Samba, I  meant that it does not allow the beginning of addresses in the "smb://"  format, it can only open files in a folder seen in a traditional Unix  directory.And using Nautilus doesn't create a mountpoint beginning with a "smb://". It's at :
```
/home/user-name/.gvfs/share-name on server-name
```. The only irritation is the space in the path.

>  Btw, the mount point in the .gvfs folder is just a shortcut to an "smb://" address, so it doesn't work for me.No it is not. It's is the other way around. It's how gvfs mounts the remote share and is not a link or a shortcut and there is no "smb://" in the path to the mountpoint.
> Theoretically the -r flag should enable read-write access, but it doesn't work..
It's the other way around."-r" renders the mount point read only. "-w" renders the mount point read/write. But it's read write by default so neither option is necessary. Note that making the mount writeable enables writeability it doesn't necessarily make it writeable to you.

Try changing this:
>  sudo mount -r -t cifs //192.168.2.101/users/username /mnt/Win7Server -o username='username'To this:
>  sudo mount -t cifs //192.168.2.101/users/username /mnt/Win7Server -o username='username',uid=1000

---

### Post by UltraZone on 2011-05-15
sweet! I think the uid=1000 bit did the trick, thanks man!

Since this works good on my home computer network, I think this issue is solved.  I will try this same commands on my work computer, hopefully it will work equally well.

---

### Post by UltraZone on 2011-05-16
Ok, I tried this at my work computer and it works equally good.

Now, one last configuration issue: persistence.  When I restart the computer, the mount points get dismounted.  How can I set them up such that they survive a restart?  Thanks!

---

### Post by Morbius1 on 2011-05-16
You've got two options:

[1] Stick the same mount command in rc.local on a line just above the "exit 0" line.

[2] Rearrange the line and add it to the end of /etc/fstab:
```
//192.168.2.101/users/username /mnt/Win7Server cifs username='username',uid=1000 0 0
```With the fstab method you can see if it works without a reboot by unmounting it first and then issuing the following command:
```
sudo mount -a
```THere is a timing issue here I should mention. The instructions in fstab are sometimes executed before the network is up so it will fail. If that happens I suggest you try this method to force a "redo" of fstab: [http://ubuntuforums.org/showpost.php?p=9313917&postcount=29](http://ubuntuforums.org/showpost.php?p=9313917&postcount=29)

---

### Post by UltraZone on 2011-05-16
Ok, I tried option 2, but I get "mount error(13): Permission denied".  Presumably the server is not receiving the password.  With the previous instructions, first it would ask me for the sudo password, then for the server authentication password (not the same).  I read the mount help at ss64.com and indeed you can put the flag -o password='whatever', but I would much rather not have the password written in a plain text document for obvious security issues.

BTW, while I'm doing this at my home computers, I'm also replicating this on my work computer that is SLED 11SP1, FWIW I know it's not the same, but so far it's been behaving the same.

Also, everytime I run the mount and it asks me for the authentication password, is this safely encrypted and stored somewhere? 

Also, if I want to try option one, do you know what is the equivalent location of rc.local on Suse? thanks!

---

### Post by Morbius1 on 2011-05-17
You would have to pass the password within the line in fstab or rc.local.

The password is is in plain text and is not encrypted. Most howto's on this subject have you creating a "credentials" file and restricting it's access to root but it's still in plain text and it's still not encrypted.

If you want the password to the remote share encrypted then you would have to go to the original method using gvfs:

[1] Run the following command:
```
 nautilus smb://192.168.2.101/users/username
```You will get prompted for username and password and given a chance to select "remember forever". This will place it in the keyring and that is encrypted.

[2] To automount it you have 2 options:

*** You can place the following command in your startup applications:
```
gvfs-mount smb://192.168.2.101/users/username
```*** You can use Gigolo
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

[3] And as I have said repeatedly the mount point is at:
```
/home/user-name/.gvfs/share-name on server-name
```You will have to enable "show hidden files" in Nautilus and in at least one application to see that hidden directory or you can create a symlink to a non-hidden directory.

---

### Post by btindie on 2011-05-17
Another option that wasn't mentioned is to use automount to automatically mount the share on demand. This comes from the autofs5 package.

Add an entry to /etc/auto.master:
```
/mnt/Win7Server    auto.win7server    -browse
```Then create the file /etc/win7server with the following:
```
username    -fstype=cifs,credentials=/root/.cifs.win7server,uid=1000    ://Win7Server/users/&
```Create the file /root/.cifs.win7server and put your credentials in there:
```
username=<username>
password=<password>
workgroup=<WORKGROUP>
```Set the permissions so only root can read it
```
sudo chmod 0600 /root/.cifs.win7server
```Issue the following command to restart autofs for the changes to take effect:
```
sudo service autofs restart
```Then whenever you try and access /mnt/Win7Server/username autofs will  automatically mount the share for you and also umount it if it hasn't  been accessed in a while.

---

### Post by UltraZone on 2011-05-18
Thanks guys for detailing all the options.

So far it looks like the simplest way is in fact to simply access the folder through the gvfs method, since it's not a shortcut as I originally thought.  The only minor annoyance is the naming of the mount point, but nothing I can't deal with.  Thanks!

---

