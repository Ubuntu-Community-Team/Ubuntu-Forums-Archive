---
title: "Difficult Question"
date: 2012-01-14
forum: General Help
---

### Post by giantpc on 2012-01-14
Hi,

I used the "Encrypted Installation" feature of a Ubuntu installation on my second HD. I'm now trying to view the data on my second HD to see how well it is encrypted, what the data looks like (@&^@$&@%$&FGDSFY#&, for example), and if there are any files and folder names visible when looking at the data on my second HD.

The problem is that I cannot find a utility that allows me to view the data on the encrypted HD -- I know the data should look something like "aW*#$*&(^RYDFGDEFU#R^" but that is alright, I still want to view the data on the second HD.

A Ubuntu Live CD requires that the second HD be mounted and for me to type in the encryption password to decrypt the HD before mounting the HD, and that defeats the whole purpose; I don't want to decrypt the system and mount it and THEN view it. I'm trying to view it BEFORE mounting the system and BEFORE decrypting the sytem.

I want to view THE ENCRYPTED DATA ON MY SECOND HD to see what it looks like and to see if there are any files or folder names visible.

Does anybody know what utility can accomplish this simple task?

---

### Post by bluexrider on 2012-01-14
Wouldn't that be defeated of the encryption? 

This may help [https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

---

### Post by giantpc on 2012-01-14
> **bluexrider said:**
> Wouldn't that be defeated of the encryption? 

This may help [https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

No, I want to view the data in its encrypted form such as "*#^FEFUGSFGD&#R#E@"

Because I don't buy into the fact that the ubuntu installation encrypts everything. How do I know that the new files I add to my home directory are encrypted for sure? What about new programs that I install? How do I know that they are encrypted?

The only way to find out is to view the whole HD and see what is encrypted and what is not encrypted. I bet that all of my newly installed programs are sitting right there unencrypted and that all the new files that I added to my home directory (Which is set to encrypted) are not encrypted.

I won't know for sure unless I use a utility to actually view the data.

(I know the data should show up as encrypted ie "2hfu^$8DFG")

---

### Post by MG&amp;TL on 2012-01-14
I would do it via command-line, by booting a disk and then mounting the filesystem. I have no idea if I need to give a pass for that, though, as I don't encrypt.

You could do it like this:

```
sudo mkdir /mnt/encryptfs
sudo mount /dev/<theencrpytedpartition> /mnt/encryptfs
cd /mnt/encryptfs/home/
```

replace <theencrpytedpartition> with the partition reference, probably something like sda1.

As always, be careful with sudo.

And if you don't buy it, why would they bother coding the button to put it on the installer? Coding takes effort,y'know. :P It will probably unencode your hard drive when you supply your password, and reencrypt when you shutdown.

---

### Post by giantpc on 2012-01-14
> **MG&TL said:**
> I would do it via command-line, by booting a disk and then mounting the filesystem. I have no idea if I need to give a pass for that, though, as I don't encrypt.

You could do it like this:

```
sudo mkdir /mnt/encryptfs
sudo mount /dev/<theencrpytedpartition> /mnt/encryptfs
cd /mnt/encryptfs/home/
```

replace <theencrpytedpartition> with the partition reference, probably something like sda1.

As always, be careful with sudo.

And if you don't buy it, why would they bother coding the button to put it on the installer? Coding takes effort,y'know. :P

I can't mount the filesystem without the passphrase because it was an encrypted installation...and if I mount the encrypted filesystem then the data is automatically supposed to be decrypted, which defeats the whole purpose.

I need to view the data on my second HD without mounting the file system. I know that most of it will show up as encrypted such as "@$&^&FGDFY" but I believe some will be left unencrypted.

---

### Post by MG&amp;TL on 2012-01-14
> **giantpc said:**
> I can't mount the filesystem without the passphrase because it was an encrypted installation...and if I mount the encrypted filesystem then the data is automatically supposed to be decrypted, which defeats the whole purpose.

I need to view the data on my second HD without mounting the file system. I know that most of it will show up as encrypted such as "@$&^&FGDFY" but I believe some will be left unencrypted.

I think to read an fs you need to mount...so that's self-defeating?

I hesitate to say this, but do you have a non-*nix based OS on your PC? I did use ext2explore on windows at one point...

---

### Post by Dangertux on 2012-01-14
> **giantpc said:**
> 
Because I don't buy into the fact that the ubuntu installation encrypts everything. How do I know that the new files I add to my home directory are encrypted for sure? What about new programs that I install? How do I know that they are encrypted?




Because the data is unencrypted at mount time and re-encrypted at unmount. Thus anything that was added in the interim will be encrypted. There is no other choice, the entire logical volume is encrypted, it can't pick and choose inodes on the volume that it doesn't want to encrypt. It doesn't work that way.

As for reading it in its encrypted form, mount it in another OS, or a drive block. Problem solved

---

### Post by giantpc on 2012-01-14
> **Dangertux said:**
> Because the data is unencrypted at mount time and re-encrypted at unmount. Thus anything that was added in the interim will be encrypted. There is no other choice, the entire logical volume is encrypted, it can't pick and choose inodes on the volume that it doesn't want to encrypt. It doesn't work that way.

As for reading it in its encrypted form, mount it in another OS, or a drive block. Problem solved


So if I add 15GB of new files to my home folder, and then reboot, it should take a few minutes for ubuntu to close down and reboot, right? That doesn't happen. So how in the heck is ubuntu encrypting my 15GB of new data at unmount (reboot) in less than 30 seconds? I never see any difference in the time it takes to unmount, or reboot and boot back up.

How does ubuntu encrypt and decrypt over 15gb of data in under 30 seconds? It would take me over 5 minutes to transfer 15GB of data from one drive to another.

If I added 50GB of new data to my home directory right now, why do I not see the difference in time when I do Log-out or Reboot?

---

### Post by Cheesemill on 2012-01-14
The data gets encrypted when it is first written to the disk, not when it is shut down.
This is why there is a disk performance drop between encrypted vs unencrypted volumes.

When you shut down, the encryption key is removed from memory therefore 'locking' the volume.

---

### Post by giantpc on 2012-01-14
> **Cheesemill said:**
> The data gets encrypted when it is first written to the disk, not when it is shut down.

When you shut down the encryption key is removed from memory therefore 'locking' the volume.

That isn't what Dangertux said. Dangertux said the data gets encrypted at unmount which is reboot bascially.

---

### Post by Serpher on 2012-01-14
Look up the dd command. You can copy your hardrive bit for bit into a file.

```
dd if=/dev/<parition> of=test.img bs=1024k count=10
```

That should copy the first 10MB of your hardrive. You can then look at everything bit for bit with commands like less and more.

---

### Post by Cheesemill on 2012-01-14
> **giantpc said:**
> That isn't what Dangertux said. Dangertux said the data gets encrypted at unmount which is reboot bascially.

That's a common way of looking at it but it isn't stictly how it works.

---

### Post by bluexrider on 2012-01-14
**How does Linux encrypt my data?**

 Traditionally  in Linux a beefed-up loopback device was used to mount a file. This  loopback device then did de-/encrypt the data passing through to it.  There were several different and incompatible versions of these loopback  encryption engines, most supporting only one crypto algorithm. 
With  the Linux 2.6 kernel the cryptoloop system was deprecated and might get  dropped from the mainline kernels altogether at some point in the 2.6  development cycle. Its functionality is incorporated into the [DeviceMapper]("https://help.ubuntu.com/community/DeviceMapper"), a generic framework used to map one blockdevice into another. Apart from encryption this [DeviceMapper]("https://help.ubuntu.com/community/DeviceMapper") is the foundation of LVM, software RAIDs and offers additional features like doing snapshots of filesystems. 
 
**So how does DeviceMapper work?**

 The [DeviceMapper]("https://help.ubuntu.com/community/DeviceMapper") is a filter, processing data passed in from a virtual blockdevice it provides, before passing it on to another blockdevice. 
When used to encrypt data the [DeviceMapper]("https://help.ubuntu.com/community/DeviceMapper")  is used to create a new blockdevice in /dev/mapper/. This virtual  device can be used like any other blockdevice you have on your system  (/dev/hdaX, etc). All data passed to this device is encrypted by the [DeviceMapper]("https://help.ubuntu.com/community/DeviceMapper")  (or better the dm-crypt module of it) using a symmetric encryption  algorithm like AES. The encrypted data is then written to another  blockdevice that does actually store the data.


This may help [https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

---

### Post by Dangertux on 2012-01-14
It's important to understand the explanation I'm trying to give is of which times the data itself is plaintext readable. Meaning. When it can be accessed as plain text. Which is pretty much any time the lvm is mounted and the passphrase has been supplied.

I am not talking about the technical aspect with how the AES (or whatever you use) algorithm is applied.

---

