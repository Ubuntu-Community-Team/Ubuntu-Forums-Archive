---
title: "How to acces encrypted ext4 partition"
date: 2010-09-07
forum: General Help
---

### Post by abbaz on 2010-09-07
I recently installed ubuntu 10.10 beta 64bit with an encrypted ext 4 partition. Now the OS wont boot anymore, I will switch back to 10.04. Unfortunately I first have to get some data from that partition.

When I boot from a live cd, I can mount the partition but Im of course not allowed to open the folder I need. But I cant find a way to enter my password.

What do I need to do, so I can copy those files and reinstall the OS.

---

### Post by wojox on 2010-09-07
Well this is a good lesson to make sure you back up. Have you tried [Recovering Your Data Manually]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually")

---

### Post by abbaz on 2010-09-07
Those are just podcasts I downloaded, but I have a limit on my internet connection so I dont want to download them again. Also the OS was installed by saturday, takes me two hours tops to configure a new one.

I cant perform the procedure in your link because i only have one pw (login i suppose) and i cant get the mount pw using the suggested command line.

---

### Post by abbaz on 2010-09-07
Also I cant find a way to boot a recovery mode.

The purple loading screen is not graphical as normal but only text on purple background.
By pushing Esc it goes into text output on black ground.
Everything is normal until he asks for login password. This phrase only stays there for 1 sec an then the screen gets all black.

Isnt there some recovery mode that i can boot.

---

### Post by abbaz on 2010-09-07
Sep  7 22:06:47 ubuntu ecryptfs-unwrap-passphrase: Error attempting to open [/home/.ecryptfs/username/.ecryptfs/wrapped-passphrase] for reading
Sep  7 22:07:03 ubuntu ecryptfs-unwrap-passphrase: Error attempting to open [/home/.ecryptfs/georg/.ecryptfs/wrapped-passphrase] for reading

wasnt sure if username had to be replaced or not

anyone an idea why my mount pw cant be found
also with 10.04 there was a boot menu who let me choose a text based mode, this would be enough to copz the files but a cant find such an option in 10.10 and the screen just drops dead black one second after prompting me to enter my login pw

---

### Post by JohnHeikkila on 2010-09-07
When you boot, it shows the Grub loading.. part, right?
Press ESC there and select the recovery mode kernel to be booted.

---

### Post by wojox on 2010-09-07
It's encrypted. You need your paraphrase to undo it. What does this say

```
ls /home/.ecryptfs/georg/.ecryptfs
```

---

### Post by abbaz on 2010-09-07
No thats the point it goes from the motherboard screen (the one where you can enter BIOS) right to the purple ubuntu loading screen (but not the fancy graphical version, just written text on purple ground)
Sometimes there will be a error message (for 1 sec, to short to note down), sometimes the screen turns black right away.

---

### Post by abbaz on 2010-09-07
> **wojox said:**
> It's encrypted. You need your paraphrase to undo it. What does this say

```
ls /home/.ecryptfs/georg/.ecryptfs
```

no such file or directory
but Im on a live cd, are you sure this command wont be searching for a user named georg on my life cd OS...

---

### Post by wojox on 2010-09-07
Your booting from a Live CD?

Do you have a nvidia graphics card/chip.

---

### Post by wojox on 2010-09-07
Is georg your real user name?

Here's what mine looks like

```

wojox@wojox-laptop:~$ ls /home/.ecryptfs/wojox/.ecryptfs
auto-mount  auto-umount  Private.mnt  Private.sig  wrapped-passphrase

```

---

### Post by abbaz on 2010-09-07
yes, i can also boot from a win 7 partition on another HDD, but then i cant see the ext4 partition at all of course
from the live cd i can mount the partition but dont have acces to the home georg folder where my data are stored

yes georg is my real username, in german thats without a second e on the end

no i  have a ati amd 5870 graphics card and a core i7 930 cpu

i was thinking, that it could be the graphics card driver
but when i press esc on the purple loading screen, it switches to text mode but will still turn black 1 sec after asking for login pw

---

### Post by abbaz on 2010-09-07
so I figured out that I have to use ```
 ecryptfs-unwrap-passphrase /home/.ecryptfs/username/.ecryptfs/wrapped-passphrase
```with the correct path since im booting from a live cd

I still get error messages
```
Sep  7 23:16:53 ubuntu ecryptfs-unwrap-passphrase: Error attempting to open [/media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/.ecryptfs/georg/.ecryptfs/wrapped-passphrase] for reading
```

edit
just forgot to use sudo, now I have the mount pw printed, looks good

---

### Post by abbaz on 2010-09-07
So I got the mount passphrase by now but this procedure to manually recover my data wont work
```
ubuntu@ubuntu:~$ sudo ecryptfs-add-passphrase  --fnek
Passphrase: 
Inserted auth tok with sig [7596c129c8a0b65b] into the user session keyring
Inserted auth tok with sig [5b3958b47bf6e896] into the user session keyring
ubuntu@ubuntu:~$ sudo mount  -t ecryptfs /media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/.ecryptfs/georg/.ecryptfs/.Private /media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/georg/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 1
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 1
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [7596c129c8a0b65b]: 5b3958b47bf6e896
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=5b3958b47bf6e896
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=7596c129c8a0b65b
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [7596c129c8a0b65b] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : yes
Successfully appended new sig to user sig cache file
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
ubuntu@ubuntu:~$ 

```

syslog says
Sep  7 23:28:10 ubuntu mount.ecryptfs: could not resolve full path for source /media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/.ecryptfs/georg/.ecryptfs/.Private [-2]
Sep  7 23:33:09 ubuntu mount.ecryptfs: could not resolve full path for source /media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/.ecryptfs/georg/.ecryptfs/.Private [-2]

---

### Post by abbaz on 2010-09-07
not making any progress here```
ubuntu@ubuntu:~$ sudo ecryptfs-add-passphrase  --fnekPassphrase: 
Inserted auth tok with sig [22b9d3d5715aab5d] into the user session keyring
Inserted auth tok with sig [edae0fbf51e655c5] into the user session keyring
ubuntu@ubuntu:~$ sudo mount  -t ecryptfs /media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/.ecryptfs/georg/.ecryptfs /media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/georg
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 1
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 1
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [22b9d3d5715aab5d]: edae0fbf51e655c5
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=edae0fbf51e655c5
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=22b9d3d5715aab5d
Mounted eCryptfs
ubuntu@ubuntu:~$ cd /media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/georgbash: cd: /media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/georg: Permission denied
ubuntu@ubuntu:~$ cd /media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/.ecryptfs/georg/.ecryptfs
bash: cd: /media/2781465b-e400-4ffd-84d6-5dfa9f83f57e/home/.ecryptfs/georg/.ecryptfs: Permission denied
ubuntu@ubuntu:~$ 

```

I just checked the box encrypt underlying file system while installing ubuntu 10.10

---

### Post by wojox on 2010-09-07
I'm out of steam George. For what it's worth (and I hate to tell anyone to reinstall) it would seem quicker to reinstall.

It shouldn't take two hours this time since you've done it once and are a little more familiar with it. ;)

---

### Post by abbaz on 2010-09-07
Im reinstalling anyway, [I]first I have to copy my music, documents and video folders

in the last attempt, I didnt try to mount that Private folder (never heard of it anyway) but the home georg folder
that clearly changed something I got those 

Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=edae0fbf51e655c5
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=22b9d3d5715aab5d
Mounted eCryptfs

lines for the first time, also szslog doesnt give me error messages
but still i cant open the corresponding folders

I highly doubt that Im the first one who encryptet his file system and who cant boot his system normaly. There has to be a way to mount it manually, ive got the key
[/I]

---

