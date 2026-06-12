---
title: "Encrypted Home Folder"
date: 2010-08-04
forum: General Help
---

### Post by MetaDark on 2010-08-04
Well for some reason my laptop went crazy, my Windows 7 partition became corrupted and my Ubuntu (Lucid Netbook Remix) partition just didn't start up the Poulsbo graphic drivers (which may be my fault when I first tried to get poulsbo working).

Well I made a new partition with Lucid Netbook Remix and I went to try to transfer my files from my old partition to my new one and I realized that I saved the Passphrase for my old partition in the documents folder.

So I typed "sudo nautilus" in the terminal to try to access my home folder and I stumble upon a desktop launcher called "Access-Your-Private-Data". I ran it and entered my login passphrase, it didn't do anything but close, I tried refreshing nautilus but it still showed the desktop launcher and its README. I tried entering the wrong password and it gave me the error;

```
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
ERROR: Your passphrase is incorrect
```

and it just prompted me for my password again. So why did nothing happen when it was typed in correctly?

Btw my old Ubuntu partition launches in recovery mode but I have no idea how I would go about to fix it.

So my only two options are to fix my old partition or to somehow gain access to my encrypted home folder without a passphrase.

---

### Post by MetaDark on 2010-08-05
I thought I recovered my passphrase but sadly it was only for my new Ubuntu partition :(

---

### Post by MetaDark on 2010-08-05
If you have your passphrase for your old partition you can follow these steps.

```
sudo -i
```
 
and just CD back with this command:

```
cd /**MOUNT_POINT_OF_ENCRYPTED_DRIVE**/home/**YOUR_USERNAME**
```

After that type in

```
ecryptfs-add-passphrase --fnek
```

Once you enter in your passphrase, copy the number inside the brackets on the last line outputted and just keep it somewhere because it is needed for the last step.

Now type in the following to start mounting the encrypted data to a new folder were it will be decrypted:

```
mount -t ecryptfs .Private Private
```

It will ask for your passphrase, type/copy it in and hit enter

It then will give you a list of options for a cipher, just type in **aes** and the hit enter.

It will then ask how many key bytes you want to use, type in **16** and hit enter.

It will then ask if you want to enable plaintext passthrough type **n** and hit enter.

It will then ask if you want to enable filename encryption type **y** and hit enter.

Now it will ask you for your filename encryption key signature (the numbers you copied earlier). Paste it in and hit enter.


You should now have all your files decrypted into a folder called Private :D

If any yes/no questions appear that were not listed just type **yes**.

---

### Post by uylug on 2010-08-05
Thanks for posting how you fixed it!

---

