---
title: "a question about umount"
date: 2010-09-09
forum: General Help
---

### Post by zarzor_2010 on 2010-09-09
Hi all
Please, I have a quick question about umount

I want to ask if i used umount to unmount a folder in my pc and then I restarted is this folder will still be unmounted

Or I will have to do umount every time I restart. If yes, then is there any thing I can do to make it a permenant unmount?


Thanks all for your help
Mina

---

### Post by NearlyALaugh on 2010-09-10
Nautilus (the file manager) seems to automount all devices by default. Short of disabling this "feature" entirely, I don't think there's much you can do.

Someone else correct me if I'm wrong.

---

### Post by garvinrick4 on 2010-09-10
If you have a device you can have it mount, mount and open or not mount at all in configuration editor. Open the configuration editor and go to apps to nautilus and the to
desktop and preferences and check or uncheck what you want to have on desktop at boot-up. Now as for folders (directories) if you have made any short-cuts on your desktop they will be there until you delete them.

---

### Post by garvinrick4 on 2010-09-10
i am sorry forgot to give you the package to implement.

```
sudo apt-get install gconf-editor
```

Will be under Applications/System Tools

---

### Post by zarzor_2010 on 2010-09-10
Thank you all for your reply
 
I think I was not clear in my question. I have a PC in my university. and when I ssh to it
The usr/local folder is mounted to some other folder in the univ server. here is what i get when i use mount -l
 
appserver1:/export/d1/Linux/doe on /usr/local type nfs4 (ro,sec=.......)

so, I umount the folder using "umount /usr/local"
 
Now is this umount will be permenant or i will have to do it every time I restart the computer.?
 
Note; I tried looking in the /etc/fstab and there is no entry for /usr/local
 
here is my fstab:
 
/dev/VolGroup00/LogVol00 / ext3 defaults 1 1
LABEL=/boot /boot ext3 defaults 1 2
tmpfs /dev/shm tmpfs defaults 0 0
devpts /dev/pts devpts gid=5,mode=620 0 0
sysfs /sys sysfs defaults 0 0
proc /proc proc defaults 0 0
/dev/VolGroup00/LogVol01 swap swap defaults 0 0
 
Thanks again
Mina

---

### Post by zarzor_2010 on 2010-09-11
Any help about this issue?
 
Thanks

---

### Post by bodhi.zazen on 2010-09-11
How is it being mounted then ? I do not see an entry in fstab.

---

### Post by robsoles on 2010-09-12
> **zarzor_2010 said:**
> Thank you all for your reply
 
I think I was not clear in my question. **[COLOR=Red]I have a PC in my university. and when I ssh to it[/COLOR]**
The usr/local folder is mounted to some other folder in the univ server. here is what i get when i use mount -l
 
appserver1:/export/d1/Linux/doe on /usr/local type nfs4 (ro,sec=.......)

so, I umount the folder using "umount /usr/local"
 
Now is this umount will be permenant or i will have to do it every time I restart the computer.?

...

If you SSH into the PC at the uni and umount the resource and then close ssh and then restart your home(?) PC and then SSH back to the PC at the uni the resource should still be unmounted UNLESS there is something in your login process (on the PC at uni) which mounts the resource.

It is probable that the PC at uni is configured to mount the resource, in booting, where you are finding it to umount.

If that is not the contents of the /etc/fstab from the PC at uni could you post that content instead please? Is it your PC at the uni? Is there anything else special about the PC at uni you could tell?

---

### Post by zarzor_2010 on 2010-09-13
> **robsoles said:**
> If you SSH into the PC at the uni and umount the resource and then close ssh and then restart your home(?) PC and then SSH back to the PC at the uni the resource should still be unmounted UNLESS there is something in your login process (on the PC at uni) which mounts the resource.

It is probable that the PC at uni is configured to mount the resource, in booting, where you are finding it to umount.

If that is not the contents of the /etc/fstab from the PC at uni could you post that content instead please? Is it your PC at the uni? Is there anything else special about the PC at uni you could tell?

Thank you all for your reply

It seems that the PC at university is configured to mount it back automatically. The problem it was not mounted automatically before. when I upgraded my linux version the problem happened.

Now when I restart my PC at university it gets mounted back again.

The /etc/fstab file shown is my univ PC. here its again.
/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/VolGroup00/LogVol01 swap                    swap    defaults        0 0


Let me give you mount -l output, it may help
/dev/mapper/VolGroup00-LogVol00 on / type ext3 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda2 on /boot type ext3 (rw)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
appserver1:/export/d1/Linux/doe on /usr/local type nfs4 (ro,sec=krb5,hard,intr,rsize=32768,wsize=32768,addr=134.117.9.133)
gambia:/export/d2/grads/madel on /home/madel type nfs4 (rw,sec=krb5,hard,intr,rsize=32768,wsize=32768,addr=134.117.9.124)
saturn:/export/d4/home on /var/web type nfs4 (rw,sec=krb5,hard,intr,rsize=32768,wsize=32768,addr=134.117.9.198)


I know that I cann in my ~/.bash_profile the command to unmount it every time I restart, but I wana do it from the source itself.

Thanks again
Mina

---

### Post by bodhi.zazen on 2010-09-13
Comment out this lin in fstab :

appserver1:/export/d1/Linux/doe on /usr/local type nfs4 (ro,sec=krb5,hard,intr,rsize=32768,wsize=32768,add  r=134.117.9.133)

---

### Post by zarzor_2010 on 2010-09-13
Thank you for your reply
But this line is not in the /etc/fstab file.
 
it only appears when I do mount -l to show all the mounted folders.
any idea where it could be beside the /etc/fstab file?
 
Thanks alot
Mina

---

### Post by bodhi.zazen on 2010-09-13
autofs perhaps.

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Again, look in /etc/fstab on the machine you ssh into (server) not the client.

---

### Post by robsoles on 2010-09-13
If the problem is not resolved for you yet then maybe it will help people to help you if you post back the resulting output from terminal for this command: (executed on uni PC, not client)
```
ls /etc/*fs*
```Perhaps not but it might provide a clue.

---

### Post by zarzor_2010 on 2010-09-16
Thank you all for your reply

I have read about the autofs. But I did not find this entry in auto.master, auto.misc, auto.net.

here is my auto.master

[PHP]net -hosts 
/misc /etc/auto.misc 
/- /etc/auto.direct 
/home ldap://ldap4/automountMapName=auto_home,dc=doe,dc=carleton,dc=ca -fstype= 
+auto.master [/PHP]

here is my /etc/auto.net

[PHP]key="$1" 

# add "nosymlink" here if you want to suppress symlinking local filesystems 
# add "nonstrict" to make it OK for some filesystems to not mount 
opts="-fstype=nfs,hard,intr,nodev,nosuid" 

# Showmount comes in a number of names and varieties.  "showmount" is 
# typically an older version which accepts the '--no-headers' flag 
# but ignores it.  "kshowmount" is the newer version installed with knfsd, 
# which both accepts and acts on the '--no-headers' flag. 
#SHOWMOUNT="kshowmount --no-headers -e $key" 
#SHOWMOUNT="showmount -e $key | tail -n +2" 

for P in /bin /sbin /usr/bin /usr/sbin 
do 
        for M in showmount kshowmount 
        do 
                if [ -x $P/$M ] 
                then 
                        SMNT=$P/$M 
                        break 
                fi 
        done 
done 

[ -x $SMNT ] || exit 1 

# Newer distributions get this right 
SHOWMOUNT="$SMNT --no-headers -e $key" 

$SHOWMOUNT | LC_ALL=C sort -k 1 |  
        awk -v key="$key" -v opts="$opts" -- ' 
        BEGIN   { ORS=""; first=1 } 
                { if (first) { print opts; first=0 }; print " \\\n\t" $1, key ":" $1 } 
        END     { if (!first) print "\n"; else exit 1 } 
        ' | sed 's/#/\\#/g'  [/PHP]

here is my /etc/auto.misc

[PHP]cd              -fstype=iso9660,ro,nosuid,nodev :/dev/cdrom 

# the following entries are samples to pique your imagination 
#linux          -ro,soft,intr           ftp.example.org:/pub/linux 
#boot           -fstype=ext2            :/dev/hda1 
#floppy         -fstype=auto            :/dev/fd0 
#floppy         -fstype=ext2            :/dev/fd0 
#e2floppy       -fstype=ext2            :/dev/fd0 
#jaz            -fstype=ext2            :/dev/sdc1 
#removable      -fstype=ext2            :/dev/hdd  [/PHP]


here is the output from  ls /etc/*fs*

[PHP]/etc/autofs_ldap_auth.conf  /etc/gnome-vfs-mime-magic  /etc/mke2fs.conf
/etc/fstab                  /etc/login.defs

/etc/gnome-vfs-2.0:
modules
[/PHP]


Thank you all for your help.
Thanks
Mina

---

### Post by zarzor_2010 on 2010-09-16
Just a quick note. all of these files and commands are run on the univ PC (server).

Thanks
Mina

---

### Post by robsoles on 2010-09-16
Perhaps it is being mounted by a login action that is scripted in your home directory or something.

Is the univ PC installed as 'server' or 'desktop'? (does it have a GUI/Desktop?)

Is someone (including you) logged into a session on the univ PC when you login via SSH?

Is it your own PC at the uni or is it their property?

---

### Post by zarzor_2010 on 2010-09-17
> **robsoles said:**
> Perhaps it is being mounted by a login action that is scripted in your home directory or something.

Is the univ PC installed as 'server' or 'desktop'? (does it have a GUI/Desktop?)

Is someone (including you) logged into a session on the univ PC when you login via SSH?

Is it your own PC at the uni or is it their property?

Thank you for your reply.
The PC at the university is a desktop. It is in my office as I a graduate student. I use it for my work at the univ. and some times I have to ssh from home to do some work.

no one else uses this computer but me. 

if it is mounted from a login script in my home. where it is most likely would be? I tried to check .bashrc and .bash_profile and it was not there too.

Thanks 
Mina

---

### Post by robsoles on 2010-09-17
I don't know yet and I'm suspicious of something else going on so I'll find out if necessary but I'm thinking not necessary yet.

I think you are most likely leaving it with yourself logged into a desktop session and perhaps you are locking the screen.

Next time you are leaving the university please log right out of your desktop session. When you get home SSH in to the PC at the uni and check for this mount - please post back your result.

---

### Post by zarzor_2010 on 2010-09-20
Thank you for your reply
I went to the university and loged out before going home.
 
Now when I ssh to the uni lab and run mount -l in the univ machine.
 
it still gives that /usr/local is ounted to the univ server
 
Thanks
Mina

---

### Post by zarzor_2010 on 2010-09-20
Thank you all for your help. Today I went to the server administrator in my univ to tell him about my problem.

He said that autofs gets its configuration from the main server of the campus. And the only way to unmount /usr/local is to stop autofs from running. but this option will make every thing unmount including my /home directory .

So, I think I will have to deal with it and change my installing directory.

Thank you all for your help
Mina

---

