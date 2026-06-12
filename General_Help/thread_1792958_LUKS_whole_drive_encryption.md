---
title: "LUKS whole drive encryption"
date: 2011-06-28
forum: General Help
---

### Post by Darris on 2011-06-28
My battery died and now my password doesn't work for my LUKS encryption.

I can't access my hard drive. I'm writing this from a live CD.

---

### Post by Darris on 2011-06-29
> **Darris said:**
> My battery died and now my password doesn't work for my LUKS encryption.

I can't access my hard drive. I'm writing this from a live CD.

At first, I had no idea why I couldn't access it, but I found a single thread from 2007 in which the OP said things happened in exactly the same order as has just happened on my laptop.

But the OP never answered the questions of the fine people who tried to help him/her. 
I tried to post on that thread but it said something about an administrator blocking my ability to do that? Maybe because the thread's too old.

---

### Post by Herman on 2011-06-29
If the files system is okay, you should be easily able to rescue files from an LUKS encrypted file system as long as you know the LUKS password.
You should be able to do so from a Live CD or a USB operating system or some other operating system in the computer.

In the Ubuntu you're working from, you may want 'lvm2' and you'll need to install 'cryptsetup              ',
```
sudo apt-get install lvm2 cryptsetup              
```and I recommend running the following,
```
sudo modprobe dm-crypt
```After that you might see an item in your 'Places' menu, (in the classic desktop), with a label something like XX GB Encrypted. If you click on that label, you should see a dialog asking you to 'Enter a password to unlock the volume'.
After entering the correct password it may give you a message that looks like an error message, but go and look in your 'Places' menu anyway and see if your file system is listed there and if it is there you should be able to open it. 

If that doesn't work then maybe your file system was damaged if the computer shut down too fast when it ran out of battery power. Usually Ubuntu will warn you just before the battery runs out completely and will want to hibernate but sometimes there are reasons why the user wants to keep using the machine for a bit longer to try to finish something important maybe that will only take a few minutes and it might run out of battery completely and shut down improperly. If that happed then you may need a file system check to fix the file system first. I already have a post in this forum about how to run file system check in a LUKS Encrypted file system here, **     [[SOLVED] Restore a backup on dm-crypted LVM]("http://ubuntuforums.org/showthread.php?t=1777611").** See post #8.

After the file system check you may be able to boot it or at least you should be able to mount it.

If that doesn't work either, try the command line way, 'ls -al /dev/mapper' to see if it's listed. 
```
ls -al /dev/mapper
```If not do,```
cryptsetup luksOpen /dev/sdd1 sdd1
```To mount,
```
sudo mkdir /mnt/data
``````
sudo mount /dev/mapper/sdd1 /mnt/data
```

---

### Post by Darris on 2011-06-29
> **Herman said:**
> If the files system is okay, you should be easily able to rescue files from an LUKS encrypted file system as long as you know the LUKS password.
You should be able to do so from a Live CD or a USB operating system or some other operating system in the computer.

In the Ubuntu you're working from, you may want 'lvm2' and you'll need to install 'cryptsetup              ',
```
sudo apt-get install lvm2 cryptsetup              
```and I recommend running the following,
```
sudo modprobe dm-crypt
```After that you might see an item in your 'Places' menu, (in the classic desktop), with a label something like XX GB Encrypted. If you click on that label, you should see a dialog asking you to 'Enter a password to unlock the volume'.
After entering the correct password it may give you a message that looks like an error message, but go and look in your 'Places' menu anyway and see if your file system is listed there and if it is there you should be able to open it. 

If that doesn't work then maybe your file system was damaged if the computer shut down too fast when it ran out of battery power. Usually Ubuntu will warn you just before the battery runs out completely and will want to hibernate but sometimes there are reasons why the user wants to keep using the machine for a bit longer to try to finish something important maybe that will only take a few minutes and it might run out of battery completely and shut down improperly. If that happed then you may need a file system check to fix the file system first. I already have a post in this forum about how to run file system check in a LUKS Encrypted file system here, **     [[SOLVED] Restore a backup on dm-crypted LVM]("http://ubuntuforums.org/showthread.php?t=1777611").** See post #8.

After the file system check you may be able to boot it or at least you should be able to mount it.

If that doesn't work either, try the command line way, 'ls -al /dev/mapper' to see if it's listed. 
```
ls -al /dev/mapper
```If not do,```
cryptsetup luksOpen /dev/sdd1 sdd1
```To mount,
```
sudo mkdir /mnt/data
``````
sudo mount /dev/mapper/sdd1 /mnt/data
```

Thank you, this gives me a lot of hope. I will try it at my earliest convenience.

---

### Post by Darris on 2011-06-30
it died :(
but your solution helped me to learn that it's dead
so, do I mark this as solved?

---

### Post by Herman on 2011-06-30
Oh, okay, I'm sorry to hear (or read) that. 
I don't know if it's better to mark the thread solved or just leave it unsolved. Leave it unsolved I guess, because we didn't really score a win this time.

---

