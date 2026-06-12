---
title: "back up with encripted home directory?"
date: 2010-12-29
forum: General Help
---

### Post by niai on 2010-12-29
long time reader and this is the 1st time i have ever had to ask any thing

i got a new hdd and installed it in my laptop, i cloned my partitions but i ended up with a misaligned drive. i backed it up to a usb drive with the idea of just copying every thing back to the new drive when fix, that didnt work. i had made a back up of my home directory with out encryption but i was stupid and accidentally deleted it. now i am out of ideas i have tryed mounting my home directory in a live cd using 

```
Recovery of an Encrypted Home Directory is possible from an Ubuntu 9.10 LiveCD.

Mount the disk partition containing the Encrypted Home Directory:

ubuntu@ubuntu$ sudo mount /dev/sda1 /mnt
Establish a proper chroot environment:

ubuntu@ubuntu$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu$ sudo mount -o bind /dev/shm /mnt/dev/shm
ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu$ sudo chroot /mnt
Become the user whose data needs recovery (i.e. &#8220;foo&#8221;) and manually add the necessary mount passphrase to the kernel session keyring:

root@ubuntu$ su &#8211; foo
foo@ubuntu$ ecryptfs-add-passphrase --fnek
Passphrase:
<Enter the recorded passphrase>
Mount the encrypted directory and then access the data:

foo@ubuntu$ ecryptfs-mount-private
foo@ubuntu$ cd $HOME
foo@ubuntu$ ls -alF
```but i do not know my pass phrase, is there any thing i can do to get my data back?

---

### Post by vanadium on 2010-12-29
The point of encryption is that the data are safeguarded and accessible only to authorized people. I guess that it will be extremely difficult to recover data from an encrypted volume without the password.

---

### Post by noah++ on 2010-12-29
This is basically the definition of secure encryption: There is no easier way to decrypt the data than to guess the password. That's called breaking the encryption by brute force. With modern processing power, if the password is only a few characters long, a brute force crack can be achieved within a reasonable time frame. If it's long enough, though, there is no hope of cracking the password within a single lifetime.

The encryption Ubuntu uses to encrypt your home directory is pretty much that secure. So if you are serious about recovering your data, try harder to recall the password, or look into a program that can make a brute force attempt for you.

---

### Post by niai on 2011-01-02
i dodnt know i had reply's to this post and i had my password just not the encryption key.

but i have solved it now using 

```
If your user account name is "user" 
 
1) sudo ecryptfs-unwrap-passphrase path/to/home/.ecryptfs/user/.ecryptfs/wrapped-passphrase 
 
Enter your account password for the user account, this will then display the encryption key, take a note of this key, if the user account password is wrong you won't be able to retrieve the key. 
 
2)sudo ecryptfs-add-passphrase --fnek 
 
Enter the key you retrieved in step 1. This will insert two auth tok with sig. Take a note of the second key. 
 
3) sudo mount -t ecryptfs path/to/home/.ecryptfs/user/.Private /path/where/you/want/to/mount 
 
 
Enter your key (Noted in step one) 
Select: aes (use the aes cipher) 
Select: 16 (use a 16 byte key) 
Enable plaintext passthrough: n 
Enable filename encryption: y ) 
Filename Encryption Key (FNEK) Signature: (Enter the key noted in step 2) 
Since you are using superuser privileges instead of your regular user account, you may get a warning that you might have entered the passphrase wrong, even if you didn't. Continue the mount operation and don't save the key if it asks. 
 
Assuming you entered your key correctly, you should be able to temporarily access your data at /home/user/Private
```

---

### Post by vanadium on 2011-01-02
> **niai said:**
> ...but i do not know my pass phrase, is there any thing i can do to get my data back?
This is what you told in your first post, so this is what we believed.

---

### Post by niai on 2011-01-02
that was because > foo@ubuntu$ ecryptfs-add-passphrase --fnek
Passphrase:
<Enter the recorded passphrase>
was asking for the passphrase (the key that it uses to encrypt the drive), so i was calling it the same as they were its a bit confusing they use passphrase for the encription key and for your password.

thanks for trying to help though and just incase you think i am being ungrateful i am not.

---

### Post by vanadium on 2011-01-04
No offence, I was just indicating that your information was contradictory. If you have the password of the encrypted volume indeed, then it is only a matter to know how you can mount it indeed, and it should work. I see {solved] in some thread titles. Does this mean you succeeded?

---

