---
title: "Recover Encrypted Home Folder From Live CD"
date: 2010-10-15
forum: General Help
---

### Post by Astnya on 2010-10-15
For a while now the Ubuntu installer has offered an option to encrypt your home directory, and decrypt it at login. Security-wise, this is a nice tool, especially for laptops and other portable computers that have a higher risk of theft, or simply for computers with a higher risk of unauthorized access. However, what if your system suffers catastrophic failure and you find yourself unable to boot Ubuntu or log into your account? Depending on what you have on the computer, it might be critical that you recover your files before you wipe your hard drive and reinstall your operating system.

Of course, if your home directory is encrypted, you can't just grab whatever you want from your hard drive. There is a process for decrypting a secure home directory, but discovering it involved a bit of Googling and around an hour of consulting someone in IRC. So I wanted to write this in case someone else had this problem for real.

Anyway. Obviously, you need an Ubuntu live CD, or a USB drive from which you can boot Ubuntu. You also need the decryption passphrase for your encrypted home folder. Hopefully you wrote it down when Ubuntu asked you to generate it the first time you logged into your new system. If you don't have it, though, there's a way to recover it (included in this post at the bottom).

Steps:

1. Boot your computer from your live CD or USB drive.

2. Mount the hard drive or partition on which the encrypted home folder is stored. You can do this by browsing the Places menu; it will likely just be something like "100 GB Filesystem". 

3. Open a terminal window (Applications > Accessories > Terminal).

4. Run the following:
```
sudo ecryptfs-add-passphrase --fnek
```
When it asks you for your passphrase, enter the decryption passphrase for your home directory. You will get two lines that resemble this:
```
Inserted auth tok with sig [9986ad986f986af7] into the user session keyring 
Inserted auth tok with sig [**76a9f69af69a86fa**] into the user session keyring
```
Copy the second string of characters in the brackets (yours will of course be different from the example I've provided) and make a note of it. You'll need it to decrypt the names of your files. (Note: In a terminal window, Ctrl+Shift+C is copy and Ctrl+Shift+V is paste.)

5. Create a folder on your desktop to use as a mount point:
```
mkdir Desktop/Mount
```

6. Now it's time to mount and decrypt your home folder. The steps for this are provided below. For sake of reference, by the time you're finished, the terminal window should look a lot like this:
```
ubuntu@ubuntu:~$ sudo mount -t ecryptfs /media/*04b67fb1-aafd-4082-aebc-493c509bdbe1*/home/.ecryptfs/**username**/.Private Desktop/Mount
Passphrase:
Select cipher:
 1) aes:
 2) blowfish: 
 3) des3_ede:
 4) twofish:
 5) cast6:
 6) cast5:
Selection [aes]:
Select key byes:
 1) 16
 2) 32
 3) 24
Selection [16]:
Enable plaintext passthrough (y/n) [n]:
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [9986ad986f986af7]: **76a9f69af69a86fa**
Attempting to mount with the following options:
 ecryptfs_unlink_sigs
 ecryptfs_fnek_sig=76a9f69af69a86fa
 ecryptfs_key_bytes=16
 ecryptfs_cipher=aes
 ecryptfs_sig=9986ad986f986af7
Mounted eCryptfs
ubuntu@ubuntu:~$
``` 
First, you enter the command to decrypt and mount the folder, hence the 'sudo mount -t...' command. The italicized string of characters is different for everyone; just hit Tab after typing '/media/' and it will probably autocomplete. Replace the bolded **username** value with the name of your home folder (for example, /home/astnya/ for me). The last part of the command tells it to mount the decrypted folder to the directory you created on the desktop.

Enter your decryption passphrase when prompted to do so, then simply hit Enter in the 'Select cipher' section to choose the default, aes. Do the same for 'key bytes' to choose 16, and the same for 'Enable plaintext passthrough' to choose not to enable it. However, you do want to enable filesystem encryption, so when asked, hit y. On the next line, enter the shorter character string you made a note of earlier; this is used to decrypt the names of your files and folders, which are encrypted separately from the files and folders themselves.

After that, the process should successfully complete, and you'll be able to rescue your files through the Mount folder on your desktop. But there's one more step to be done. Since you mounted the folder with superuser permissions, you must have those permissions to view its contents:
```
sudo nautilus
```
This will bring up a file browser window. In that window, navigate to the folder (press Ctrl+L and type in '/home/ubuntu/Desktop/Mount'). You should now be able to view your home folder, and to modify or copy its contents as necessary, as long as you keep that window open.

If you find that you need your decryption passphrase, you can run this to generate it:
```
ecryptfs-unwrap-passphrase /media/*04b67fb1-aafd-4082-aebc-493c509bdbe1*/home/.ecryptfs/**username**/.ecryptfs/wrapped-passphrase
```
Again, the italicized characters and **username** will differ for you. Enter your login password for your account on the computer into the prompt, and it will give you the decryption passphrase for your home folder.

Credit goes to Aemaeth in #ubuntu and the authors of [this page](https://help.ubuntu.com/community/EncryptedPrivateDirectory) for the help in figuring this out. Hopefully this guide was written in enough of a noob-friendly fashion that it's not confusing for people new to Ubuntu or Linux. =)

---

### Post by blondyman1503 on 2010-10-30
so im all good up until step 6.
this is what my terminal looks like: 
```
root@ubuntu:~# sudo mount -t ecryptfs /media/7a5b2866-d689-45db-9ce4-3c5ac19109e4-aafd-4082-aebc-493c509bdbe1/home/.ecryptfs/nick/.Private /root/mount
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [7b21373f02b63b3d]: df7434469798a319
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=df7434469798a319
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=7b21373f02b63b3d
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
root@ubuntu:~# 

```
It says that there is no file or folder named "eCryptfs"...so now what?

---

### Post by itkahuna on 2010-11-24
Worked like a charm, thank you!

---

### Post by ario on 2011-01-19
I read a lot of forums and created this reply just in case it may become useful to others.
To recover your files you can bring up system with a live cd and use either of methods below:
Method 1 (Prefered):
[INDENT]    find your real home folder in /home/.private/USERNAME
    There go to .ecryptfs folder. Here you can see settings files needed to recover your home folder. If you can not see these files, then God help you!
    You must have a passphrase first. This is different from the one you used to login to your PC. In a terminal enter:
```
        ecryptfs-unwrap-passphrase /home/.private/USERNAME/.ecryptfs/wrapped-passphrase
```
    Then enter your login password. It will show you an important momble jumble word! For now we call it **secret1**.
    Then find the file Private.sig there. If you cannot find that file (Why?) you can run this:
```
        ecryptfs-add-passphrase --fnek
```
When it asked you, enter **secret1**. Consider momble jumble letters from second line of either Private.sig file or output of this command as **secret2**. We will use it later.
    Then run:
```
mount -t ecryptfs /home/.private/USERNAME/.Private /mnt
```
    Enter **secret1** as passphrase. Answer all questions by pressing enter EXCEPT:
>         Answer "Enable filename encryption " with y
        Answer "Filename encryption key (FNEK)" with **secret2**
    Here we are. Now go to /mnt and see your files. If you still see momble jumble worlds, then you may forget something or..., I don't know!
    Good wishes:)
    Aario
    Main and primary source: [http://ubuntuforums.org/showpost.php?p=9975523&postcount=1](http://ubuntuforums.org/showpost.php?p=9975523&postcount=1)[/INDENT]
Method 2:
>     You can do this from a terminal with:
    ubuntu@ubuntu$ sudo mount /dev/sda1 /mnt
    ubuntu@ubuntu$ sudo mount -o bind /dev /mnt/dev
    ubuntu@ubuntu$ sudo mount -o bind /dev/shm /mnt/dev/shm
    ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc
    ubuntu@ubuntu$ sudo mount -o bind /sys /mnt/sys
    ubuntu@ubuntu$ sudo chroot /mnt
    root@ubuntu$ su - kirkland
    kirkland@ubuntu$ ecryptfs-mount-private
    Enter your login passphrase:
    Warning: Using default salt value (undefined in ~/.ecryptfsrc)
    Inserted auth tok with sig [xxx] into the user session keyring
    kirkland@ubuntu$ cd $HOME
    kirkland@ubuntu$ ls -alF
    ...
    kirkland@ubuntu$ cat .profile
    ...
    The above process assumes that your ~/.ecryptfs/wrapped-passphrase file is available on this system. If you're using 2-factor authentication and storing this elsewhere, you might need to perform an additional mount and symbolic link to make this file available.

    Alternatively, if you're trying to recover data, and you've recorded your mount passphrase properly, you would use
    kirkland@ubuntu$ ecryptfs-add-passphrase --fnek
    just before the ecryptfs-mount-private bit, to manually enter your passphrase (rather than pulling it from ~/.ecryptfs/wrapped-passphrase).

    Notes:
    /dev/sda1 is the device serving my $HOME/.Private
    kirkland is my username, yours will likely be different ;-)
    Binding mounting /sys and /proc are critical -- ecryptfs needs access to kernel information shared there
    The dash in "su - " is important -- don't forget it!
    Source: [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

---

### Post by DancingGeek on 2011-02-21
> **blondyman1503 said:**
> so im all good up until step 6.
this is what my terminal looks like: 
```
<snip>
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
root@ubuntu:~# 

```It says that there is no file or folder named "eCryptfs"...so now what?

I got this error and was able to fix it by typing the full address of the directory I wanted to mount, i.e. rather than using Desktop/Mount in the first workthrough given, I used /home/ubuntu/Desktop/Mount (I'm using the live CD and so am logged in as user ubuntu).

So for me the error "No such file or directory" referred to where I was trying to mount my partition.

Otherwise this post helped a lot, but there is also a walkthrough of this on the ubuntu EncryptedPrivateDirectory page [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Long%20way](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Long%20way)

It isn't as easy to follow, not so newbie friendly, but it helped me work out was I was doing wrong.

---

### Post by airtacable on 2011-04-30
Thanks very much. This worked perfectly.

airtacable

---

### Post by maiko29 on 2011-05-05
> **Astnya said:**
> 
2. Mount the hard drive or partition on which the encrypted home folder is stored. You can do this by browsing the Places menu; it will likely just be something like "100 GB Filesystem". 



I can't do that. I have in my Places menu:
255MB Filesystem
164GB Encrypted
43GB Encrypted
37GB Encrypted

If i click any of them, it asks me to insert:
> Enter a password to unlock the volume

The device "165GB Hard Disk contains encrypted data on ppartition 5."

> Enter a password to unlock the volume

The device "80GB Hard Disk contains encrypted data on ppartition 1."

> Enter a password to unlock the volume

The device "80GB Hard Disk contains encrypted data on ppartition 2."

---

### Post by edsonski on 2011-08-05
Hi. Noob here. I think i have the same problem. Does this work for 11.04?

---

### Post by edsonski on 2011-08-05
Oh and you also forgot to include on how to recover passphrase. Please, please reply. :)

---

### Post by MikeVaughanG on 2011-10-28
Dont know if anyone's still interested but...

```

Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [ef1273aeb9dbeaba]: 853c8a4c5d62cdb1                
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=853c8a4c5d62cdb1
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=ef1273aeb9dbeaba
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [ef1273aeb9dbeaba] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
ubuntu@ubuntu:~$ sudo nautilus

```

As you can see, there was an error
But,  it worked just fine. 

Thanks for the post. 

Mike

---

### Post by awtovey on 2011-11-03
I'm a total newbie so bear with me...

I followed up to this bit

"The italicized string of characters is different for everyone; just hit  Tab after typing '/media/' and it will probably autocomplete. Replace  the bolded **username** value with the name of your home folder (for example, /home/astnya/ for me)"

Firstly, hitting tab does nothing at all. Thus I dont know how to generate my own string of characters. Using the ones you list appears to not work!

Secondly, I'm uncertain about my username. if I'm andrew, do I type in [FONT=monospace]

[/FONT]ecryptfs/**andrew**/.Private

or

ecryptfs/**/andrew**/.Private

or

ecryptfs/**home/andrew**/.Private

or

ecryptfs/**/home/andrew/**/.Private It might seem a stupid question but I really dont know. From your instructions it would seem like the last option is correct...

???


Turns out I dont have the passphrase either, so will need to run the following

ecryptfs-unwrap-passphrase /media/*04b67fb1-aafd-4082-aebc-493c509bdbe1*/home/.ecryptfs/**username**/.ecryptfs/wrapped-passphrase

obviously I need the same info I highlighted above in order to do this. Can you help?

---

### Post by lunatico on 2012-05-11
Just followed steps from post #1 on Linux Mint 12 and it works perfectly.

Thanks!

---

### Post by xirix404 on 2012-06-25
thank you so much Astnya 
Fantastic manuel for a newbie

---

### Post by oldos2er on 2012-06-25
Old thread closed.

---

