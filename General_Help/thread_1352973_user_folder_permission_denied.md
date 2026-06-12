---
title: "user folder permission denied"
date: 2009-12-12
forum: General Help
---

### Post by mahmater on 2009-12-12
Yesterday,I couldn't get into my ubuntu 9.10 desktop. After I enter my login and password all I have is a blank screen with a warning saying: error occured while saving or loading configuration information of evolution-notify-alarm..

 1. is there a way to fix that?
 2. or at least,a way to rescue my data.( I tried live CD,but my user's folder permission denied).

many thanks.

---

### Post by Leppie on 2009-12-12
You could boot into the recovery console, create a new user with "adduser" command, reboot and see if the same happens with the newly created account.

---

### Post by napurist on 2009-12-12
Also, you may have an upgrade failure of some sort.  When booting press the escape key and choose one of the previous kernels.  Let's see if that get's you to the OS.

---

### Post by mahmater on 2009-12-12
thanks for such quick replies.

 1. I booted via previous kernels,still can't get into the desktop.
 2. I already have another user on my desktop reserved for my sister.things run normally with it.but I can't get into my user's folder because of the permission issue.

---

### Post by nothingspecial on 2009-12-12
You need to create an admin user. In recovery mode

```
adduser bob
```

```
adduser bob admin
```

Then use bobs account with sudo to get your stuff.

---

### Post by mahmater on 2009-12-12
> **nothingspecial said:**
> You need to create an admin user. In recovery mode

```
adduser bob
```

```
adduser bob admin
```

Then use bobs account with sudo to get your stuff.

well friend I did what u told me,and things went well. but the problem is how to get into my user's folder "covy" (screenshot1)?

even when I used the command "sudo nautilus" this is what it gave me( screenshot 2).

---

### Post by nothingspecial on 2009-12-12
From bobs account

```
sudo mv /home/username/covy /home/bob/
```

```
sudo chown -R bob:bob ~/covy
```

---

### Post by mahmater on 2009-12-12
> **nothingspecial said:**
> From bobs account

```
sudo mv /home/username/covy /home/bob/
```

```
sudo chown -R bob:bob ~/covy
```

thanks "nothingspecial" for all your help. I feel i'm getting closer now,but still can't get access into covy folder. the same screenshot2 from my previous post. and here's what it also gave me this time (screnshot3). I wonder if that has anything to do with the way I installed 9.10 (I mean encrypted disk).

---

### Post by scouser73 on 2009-12-12
**1** - > sudo -i
**2** - > cd to directory where file is held
**3** - > chown -R username filename

Replace the username with your own, and the filename to the name of the file.

---

### Post by mahmater on 2009-12-12
here's screenshot4.

---

### Post by nothingspecial on 2009-12-12
Ah ha, I didn`t realise it was encrypted. I`ve never done it myself so I don`t know, but I`ll have a look.

Maybe it would be better to fix your original account.

Can you remember what you did before it broke. Also can you login to your original accout from the command line. Press Ctrl Alt F1 and see if you can login.

---

### Post by mahmater on 2009-12-12
very weird indeed. yes now I can successfully log in my original user desktop (covy) but the problem is that it seems as if it is a newly created user (of course the the covy folder is moved to Bob). even firfox cannot load because it missed the user's configuaration details.

---

### Post by nothingspecial on 2009-12-12
If you try moving the covy folder back to covy can you view the contents. You will probably need to rechown it back to covy. (the command I gave you before with covy substituted for bob).

rechown.....? Is that a real word? hmmm......

---

### Post by mahmater on 2009-12-12
attempting to re-chown (copy right is yours) the folder after moving it  here's what it gave me: 

bob@covy-desktop:~$ sudo chown -R covy:covy ~/covy
chown: cannot access `/home/bob/covy': No such file or directory.

---

### Post by Leppie on 2009-12-12
don't use "sudo" in this case, bob owns the folder now.

and maybe it's wise to copy the contents to covy's home first (bob is an admin, right?), then chown.

---

### Post by mahmater on 2009-12-12
I'm afraid I didn't get ur point. now "covy" folder is back into covy user.I logged into covy (the original user) and it's there but it still locked and the permission is with bob. what should I do?

---

### Post by Leppie on 2009-12-12
> **mahmater said:**
> I'm afraid I didn't get ur point. now "covy" folder is back into covy user.I logged into covy (the original user) and it's there but it still locked and the permission is with bob. what should I do?

open a terminal and give the following command:
```
$su bob
```
you will be prompted for bob's password and once provided you have access as bob. then do the chown command.

---

### Post by mahmater on 2009-12-12
now the same old problem: data is encrypted. it seems there is no way.
I appreciate your help "nothingspecial". 5 GB is lost!!!!!

---

### Post by Leppie on 2009-12-12
I found the following:
> Do NOT move ~/.ecryptfs into ~/Private!!! The ~/.ecryptfs directory contains a key signature required to mount ~/Private, and the only valuable data (your key) is already encrypted in that directory. Should you do something silly like this, to recover your data, you will need to manually mount ~/Private as root, and using the unwrapped passphrase. 
sudo mount -t ecryptfs /home/USER/.Private /mnt 
key type: passphrase 

passphrase: whatever you recorded when you ran ecryptfs-setup-private 
key cipher: aes 
key bytes: 16 
plaintext passthrough: no 
mount: yes 
avoid warning in the future: no 
sudo mv /mnt/.ecryptfs /home/USER/ 
sudo umount /mnt

on [this page]("https://wiki.ubuntu.com/EncryptedPrivateDirectory").

so basically as root you would be able to access the files.

---

### Post by nothingspecial on 2009-12-12
I am really sorry, I know nothing of encryption.

There will be a way to solve this. As long as your files still exist, we can get at them.

You will have to excuse me though. I have just been to a live concert. I am a little drunk, and can be of no more service until (late) tommorow morning - my time.

Rest assured though, I have not given up.

---

### Post by mahmater on 2009-12-13
thanks again for all ur services. I should confess I learnt a great deal from you. But I also learnt very valuable lessons:

  1.never encrypt a disk as long as there is no need for that.
  2. If it happened that one encrypted a disk he should keep the passphrase in a secure place,and -if he is very forgetful as I am- tell his wife about it so that she could remind him later.

 Now,nothing special I'm trying to look for the place whre I kept the passphrase immediately after the installation of 9.10. a lot of CDs and four flash disks to check.

have a nice day or night ...who knows what you have there in that part of the world?

---

### Post by Leppie on 2009-12-13
I've never really looked into encryption that much. I suppose it's better to keep your box safe in other ways. Hopefully some day some really good tut on encryption will appear.
It's funny to see there's tons of tuts and howtos on how to set encryption, but I haven't found much on recovery of encrypted filesystems and nothing about switching it off...

---

### Post by nothingspecial on 2009-12-13
I have failed to find an answer your problem yet, but [[COLOR="Magenta"]here[/COLOR]]("https://help.ubuntu.com/community/EncryptedFilesystemHowto") is some interesting reading

I suggest, making a new thread in the general help section entitled "how to recover encrypted file system" or similar, in the hope that someone has an answer. There are many knowlegable people who scan the forum from time to time. You never know. In the meantime I`ll continue looking.

---

### Post by mahmater on 2009-12-17
sorry for not responding these days, I had a terrible asthma fit.now I m recovering.thank you for the suggestion.I'll do that for sure.

---

