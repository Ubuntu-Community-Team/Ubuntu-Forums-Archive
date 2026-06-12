---
title: "fstab not mounting my cifs, I have to manually call mount -a"
date: 2010-04-30
forum: General Help
---

### Post by skelooth on 2010-04-30
Hi, I don't get it.

I have the following line in my fstab:
```
//192.168.0.242/websites /mnt/supercube cifs rw,user=XXX,pass=XXX,iocharset=utf8,file_mode=0777,file_mode=0777,dir_mode=0777,uid=XXX 0 0
```

But it doesn't auto mount with everything and disconnects whenever I suspend my computer. The only way to get it to mount is with
```
sudo mount -a
```
and it mounts fine with no error.

Did lucid change the way it uses fstab or something? Obviously writing mount -a isn't a huge concern, but it kind of destroys the point of putting it in my fstab.

---

### Post by dino99 on 2010-04-30
MountManager is your boy

---

### Post by skelooth on 2010-04-30
That doesnt' really look like what I'm looking for.

---

### Post by skelooth on 2010-05-03
Bump?

It makes no sense that the network share won't mount until I manually run sudo mount -a

---

### Post by skelooth on 2010-05-03
Bump?

It makes no sense that the network share won't mount until I manually run sudo mount -a

---

### Post by Morbius1 on 2010-05-03
I may get you part of the way there. It's possible that fstab is being executed before your network is up. Add the following option to your fstab entry:

```
_netdev
```Option _netdev delays mounting until the network has been enabled.

Disconnecting during a suspend is another matter. There may be something in my notes. Hopefully you'll get more responses.

---

### Post by john newbuntu on 2010-05-03
If you can script the mount command and stick the script into /etc/network/if-up.d, your mount will run as soon as your network is up.  A similar umount script thrown into /etc/network/if-down.d should bring it down.  Make sure the scripts are executable and is owned by root.

The following is an example of a mount script called by wireless network. (call it say 'mntNetShare' and change "wlan0" if not wireless by looking at the output of 'ifconfig')

```
#!/bin/bash
if [ "$IFACE" = "wlan0" ]; then
      mount -t cifs -o rw,user=XXX,pass=XXX,iocharset=utf8,file_mode=0777,file_mode=0777,dir_mode=0777,uid=XXX  //192.168.0.242/websites /mnt/supercube
fi
```Create a similar script for umount and  remove your fstab entry.
FYI, I use a similar script but serves me another purpose.

---

### Post by skelooth on 2010-05-03
Thanks guys, those solutions help greatly. 

I'm leaving the thread 'unsolved' in case anyone knows why fstab behavior has changed.

---

### Post by Morbius1 on 2010-05-03
I like the script idea a lot. Opens up all sorts of possibilities for other things. As for the change in behaviour - and trust me this is just a guess - there was a great effort to reduce boot up times. This and a similar thing that is happening to VirtualBox guests seem to be victims of "unintended consequences" of doing so.

---

### Post by john newbuntu on 2010-05-03
At some point (perhaps in Jaunty or Karmic), the networking stuff got moved to upstart.  There was a dependency introduced to bring up the network manager daemon after mounting the filesystems(in fstab).  So the behavior should be similar if you have used Karmic I'd imagine.

---

### Post by JKyleOKC on 2010-05-03
> **skelooth said:**
> I'm leaving the thread 'unsolved' in case anyone knows why fstab behavior has changed.I don't think that fstab, itself, has changed. However a large part of the development done for Lucid dealt with speeding up the boot process by doing as much as possible in parallel rather than sequentially. It's quite likely that the speedup has made the mount operation happen before the network is fully operational! The option to delay mounting (which I didn't know about until reading this thread) should take care of it if that's the case...

---

### Post by skelooth on 2010-05-07
I've gotta say, even though I'm not a full time system administrator, I administrate a handful of important servers, and this change is really bullocks.  It's great that I can move the mounting to ifup/ifdown config, but it's an over all crappy change for what my computing needs are (I really love ubuntu but it's becoming less and less appropriate for work)

Does the server edition suffer from the same "feature" do you guys know? I'm glad I found out now before I upgraded my LTS server! 

Thank you, all of you, so much. It's tough to keep up on all of this stuff. I only use the LTS distros because I try to avoid situations like this.

The _netdev flag did not help for the record.

---

### Post by geekyhawkes on 2010-05-07
PI have been looking for help here with a similar problem ([http://ubuntuforums.org/showthread.php?t=1467986&page=2](http://ubuntuforums.org/showthread.php?t=1467986&page=2)) so Im now trying this script;

#!/bin/bash
if [ "$IFACE" = "wlan0" ]; then
mount -t cifs -o rw,user=xxx,pass=xxx,iocharset=utf8,file_mode=0777 ,file_mode=0777,dir_mode=0777 //192.168.1.14/share/ /media/nas/
fi

If i paste the mount command above into a terminal then the nas mounts fine, but for some reason the script doesnt seem to mount the nas (even if i ./nas.sh). What is going on?

Have i missed something about the if statement?  Ifconfig reveals that wlan0 is the correct name for the interface.

Thanks;

Andy

---

### Post by JKyleOKC on 2010-05-07
> **geekyhawkes said:**
> If i paste the mount command above into a terminal then the nas mounts fine, but for some reason the script doesnt seem to mount the nas (even if i ./nas.sh). What is going on?There could be several reasons for your problem. Most likely, I think, is that the "mount" command requires root permissions. Try running your script using "sudo" and if that's what is wrong, it should then work.

If you're trying to add the script to /etc/rc.local, that would not be a problem -- but you would need to provide the full path to the script, not just the "./nas.sh" shortcut version. No "sudo" would be needed in this case, because rc.local runs as root before you're logged in. That's why you need the full path (/home/xxx/nas.sh where xxx is your user name).

And if this still doesn't work, then you may be running into the parallel-boot situation, so try putting a "sleep 5" in rc.local just in front of the call to your script. This will force a 5-second delay which ought to be plenty of time for the network to come up so that the NAS is visible to the program. If that works, you can try cutting down the time if you don't want to delay the boot process more than you have to...

---

### Post by geekyhawkes on 2010-05-08
Maybe its my understanding, but i thought the point of putting the script in /etc/network/if-up.d/  was that it would run when the network is setup (without calling it in rc local).  Thats certainly how the umount script is working for me when i placed it in if-down.d

There is something wrong with the if statement in my script, if i # it out then the mount command works fine (when the script is called form a terminal).  With the If statement in then the script runs but doesnt mount the nas.  

Ifconfig says that wlan0 is the right device name (assuming i should be looking in the very most left hand side of the output).  

Anymore thoughts?

---

### Post by Morbius1 on 2010-05-08
Actually now that I look at it, the if statement as used in this context may be redundant. I don't know why it wouldn't run anyway but perhaps **john newbuntu** would comment on my logic.

By design any script that is placed in /etc/network/if-up.d/ will execute only after the network is up. There's really no need for the script to check the network status, so the script can look like this:
```
#!/bin/bash
mount -t cifs -o rw,user=xxx,pass=xxx,iocharset=utf8,file_mode=0777 ,file_mode=0777,dir_mode=0777 //192.168.1.14/share/ /media/nas/

```

---

### Post by geekyhawkes on 2010-05-09
Well this is where i am now;

if i hask out the if statement then the nas still doesnt auto mount during logon.  If however i manually run the script 

sudo ./nas.sh

then the nas mounts fine.  

Is there something else i need to do get the script to run automatically as the network comes up?

---

### Post by geekyhawkes on 2010-05-10
Just as extra info, if i just try and run the script as a normal user it doesnt mount (telling me only sudo can mount), so is there some kind of chmod i need to do to the script to make it run as root during log in from the ip-up.d folder?

---

### Post by JKyleOKC on 2010-05-10
> **geekyhawkes said:**
> Just as extra info, if i just try and run the script as a normal user it doesn't mount (telling me only sudo can mount), so is there some kind of chmod i need to do to the script to make it run as root during log in from the ip-up.d folder?Have you tried copying the script to the /etc/if-up.d folder using "sudo cp nas.sh /etc/if-up.d/nas" (note no ".sh" on the target name)? The copying will automatically change the owner and group for the target file to "root" just like all the other scripts there, so it ought to work properly.

Actually "chown" and "chmod" only change the attributes and properties of files and directories; they always execute in the context of the logged-in user unless "su" or a variant such as "sudo" temporarily changes the context.

---

### Post by skelooth on 2010-05-10
Now I'm really curious.... it seems to randomly connect on boot. IE, maybe 4 out of 5 times I have to manually sudo mount -a, but that once in a while it will come up just fine.

---

### Post by alienprdkt on 2010-05-10
> **skelooth said:**
>   It's great that I can move the mounting to ifup/ifdown config, but it's an over all crappy change for what my computing needs are )



I have the same issues mounting drives with ubuntu!

my network drives mount after a mount -a 

my 2 500gb ext3 drives wont mount at all or unmount for that matter till I had created a script.

can get list of drives by either running 

fdisk -l     

or by uuid

ls /dev/disk/by-uuid -lah

   
heres the script i had to use ...

#!/bin/sh
mount -t ext3 /dev/sda /mymount/1 
mount -t ext3 /dev/sdb /mymount/2
exit0

save to startup script location:
/etc/rc0.d/K99custom_mount 

make executable:
chmod +x /etc/rc0.d/K99custom_mount

then create a shutdown script

#!/bin/sh
umount -t ext3 /dev/sda 
umount -t ext3 /dev/sdb
exit0

save as  /etc/rc6.d /K99custom_mount
chmod +x  /etc/rc6.d /K99custom_mount

That seemed to be the only solution for me that worked. Maybe you can re-work it to fit your network files system type... 

something maybe like this (credentials is only needed if you need to enter username and password)

#!/bin/sh
mount -t cifs /dev/sda /mymount/1 credentials=~/.credentialfile
mount -t cifs /dev/sdb /mymount/2 credentials=~/.credentialfile

exit0

create credential file:
username=your username
password=your password

save as ~/.credentialfile

help from [http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown]("http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown")

---

### Post by geekyhawkes on 2010-05-10
> **JKyleOKC said:**
> Have you tried copying the script to the /etc/if-up.d folder using "sudo cp nas.sh /etc/if-up.d/nas" (note no ".sh" on the target name)? The copying will automatically change the owner and group for the target file to "root" just like all the other scripts there, so it ought to work properly.

Actually "chown" and "chmod" only change the attributes and properties of files and directories; they always execute in the context of the logged-in user unless "su" or a variant such as "sudo" temporarily changes the context.


Actually fixed it thanks!  Im pretty new to messing about with the chmod and chown stuff (its causing some problems within my mythtv setup) and the above detail has been pretty useful.  

Thanks for the help, this worked for me and actually once you get to the bottom of it, its pretty simple to get it working.

Thanks again!

---

### Post by JKyleOKC on 2010-05-11
That sounds like a race condition, in which the mount command in the if-up script gets executed before the network is actually fully up (or maybe before the Samba routines are ready to support the cifs type) but occasionally the timing is right. In the old sysv approach, the decimal numbers following the "S" in the link's name handled the timing and it was easy to adjust for things like this, but with the new upstart system it's much more problematical. The scripts in /etc/init.d do list which others are required for starting, but those in /etc/network subdirectories do not -- making it a trial-and-error situation for most of us.

---

### Post by skelooth on 2010-05-11
> **JKyleOKC said:**
> That sounds like a race condition, in which the mount command in the if-up script gets executed before the network is actually fully up (or maybe before the Samba routines are ready to support the cifs type) but occasionally the timing is right. In the old sysv approach, the decimal numbers following the "S" in the link's name handled the timing and it was easy to adjust for things like this, but with the new upstart system it's much more problematical. The scripts in /etc/init.d do list which others are required for starting, but those in /etc/network subdirectories do not -- making it a trial-and-error situation for most of us.
Can this be listed as a real "bug" to be fixed? I don't care about 10 second boot times if I have to babysit things. I've been using linux for.... geez, 10 years now already? And I've never run into something as "dumb" as this. We as a community should not be sacrificing boot time daemon stability to shave a few seconds off the boot it's self. It's just... counter productive.

---

### Post by JKyleOKC on 2010-05-12
I agree with you 1000%; I've not liked upstart since it first showed up in Hardy LTS but at least there the race effects were minimal. When Hardy finally goes EOL, I may have to switch all my systems to something else although I really do like Ubuntu better than anything else I've tried (Slackware 2, SUSE 6, Mandrake 8, Mandriva, Puppy, and Mint, so far). I've used PCs since the days of CP/M and know my way around the internals of a number of systems (including the undocumented aspects of MS-DOS from Versions 3 through 6) but the idea of totally parallelizing what's essentially a serial process strikes me as less than brilliant (to be as polite about it as I can)...

Can you file the bug report? I'm avoiding Lucid completely at this stage of its development, and in addition I've not yet figured out how to use the bug report system...

---

### Post by alienprdkt on 2010-05-13
> **skelooth said:**
> Can this be listed as a real "bug" to be fixed? I don't care about 10 second boot times if I have to babysit things. I've been using linux for.... geez, 10 years now already? And I've never run into something as "dumb" as this. We as a community should not be sacrificing boot time daemon stability to shave a few seconds off the boot it's self. It's just... counter productive.


AGREED!!!

my mount and unmount scripts are definitely counter productive... this needs to be fixed. 
especially when I have setup an 8 hard disc system... and only 3 of them chose to mount.

Not a problem with the discs either since they mounted fine manually.
 
That is why I just created my own mount and umount scripts and placed them in the correct locations for start up and shutdown, but why should I have to avoid fstab which I have been using for the past 7 yrs. is beyond me. Just to spare something that takes not even 2 secs to run properly.

---

### Post by skelooth on 2010-05-14
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/508186](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/508186)

I didn't start the thread, but apparently this is where we can go to provide information. I've never had to file a bug before so I really don't know too much about the process. Please go to the link and click the link saying it affects you. Hopefully a Dev will see it.

---

### Post by JKyleOKC on 2010-05-15
Thanks for the link; others affected by this need to create Launchpad accounts for themselves and add to the report. Currently it says that only two persons are affected by this bug -- and that certainly won't attract much effort toward fixing it!

The page linked to has its own link to "register" for Launchpad, and that's a necessary step toward bumping the bug report -- but if enough of us complain, it might get some attention...

---

### Post by Morbius1 on 2010-05-17
Until this is fixed I'm wondering if a simpler solution is possible:

Create a script with the "mount -a" command in it and place it in if-up.d:

Open **Terminal**
Type **gksu gedit /etc/network/if-up.d/fstabmount**
Add the following lines:
```
#!/bin/sh
mount -a
```Save the file, exit gedit, and back in the terminal make the file executable:
```
sudo chmod +x /etc/network/if-up.d/fstabmount
```Haven't tested it myself because this is not a problem for me but if it works then everyone could go back to having fstab entries as before instead of these mount and umount scripts.

Anyone care to test this hypothesis ?

---

### Post by skelooth on 2010-05-17
Exactly.

Fellows: Please register your problem with launchpad! This is, in my opinion, a significant system administration problem.

---

### Post by unisubzero on 2010-05-17
> **Morbius1 said:**
> Until this is fixed I'm wondering if a simpler solution is possible:

Create a script with the "mount -a" command in it and place it in if-up.d:

Open **Terminal**
Type **gksu gedit /etc/network/if-up.d/fstabmount**
Add the following lines:
```
#!/bin/sh
mount -a
```Save the file, exit gedit, and back in the terminal make the file executable:
```
sudo chmod +x /etc/network/if-up.d/fstabmount
```Haven't tested it myself because this is not a problem for me but if it works then everyone could go back to having fstab entries as before instead of these mount and umount scripts.

Anyone care to test this hypothesis ?

                                 It seems to be working for me at least !
 

 Thanks for the great and simple solution :)

---

### Post by skelooth on 2010-05-18
> **skelooth said:**
> 
Fellows: Please register your problem with launchpad! This is, in my opinion, a significant system administration problem.

Guyz, come on :)

If you care enough to post: care enough to file a bug report.

---

### Post by natuk on 2010-05-23
> **Morbius1 said:**
> Until this is fixed I'm wondering if a simpler solution is possible:

Create a script with the "mount -a" command in it and place it in if-up.d:

Open **Terminal**
Type **gksu gedit /etc/network/if-up.d/fstabmount**
Add the following lines:
```
#!/bin/sh
mount -a
```Save the file, exit gedit, and back in the terminal make the file executable:
```
sudo chmod +x /etc/network/if-up.d/fstabmount
```Haven't tested it myself because this is not a problem for me but if it works then everyone could go back to having fstab entries as before instead of these mount and umount scripts.

Anyone care to test this hypothesis ?

This seems to be working with me as well. Thanks.

---

### Post by h0rnman on 2010-06-16
For my part, I am using a 2 step solution:

1)  Manually add the shares/locations to be automounted to a new script (I call mine mount-mapped-drives.conf) in the /etc/init folder.  The file contents are as follows:

```

# mount-mapped-drives
#
# Manually mount network shares after network becomes available

description	"Mount network shares"

start on net-device-up

task

script
	mount -t cifs \\\\192.168.1.110\\Music /media/MediaCenter/Music -o iocharset=utf8,credentials=/root/.cifscred,file_mode=0777,dir_mode=0777
	mount -t cifs \\\\192.168.1.110\\Programs /media/MediaCenter/Programs -o iocharset=utf8,credentials=/root/.cifscred,file_mode=0777,dir_mode=0777
end script

```

2)  Change the location of the umountnfs.sh script as follows:

```

sudo mv /etc/rc0.d/S31umountnfs.sh /etc/rc0.d/K11umountnfs.sh
sudo mv /etc/rc6.d/S31umountnfs.sh /etc/rc6.d/K11umountnfs.sh

```

The first part makes use of upstart's 'net-device-up' message to activate the mount process ONLY when the network comes up, and the second part works around an issue with SysV that puts network device disconnection before network share unmounts (using a 'K' script ensures that the script is called with the 'stop' parameter).

Hope that helps!

Chris

---

