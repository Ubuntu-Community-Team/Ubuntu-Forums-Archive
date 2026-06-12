---
title: "home directory not decrypting on login - 10.04 ecryptfs"
date: 2010-10-11
forum: General Help
---

### Post by thirstyjon on 2010-10-11
Ubuntu 10.04 LTS

Ran some updates, finally got around to rebooting.

When I rebooted, It came up with Some errors about missing files, etc...

Came to discover my home directory was not decrypted. I simply had a readme file that said to run "encryptfs-mount-private".

When I do it doesn't tell me the passphrase is incorrect, it tells me

```
Inserted auth tok with sig [xxxxxxxxxx] into the user session keyring
You do not own that encrypted directory
```

and I do own it. If I put in a different pass it tells me it's incorrect, I'm logging in fine, but my home directory is remaining encrypted.

Help?

---

### Post by thirstyjon on 2010-10-11
please help?

---

### Post by wghornsby on 2010-10-17
I have the same problem, this time with Lubuntu 10.04. I logged in this morning and all my data and settings are encrypted. I opened a terminal and ran ecryptfs-mount-private and received the same as above: "You do not own that encrypted directory." I am the only user of the computer.

---

### Post by strm on 2010-10-21
anyone have any luck figuring this one out?
hopefully without going through the process of manually mounting your home directory as another user?

---

### Post by Remanifest on 2010-10-24
Exactly the same problem for me.  I just did an upgrade from 10.04 to 10.10.  Now my home directory is locked up within ecryptfs, and entering in my passphrase results in "You do not own that encrypted directory".

---

### Post by trasgo77 on 2010-10-24
Same problem in my xubuntu, any help?

---

### Post by trasgo77 on 2010-10-24
come on

---

### Post by trasgo77 on 2010-10-25
Could anybody help? i need my linux

---

### Post by philiaagape on 2010-11-01
I'm using Ubuntu Desktop 10.10 x86_64 and have the same problem.  It worked until some time last week.  I do not recall exactly which day or which updates I had just applied.

However, a workaround for me:

1) From the console graphical login screen hit [Ctrl]+[Alt]+[F1] to get to a terminal console
2) Login as your user (your ecryptfs home directory will not be mounted)
3) Run these commands to kill anything using your home directory:
cd ..
for pid in `lsof | grep home/<your_user_name> | awk '{print $2}'`
do
kill $pid
done
4) It should now work to mount your encypted home directory using the command 'ecryptfs-mount-private'
5) Assuming that worked, you can now hit [Ctrl]+[Alt]+[F7] to return the to the graphical login screen and login as usual.

---

### Post by notarocketscientist on 2010-11-20
I'm having the same problem. I tried manually mounting with:
```
ecryptfs-mount-private
```and got the same message as [thirstyjon]("http://ubuntuforums.org/member.php?u=1069573"). Figured I could try:
```
sudo mount -t ecryptfs /home/$username/.Private /home/$username/dummydirectory
```but it ended up with a failure. final message stated that ecrypt ended with [-2] error: no such file/directory. Also tried 
```
sudo ecryptfs-add-passphrase --fnek
```
before the previous comand. That mounted my home folder into the dummy folder, but I could still not access anything:
```
ls: cannot access Desktop: No such file or directory
```

I don't even know why would that happen. Random update disaster maybe. One things for sure - it does not help me write my thesis at all. I'm using ubuntu 10.10.

commands:

```

sudo mount -t ecryptfs .Private/ dup/
[sudo] password for $username: 
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
Filename Encryption Key (FNEK) Signature [be84a471c11e8a0b]: acde6406983317fb
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=acde6406983317fb
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=be84a471c11e8a0b
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [be84a471c11e8a0b] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
``````
ecryptfs-mount-private 
Enter your login passphrase:
Inserted auth tok with sig [acde6406983317fb] into the user session keyring
You do not own that encrypted directory
```

---

### Post by juanto on 2010-12-20
Finally I resolved this problem.

When you get "You do not own that encrypted directory" it is because there is a problem with the permission of the directory where the encrypted data is.

I didn't remember very well, but if you go to /home/ you will find a hidden directory ".ecryptfs".

You have 2 options:

1. I did it. Change the owner of that directory, in my case:

$ sudo chown juanto:juanto .ecryptfs

With that you can run again the command:

ecryptfs-mount-private

And now you will get all your data decripted.

2. Change the permission over that directory with command "chmod"

Bye!

Juanto.

---

### Post by kuraykillua on 2010-12-26
I have the exact same problem, and have followed juanto's steps.
However even after changing the owner status of .ecryptfs, running "sudo chown username:username .ecryptfs" it STILL says that I do not own that directory.
For me this happened right after an update, and I'm pretty sure that's what caused it...

---

### Post by juanto on 2010-12-28
If in /home you execute "ls -la", What's on? and also tell us what steps you did.

---

### Post by dubspecial on 2011-03-09
I ran into this same problem on 10.10.

In my case, /home/.ecryptfs/<user>/.Private was owned by some really odd user.  Once I did a chown <user>:<user> /home/.ecryptfs/<user>/.Private I dont longer got the issue with "You do not own that encrypted directory"

---

### Post by galvani on 2011-05-01
Hi guys, I have moved my whole home folder prior to upgrading. After 11.04 installation  had to mount my old home folder to copy data I needed. I had to modify /home.bak/.ecryptfs/jan.bak/.ecryptfs/Private.mnt to point to existing folder I own. That solved my problem.

So Just make sure you are pointing to the correct path in your /home/.ecryptfs/<user name>/.ecryptfs/Private.mnt

---

