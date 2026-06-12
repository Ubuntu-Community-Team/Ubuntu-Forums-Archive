---
title: "NTFS automount and symbolic link question"
date: 2010-01-02
forum: General Help
---

### Post by Darth_tater on 2010-01-02
Hey all! 

I just put ubuntu on my laptop and i have to say 9.10 is very, very nice!  so nice, that ive decided i want to start using it full time!

Before i can do this though, i need to know how i can do the following:

1) auto mount my windows partition (when i do this now, i am prompted to enter my password...)

2) set up a symbolic link so that any time a certain progrm (pidgin) tries to write to ~/.purple it will be automatically written to /mount/WindowsPartition/Documents and settings /... /.purple/

The reason for this is that i rely on windows live sync to keep my IM settings / plugins / logs in sync across the multiple OS's on my desktop and laptop.  Since WLS wont run in linux, and the other alternatives all suck (no, dropbox is not an alternative! Not until i can specify *multiple* folders to be kept in sync!) i have to rely on WLS.  With the setup above, i think that any changes made in linux or windows will be kept in sync since i will be semi regularly booting into windows (at least once a day to perform the sync...)

PS: does anybody know of an evernote compatible program for linux?

---

### Post by SuperSonic4 on 2010-01-02
> **Darth_tater said:**
> Hey all! 

I just put ubuntu on my laptop and i have to say 9.10 is very, very nice!  so nice, that ive decided i want to start using it full time!

Before i can do this though, i need to know how i can do the following:

1) auto mount my windows partition (when i do this now, i am prompted to enter my password...)

2) set up a symbolic link so that any time a certain progrm (pidgin) tries to write to ~/.purple it will be automatically written to /mount/WindowsPartition/Documents and settings /... /.purple/

The reason for this is that i rely on windows live sync to keep my IM settings / plugins / logs in sync across the multiple OS's on my desktop and laptop.  Since WLS wont run in linux, and the other alternatives all suck (no, dropbox is not an alternative! Not until i can specify *multiple* folders to be kept in sync!) i have to rely on WLS.  With the setup above, i think that any changes made in linux or windows will be kept in sync since i will be semi regularly booting into windows (at least once a day to perform the sync...)

PS: does anybody know of an evernote compatible program for linux?

0) Ensure ntfs-3g is install ```
sudo apt-get install ntfs-3g
```

1a) It would be best to edit your fstab to include the windows partition. I will assume it's /dev/sda2 but use your actual number (you find out with ```
sudo fdisk -l
```) I've called it Windows but again take your pick

First create the windows partition mount point: ```
sudo mkdir /mnt/Windows
```

Open fstab (as root) with the following

```
gksu gedit /etc/fstab
```

Add the following line

```
/dev/sda2   /mnt/Windows  ntfs-3g  defaults 0 0
```

save and exit gedit and mount either with a reboot or ```
sudo mount -a
```

To give your user permission for all subfolders and files (but not /mnt/Windows itself) then ```
sudo chown -Rv user:user /mnt/Windows/*
```

(where user is your username)

1b) Install ntfs-config (from the repos?) ```
sudo apt-get install ntfs-config
```

Run ntfs-config as root ```
gksu ntfs-config
``` and follow on-screen instructions

[COLOR="Green"]*note: 1b is easier but you get a better idea of how fstab and linux works with 1a. As usual in linux - it's your choice :)*[/COLOR]


----------------------------------------------------------

2) Doesn't pidgin let you change the directory of where it stores stuff? A symlink would be ```
ln -s ~/.purple /mnt/Windows/Documents\ and\ settings /... /.purple/
```

note: the \ character tells the shell to treat the following character as a literal character, if you put a space it would assume multi-symlinks. When doing this tab completion is your friend - type in the first few characters and hit the tab key

note 2: I don't know if symlinks work in that way, it might be better to set up rsync to copy it on shutdown or use cp whenever you want ```
cp -R ~/.purple /mnt/Windows/Documents\ and\ settings /... /.purple/
```

---

### Post by Leppie on 2010-01-02
Welcome to the community :)

> **Darth_tater said:**
> 1) auto mount my windows partition (when i do this now, i am prompted to enter my password...)
Karmic has the ntfs-3g module as default ntfs module, which provides excellent ntfs support. Install ntfs-config:
```
$sudo apt-get install ntfs-config
```
ntfs-config will set the configurations so your windows partitions can be mounted on next boot.

> **Darth_tater said:**
> 2) set up a symbolic link so that any time a certain progrm (pidgin) tries to write to ~/.purple it will be automatically written to /mount/WindowsPartition/Documents and settings /... /.purple/
you can create symbolic links by using "ln -s":
```
$ln -s /mount/WindowsPartition/Documents\ and\ settings/.../.purple/ ~/.purple
```
but i believe that the target cannot be something already existing.

---

### Post by Darth_tater on 2010-01-02
> **Leppie said:**
> Welcome to the community :)

hahah, thanks.  I havent been here in a month -  its good to be welcomed back.

Ill look into creating the symbolic link once i get back to my computer (posting from my blackberry now...)... if you are correct in saying that the target *cann0t* be pre exisiting then this will really throw a wrench into my plans.

else, i think this will work quite well.

And thanks for the help/advice w/ the ntfs stuff... i know how to make the fstab entry, but what i needed was a way to make the partition auto mount at boot and it looks like both of you have given me what i need!

-- Ill mark this as resolved in a few hours once i get to implement --

---

### Post by Darth_tater on 2010-01-02
> **SuperSonic4 said:**
> 

2) Doesn't pidgin let you change the directory of where it stores stuff? 


Not that i know of.  If this is in fact true, then please tell me more!  This would be even easier!

---

### Post by SuperSonic4 on 2010-01-02
> **Darth_tater said:**
> Not that i know of.  If this is in fact true, then please tell me more!  This would be even easier!

Can't I'm afraid, I use KMess instead of pidgin but a lot of programs seem to allow it

---

### Post by Leppie on 2010-01-02
> **Darth_tater said:**
> hahah, thanks.  I havent been here in a month -  its good to be welcomed back.
lol, had not seen that... sorry...  :)

> **Darth_tater said:**
> Ill look into creating the symbolic link once i get back to my computer (posting from my blackberry now...)... if you are correct in saying that the target *cann0t* be pre exisiting then this will really throw a wrench into my plans.
i just tested this and unfortunately it's true.
try setting it in pidgin ;)

---

### Post by Darth_tater on 2010-01-02
> **SuperSonic4 said:**
> Can't I'm afraid, I use KMess instead of pidgin but a lot of programs seem to allow it

Ah, yeah i know that is is a common feature on other IM clients... but Pidgin doesnt support this AFAIK.

---

### Post by Darth_tater on 2010-01-02
> **SuperSonic4 said:**
> 
note 2: I don't know if symlinks work in that way, it might be better to set up rsync to copy it on shutdown or use cp whenever you want ```
cp -R ~/.purple /mnt/Windows/Documents\ and\ settings /... /.purple/
```


Well, how can i make it so that when any application tries to write to ~/.purple it will seamlessly transition to /Windows/Docs and settings.../.pruple

isint that the point of a system link?

---

### Post by Leppie on 2010-01-02
what you could do is try to copy the data present in ~/.purple to the windows .purple folder, then delete the ~/.purple folder and create the symlink.
you may want to back up the folder somewhere else as well, just in case ;)

---

### Post by Darth_tater on 2010-01-02
> **Leppie said:**
> what you could do is try to copy the data present in ~/.purple to the windows .purple folder, then delete the ~/.purple folder and create the symlink.
you may want to back up the folder somewhere else as well, just in case ;)


thats pretty much what i did.

I had to delete the .purple folder in my home folder, and then i could create the system link.

it worked perfectly!

~/.purple is actually pointing at my windows purple folder!  all my buddy lists and the like just loaded right up w/o any hastle!

thanks

-- im going to mark this as solved --

---

### Post by dcstar on 2010-01-02
> **SuperSonic4 said:**
> 0) Ensure ntfs-3g is install ```
sudo apt-get install ntfs-3g
```

1a) It would be best to edit your fstab to include the windows partition. .........)
1b) Install ntfs-config (from the repos?) ```
sudo apt-get install ntfs-config
```

Run ntfs-config as root ```
gksu ntfs-config
``` and follow on-screen instructions

[COLOR="Green"]*note: 1b is easier but you get a better idea of how fstab and linux works with 1a. As usual in linux - it's your choice :)*[/COLOR]
.......

Or simply install the **pysdm** package and use a GUI for a minute or two rather than stuff around manually editing critical system files that you could mess up quite easily.

---

### Post by Leppie on 2010-01-02
> **dcstar said:**
> Or simply install the **pysdm** package and use a GUI for a minute or two rather than stuff around manually editing critical system files that you could mess up quite easily.
ntfs-config is a gui application and because of it's simplicity it wouldn't even take a minute to configure it.

---

### Post by Leppie on 2010-01-02
> **Darth_tater said:**
> thats pretty much what i did.

I had to delete the .purple folder in my home folder, and then i could create the system link.

it worked perfectly!

~/.purple is actually pointing at my windows purple folder!  all my buddy lists and the like just loaded right up w/o any hastle!

thanks

-- im going to mark this as solved --

great, glad it's all working ;)

---

### Post by SuperSonic4 on 2010-01-03
> **dcstar said:**
> Or simply install the **pysdm** package and use a GUI for a minute or two rather than stuff around manually editing critical system files that you could mess up quite easily.

ntfs-config is a simple GUI which is self-explanatory, I included the manual method in case the OP wanted to know what was happening.

@OP: glad it worked for you :) (my symlinks are usually in /usr/bin/prog pointing to /usr/local/bin/prog xD

---

