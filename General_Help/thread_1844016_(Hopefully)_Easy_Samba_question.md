---
title: "(Hopefully) Easy Samba question"
date: 2011-09-14
forum: General Help
---

### Post by aeathb on 2011-09-14
If this is in the wrong sub-form I apologize in advance. I am trying to set up file sharing between 2 Ubuntu commuters. I used [http://ubuntuforums.org/showthread.php?t=1502265&highlight=HOWTO%3A+Easy%2C+simple+GUI](http://ubuntuforums.org/showthread.php?t=1502265&highlight=HOWTO%3A+Easy%2C+simple+GUI) which was awesome, but now Im getting an error that "failed to mount windows share." (See screenshot below). Maybe I am doing something really dumb, but I thought because its visible and everything is showing up I'm not sure why its not working......

---

### Post by Morbius1 on 2011-09-14
A "failed to mount Windows share" is usually a Linux permissions problem. Post the output of the following command please from the Ubuntu machine with the share:
```
testparm -s 
```

---

### Post by aeathb on 2011-09-14
> **Morbius1 said:**
> A "failed to mount Windows share" is usually a Linux permissions problem. Post the output of the following command please from the Ubuntu machine with the share:
```
testparm -s 
```
Hopefully this will help?

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[3 Doors Down]"
Processing section "[Pictures]"
Processing section "[Documents]"
Processing section "[Music]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = FILESOLD
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[3 Doors Down]
    path = /home/aeathb/Music/3 Doors Down
    read only = No
    guest ok = Yes

[Pictures]
    path = /home/aeathb/Pictures
    read only = No
    guest ok = Yes

[Documents]
    path = /home/aeathb/Documents
    read only = No
    guest ok = Yes

[Music]
    path = /home/aeathb/Music
    read only = No
    guest ok = Yes

---

### Post by Morbius1 on 2011-09-14
And what are the permissions on the Music directory:
```
ls -dl /home/aeathb/Music
```

---

### Post by aeathb on 2011-09-14
> **Morbius1 said:**
> And what are the permissions on the Music directory:
```
ls -dl /home/aeathb/Music
```
When I input that command all I get is "aeathb@Austin-Ubuntu:~$ aeathb@Austin-Ubuntu:~$ ls -dl /home/aeathb/Music
aeathb@Austin-Ubuntu:~$: command not found
aeathb@Austin-Ubuntu:~$ drwxrwxrwx 107 aeathb aeathb 20480 2011-08-22 15:41 /home/aeathb/Music
drwxrwxrwx: command not found"

---

### Post by Morbius1 on 2011-09-14
I read the HowTo you are following. Please post the output of this command as well please:
```
net usershare info --long
```

---

### Post by aeathb on 2011-09-14
> **Morbius1 said:**
> I read the HowTo you are following. Please post the output of this command as well please:
```
net usershare info --long
```
aeathb@Austin-Ubuntu:~$ net usershare info --long
[music]
path=/home/aeathb/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

And I would like to thank you for all the time you are taking to help. I sincerely appreciate it.

---

### Post by Morbius1 on 2011-09-14
That HowTo is using 2 completely different methods of sharing folders. 

This is a Classic Samba share:
> [Music]
    path = /home/aeathb/Music
    read only = No
    guest ok = Yes     This is a Samba Usershare:
> [music]
path=/home/aeathb/Music
comment=
usershare_acl=Everyone:F,
guest_ok=yUsing both methods on the same target is not recommended although in this case they are at least in sync. What I would do is go back into Nautilus and undo the share at /home/aeathb/Music then just to make sure the permissions are correct:
```
chmod 0777 /home/aeathb/Music
```

[COLOR=Blue]**EDIT**[/COLOR]: If you run "net usershare info --long" again it should come back blank.

Then try to access the share from the client.

---

### Post by aeathb on 2011-09-14
Sorry for the REALLY basic question, but Nautilus is the "windows explorer" of ubuntu correct? And do you mean to go to the folder I want shared, click on sharing options and configuring it that way? also, what exactally was 
chmod 0777 /home/aeathb/Music

EDIT: I figured out what you meant by why to type in chmod 0777 /home/aeathb/Music

---

### Post by aeathb on 2011-09-14
And yes, they cam back blank; however, I am still getting the same error....

---

### Post by Morbius1 on 2011-09-14
Nautilus is the file browser, yes. So if you do the following in a terminal:
```
nautilus /home/aeathb
```It should bring you to your home directory. Then just right click the Music folder > Sharing Options and uncheck all the boxes.

```
chmod 0777 /home/aeathb/Music     
```This will make /home/aeathb/Music have rwx permissions for everyone so that it's consistent with how your Classic Samba share is set up.

---

### Post by Morbius1 on 2011-09-14
Posted past each other I see. 

Let's try something more fundamental. From whatever machine you are on post the output of the following command:
```
smbtree
```

Also, what version of Ubuntu are you using?

---

### Post by aeathb on 2011-09-14
11.04 Natty on both machines. I put in smbtree and got
"WORKGROUP
    \\AUSTIN-UBUNTU          Austin-Ubuntu server (Samba, Ubuntu)
        \\AUSTIN-UBUNTU\IPC$               IPC Service (Austin-Ubuntu server (Samba, Ubuntu))
        \\AUSTIN-UBUNTU\Music              
        \\AUSTIN-UBUNTU\Documents          
        \\AUSTIN-UBUNTU\3 Doors Down       
        \\AUSTIN-UBUNTU\Pictures           
    \\AUSTIN-PC              
cli_start_connection: failed to connect to AUSTIN-PC<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME"

The fail is bad I think!

---

### Post by Morbius1 on 2011-09-14
Edit smb.conf as root on both machines:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section right under the "workgroup" line:
```
name resolve order = bcast host lmhosts wins
```Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down ( restarting samba throws the network into chaos for a few minutes ). Then run smbtree again and see if there are any errors.

---

### Post by aeathb on 2011-09-14
WORKGROUP
    \\AUSTIN-UBUNTU          Austin-Ubuntu server (Samba, Ubuntu)
        \\AUSTIN-UBUNTU\IPC$               IPC Service (Austin-Ubuntu server (Samba, Ubuntu))
        \\AUSTIN-UBUNTU\Music              
        \\AUSTIN-UBUNTU\Documents          
        \\AUSTIN-UBUNTU\Pictures           
        \\AUSTIN-UBUNTU\3 Doors Down       
FILES
cli_start_connection: failed to connect to 192.168.1.110<20> (192.168.1.110). Error NT_STATUS_CONNECTION_REFUSED
cli_start_connection: failed to connect to UBUNTU<20> (192.168.1.110). Error NT_STATUS_CONNECTION_REFUSED

---

### Post by Morbius1 on 2011-09-14
Did you enable the firewalls on these machines. If so disable it:
```
sudo ufw disable
```

If you are using something other than the built in firewall utility let me know.

What version of Ubuntu are you using?

---

### Post by aeathb on 2011-09-14
No other firewalls. 11.04

---

### Post by Morbius1 on 2011-09-14
I can reproduce your error instantly by disabling smbd:
> cli_start_connection: failed to connect to 192.168.0.100<20> (192.168.0.100). Error NT_STATUS_CONNECTION_REFUSED
cli_start_connection: failed to connect to MORBIUS<20> (192.168.0.100). Error NT_STATUS_CONNECTION_REFUSED
Go to whatever 192.168.1.110 is and start smbd:
```
sudo service smbd start
```Just a hunch but what is the ip address of AUSTIN-UBUNTU ?

---

### Post by aeathb on 2011-09-14
Austin Ubuntu is the 192.168.1.100 address which is the server. I can't find a 192.168.1.110 address. When I put the command into the server, I received a "start: Job is already running: smbd"

EDIT: The client was 192.168.1.110. But its still failing to mount....

---

### Post by Morbius1 on 2011-09-14
Is AUSTIN-PC the client?

What is it's ip address?

---

### Post by aeathb on 2011-09-14
Austin Ubuntu is at 1.100 and is the server. The client is at 1.110

---

### Post by Morbius1 on 2011-09-14
Let's bypass browsing. In fact let's bypass nautilus. From the client access the server share directly:
```
gvfs-mount smb://192.168.1.100/music
```What should happen on the client is a mount icon will be placed on the desktop. Double click that to open Nautilus to that location.

Same errors?

---

### Post by aeathb on 2011-09-14
austin@ubuntu:~$ gvfs-mount smb: //192.168.1.100/music
Error mounting location: volume doesn't implement mount
Error mounting location: Location is already mounted

---

### Post by Morbius1 on 2011-09-14
Install the following package:
```
sudo apt-get install cifs-utils
```Then mount it old school:
```
sudo mount.cifs //192.168.1.100/music /mnt -o guest
```Does the thing at least mount to /mnt?

BTW, if a miracle happens at it does actually mount, to unmount it:
```
sudo umount /mnt
```

---

### Post by aeathb on 2011-09-14
Do I mount this from the client or server?

---

### Post by Morbius1 on 2011-09-14
Client

And the package has to be installed on the client

---

### Post by aeathb on 2011-09-14
From the Client:
austin@ubuntu:~$ sudo mount.cifs //192.168.1.100/music /mnt -o guest
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

---

### Post by Morbius1 on 2011-09-14
can the client even ping the server:
```
ping 192.168.1.100
```

---

### Post by aeathb on 2011-09-14
Its Pinging fine. If I ran a port scan to find the open ports would it be of any assistance?...Although I can see the files so the smbd port is good right?

---

### Post by Morbius1 on 2011-09-14
> Although I can see the files so the smbd port is good right?What do you mean you can see the files? You mean the folders or do you mean you now have access to the share?

[COLOR=Blue]**EDIT**: Did you by any chance encrypt your home folder when you installed?[/COLOR]

---

### Post by aeathb on 2011-09-14
just the folders sorry....How would i check if encrypted? I think it might be....

---

### Post by Morbius1 on 2011-09-14
That would explain many things.

How do you check? I have no idea. Had to look it up: [http://ubuntuforums.org/showthread.php?t=1598738](http://ubuntuforums.org/showthread.php?t=1598738)
```
 mount | grep ecryptfs
```
If it comes back to the prompt then it's not.

I have no idea what to do with a samba share pointing to an encrypted directory. Some random thoughts:

* Since all your shares are guest shares you could add an option to your smb.conf file that will convert all remote users to you - at least as far as those shares are concerned:
```
force user = aeathb
```Add that to your growing list of samba additions in the [globa] section of your server and then restart smbd. 

* Create shares outside of the home directory.

Make a directory at say ... /mnt/Shared:
```
sudo mkdir /mnt/Shared
```Then create subdirectories for Music, etc... and share those.

Unfortunately, I have to shut down for the day, Sorry. I'll pick it up tomorrow.

---

### Post by aeathb on 2011-09-14
First off, you shouldn't apologize for having to shut down! You are SO kind for helping me trough this point. 
When I ran the first command I got back,
/home/aeathb/.Private on /home/aeathb type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=a0424253b99500f8,ecryptfs_fnek_sig=04ff3bd2eb7d98cd)

This leads me to believe yes its encrypted, but I can't really tell....

EDIT: 
So brilliant idea to mount the share somewhere else!! It now mounts and I can see all of the files, but I'm getting an error on the client that says I don't have proper permissions even though I have grant access to everyone checked in samba...... It never gets easy!

---

### Post by frozen.fire on 2011-09-15
Did you do the chmod 0777 for your new directory.

As long as you dont do that, you wont be able to write any file in the shared folder from the client and will recieve that error...

---

### Post by Morbius1 on 2011-09-15
> EDIT: 
So brilliant idea to mount the share somewhere else!! It now mounts and I  can see all of the files, but I'm getting an error on the client that  says I don't have proper permissions even though I have grant access to  everyone checked in samba...... It never gets easy!You have 2 options:

[1] What frozen.fire posted

That will take care of the access problem and depending on where you created the folder you probably have to do it anyway.

[2] force user

There is one problem that [1] will not fix. Your shares are set up to allow read/write access but when the remote guest user adds a file it will save as owner = "nobody" - literally. Since aeathb is not "nobody" aeathb won't be able to edit the file locally.

There's a couple of ways to fix this but one of them is something I mentioned above and that's to convert the remote user from "nobody" to "aeathb":

You can place the following line in the [global] section:
```
force user = aeathb
```Or you can place it in the share definition itself:
> [Music]
    path = /path/to/Music/folder
    read only = No
    guest ok = Yes                      
force user = aeathbAs a side benefit it comes in handy should you ever want to share an external USB drive formatted in NTFS or FAT32. Those drives will mount with you as owner and access limited to you alone. The "force user" will make everyone you so access to the external drive will be allowed.

*[COLOR=Blue]Side Note[/COLOR]: The "force user" is applied after authentication by Samba so should you decide later on to limit access to a given share to a subset of remote users you can still do that but after they provide the correct username and password they will be converted to you.*

---

### Post by frozen.fire on 2011-09-15
No offence to anybody but i always had a very simple procedure to configure samba..

```
$sudo apt-get install samba
$sudo vi /etc/samba/smb.conf
> 
[LEFT]interfaces = lo eth0       (for you it might be eth1 or else... do "ifconfig [-a]" without quotes to find the network interface for you.)
bind interfaces only = true[/LEFT]
[LEFT]> 

security = share
...
...
guest account = nobody
> 

 [Guest Writeable Share]
        comment = Guest access share
        path = /path/to/dir/to/share
        browseable = yes
        read only = yes
        guest ok = yes
$ testparm         (to check that the config is good, might not work always without error but its been ok)
[/LEFT]
 $ cd /path/to/dir/to/
$ chmod 777 share    (you may also use -R with chmod)

 $sudo /etc/init.d/samba reload

```It always worked for me.  The ones in the quotes need to be edited in the file /etc/samba/smb.conf (it is always a good idea to make a back up of any file before you edit.)
Hope this will be useful in future. :)

---

### Post by Morbius1 on 2011-09-15
I hope you don't take offense to this either but ...

[1] Share level security
> security = share
...
...
guest account = nobody
Share level security has been deprecated - although it's been in the deprecated state for some time now - and the guest account is already set to nobody. The current and default mechanism to achieve the same result is to have these 2 parameters set:
> security = user
map to guest = Bad User
[2]  Your share definition would be fine for a Server ( with a big "S" ) but in the peer-to-peer type of environment that samba is used in a home lan it has the same problem as I described above. 

When "guest" adds a file to the share it will save with:
owner = nobody
group = nogroup
mode = 644

If the share is on my system I can read the file, move it, and even delete it, but I can't edit it. You can play around with create masks, setgids on the Server side and such or just use force user but something will need to done to make it work for the server user.

[3] Recursive chmod using octal notation.
>  chmod 777 share    (you may also use -R with chmod)I wouldn't use "-R" with the 777 only because you just set every file executable. I would suggest the following instead:
```
sudo chmod -R a+rwX /path
```The big "X" will make every folder executable ( which you must have ) but only make executable those files that were set as executable to begin with.

[4] Not to be picky but:
> sudo /etc/init.d/samba reloadThere is no longer a "samba" service and the new one is no longer in init.d. "samba" has been sent back in time and broken up to it's component daemons: smbd and nmbd. smbd is no longer a SystemV service it's now controlled by Upstart and it's file is in /etc/init/smbd.conf so the current way to restart the service is:
```
sudo service smbd restart
```

---

### Post by aeathb on 2011-09-15
So, what exactly and how exactally do you "chmod 0777"? Is that a terminal command on the server?
And do I 
force user = aeathb on the client after I try to get into the directory and see the files.....? Sorry for the dumb questions. This is new and there is so much to learn.

---

### Post by Morbius1 on 2011-09-15
On the server in a Terminal:
```
sudo chmod 0777 /mnt/Shared
```[COLOR=Blue]*Change /mnt/Shared to the exact path to your shared folder.*[/COLOR]

The "force user" is on the server as well. When the client tries to access the server's share as a guest the server will convert him to aeathb. 

Just make sure that after any kind of direct editing of smb.conf you do a smbd restart:
```
 sudo service smbd restart
```

---

### Post by frozen.fire on 2011-09-16
Morbius thanks for the correction there.... I never even looked back when i set everything to excecutable... <embarrassed> There i should have been careful... by the way, that whole code thing was just a hint... I usually set the permissions for read and write in recursive and do that only for specific users by creating a group and adding them and then setting permissions on the folder for that group..:)

And yes, of course, that samba reload doesnt work that way... service command is the right one... I was just trying to make it simpler considering the case of aeathb explaining what i wud do...i just thought he might not want to add a group and a user in it... so i just made the share global...

---

### Post by aeathb on 2011-09-16
and by under global do you mean I put it in the .conf file I was toying with earlier? If so, where exactly in the global section...?

---

### Post by Morbius1 on 2011-09-16
In /etc/samba/smb.conf on the server the global section would look like this with the new line added:
> #======================= Global Settings =======================

[COLOR=Blue] [global][/COLOR]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup
    [COLOR=Blue]**force user = aeathb**[/COLOR]Then save smb.conf and restart smbd:
```
sudo service smbd restart
```

---

### Post by aeathb on 2011-09-21
The last few posts solved my issue and the thread is now marked! Thanks Morbius1 for all of your help!!

---

