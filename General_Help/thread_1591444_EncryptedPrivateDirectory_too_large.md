---
title: "EncryptedPrivateDirectory too large"
date: 2010-10-09
forum: General Help
---

### Post by xenton on 2010-10-09
This thread was nearly titled "The volume Filesysyem root has only 128 KB free space remaining" then I discovered the cause my Encrypted Private Directory had grown to 20GB eating all the free space on my Ubuntu system partition. Here's what happened:

                      All was well with my system last night, left it downloading 2 GB of files from the internet to an NTFS drive to return to low space errors this morning.
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot.png?t=1286633997[/IMG]

 I checked and nothing had been downloaded to my Ubuntu partition, and even if it had, it could of handled the 2GB without issue. Did some reading on here and the first step I tried found the problem:
 

```
mark@media:~$ df -h
 Filesystem            Size  Used Avail Use% Mounted on
 /dev/mapper/nvidia_abjcfaad3
                        20G   19G   54M 100% /
 none                  1.3G  348K  1.3G   1% /dev
 none                  1.3G  440K  1.3G   1% /dev/shm
 none                  1.3G  340K  1.3G   1% /var/run
 none                  1.3G     0  1.3G   0% /var/lock
 none                  1.3G     0  1.3G   0% /lib/init/rw
 /dev/mapper/nvidia_abjcfaad2
                       489G  386G  104G  79% /media/Seven
 /dev/mapper/nvidia_jjeidcec1
                       1.9T  1.4T  462G  76% /media/Storage
 /dev/mapper/nvidia_abjcfaad1
                        71G   47G   24G  67% /media/XP
[COLOR=Red] /home/mark/.Private    20G   19G   54M 100% /home/mark[/COLOR]
 
```The problem is clearly the .Private directory in my home folder I have no idea how it got there here's what the mount command turns up for it:
 

```
/home/mark/.Private on /home/mark type ecryptfs (ecryptfs_sig=***************c,ecryptfs_fnek_sig=***************e,ecryptfs_cipher=aes,ecryptfs_key_bytes=16) 
 gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)  

``` I have never set this up, and knew nothing about the encrypted private directory until I just googled it and found it was a feature introduced with intrepid.
 

 A few questions
 

 
[LIST=1]
[*]Should it be there     in Lucid without me seting it up?
[*]How the heck did     it get up to 20 gigs all of a sudden?
[*]Is it used by the     system for anything or can I either delete it or follow the removal     guide in the Wiki?
[/LIST]
A couple of reboots later and the .private directory has shrunk and Ubuntu is running well again, it's still far too large considering I don't even use it though:

```
mark@media:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/nvidia_abjcfaad3
                       20G   12G  7.1G  63% /
none                  1.3G  348K  1.3G   1% /dev
none                  1.3G  332K  1.3G   1% /dev/shm
none                  1.3G  292K  1.3G   1% /var/run
none                  1.3G     0  1.3G   0% /var/lock
none                  1.3G     0  1.3G   0% /lib/init/rw
/dev/mapper/nvidia_abjcfaad2
                      489G  386G  104G  79% /media/Seven
/dev/mapper/nvidia_jjeidcec1
                      1.9T  1.4T  462G  76% /media/Storage
/dev/mapper/nvidia_abjcfaad1
                       71G   47G   24G  67% /media/XP
[COLOR=Red]/home/mark/.Private    20G   12G  7.1G  63% /home/mark[/COLOR]

```Any help here would be greatly received, I am holding off taking any action for fear of breaking something, it's a hidden directory that I don't really understand, they probably hid it from me for a reason :)

---

### Post by xenton on 2010-10-09
Right it's hidden, I didn't put anything in there, and everything in there is encrypted, so I'm going to go ahead and try to remove it using [these instructions]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup"). Wish me luck.

---

### Post by xenton on 2010-10-09
Okay then, that didn't go well. Ended up with an inaccessible home directory which meant nautilus woulndn't start. Booted into the recovery mode and chmod 777 home. Now appear to have a new home directory (all old files gone). Theme settings, application settings (cairo-dock and firefox) all gone.

Seems the information in the Wiki is outdated and the EncryptedPrivateDirectory is used heavily in Lucid for storing important settings.

I have modified the permissions of home again to 755.

I will leave as is for the moment, settings for the apps and desktop can easily be redone, I don't want to go back to the encrypted private directory as it went wrong and hopefully I can manage without it.

I would still be grateful if anyone has any ideas on:

1) Why it grew to 19GB in the first place?
2) is there a way to remove it without losing data?
3) Any drawbacks to not using it?

Ta Muchly

---

