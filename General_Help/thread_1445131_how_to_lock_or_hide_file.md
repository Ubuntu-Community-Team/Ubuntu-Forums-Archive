---
title: "how to lock or hide file?"
date: 2010-04-02
forum: General Help
---

### Post by abhilashm86 on 2010-04-02
i've been facing this problem of locking up files, i've three users in my system, i can't lock a folder but just can hide it by appending . in front of file.

is there any tool/software in linux to lock a file, so other users cannot even open/see.

i tried with chmod options but din't work?

---

### Post by HermanAB on 2010-04-02
Gpg, TrueCrypt, LUKS, Zip with password...

---

### Post by Hariharan_the_great on 2010-04-02
Hi :D

    You can hide as well as lock your datas in ubuntu.. There are two options for you. During the installation of Ubuntu, there will be an option, stating encrypt home folder or something.  If you select it, each user will get their home directory encrypted and so other users cannot access it.  Else if you want to hide your files but also you want to see other user files, you can simply encrypt your files using PGP, explicitly.  It will require a key generation for encrypting. Other users if they try to read your file, Ubuntu will ask them for the key.... 

The risks are, if you fail to keep the key safe, the data will be unrecoverable :frown::frown:

Hope my reply is useful.

Regards,
Hariharan. :-({|=

---

### Post by yota on 2010-04-02
If you just want to prevent other users to access some files or enter some directories, probably encryption is overkill.
[Filesystem permission]("http://en.wikipedia.org/wiki/Filesystem_permissions#Traditional_Unix_permissions") are exactly meant for that and if it didn't work it just means that, most likely, you haven't applied the correct permissions to achieve your goal.

A good starting point can be: [http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)

Hope this helps!

---

### Post by stinkeye on 2010-04-02
Cryptkeeper is a system tray applet that manages EncFS encrypted folders. 
Simple to use.

---

### Post by abhilashm86 on 2010-04-07
thanks for those replies.....

see i can change permissions for text and system files easily, i did using chmod,

```
abhilash@abhilash:~$ ls -l 
total 88
drwxrwxr-x  9 abhilash abhilash 4096 2010-04-02 16:33 Adobe_Flex_Builder_Linux
----------  1 abhilash abhilash  344 2010-04-04 18:40 chat1.html

```

see chat1.html has all permissions off.

But can i make video and audio files also lock and hide? i tried but it did not change permissions, see this 
```
abhilash@abhilash:/media/SONGS/videosongs/English$ ls -l Breaking\ Benjamin-The\ Diary\ Of\ Jane.mpg 
-rwxr-xr-x 1 abhilash abhilash 35522340 2008-02-22 17:38 Breaking Benjamin-The Diary Of Jane.mpg
abhilash@abhilash:/media/SONGS/videosongs/English$ chmod a-x Breaking\ Benjamin-The\ Diary\ Of\ Jane.mpg 
abhilash@abhilash:/media/SONGS/videosongs/English$ ls -l Breaking\ Benjamin-The\ Diary\ Of\ Jane.mpg 
-rwxr-xr-x 1 abhilash abhilash 35522340 2008-02-22 17:38 Breaking Benjamin-The Diary Of Jane.mpg
abhilash@abhilash:/media/SONGS/videosongs/English$ chmod a-r Breaking\ Benjamin-The\ Diary\ Of\ Jane.mpg 
abhilash@abhilash:/media/SONGS/videosongs/English$ ls -l Breaking\ Benjamin-The\ Diary\ Of\ Jane.mpg 
-rwxr-xr-x 1 abhilash abhilash 35522340 2008-02-22 17:38 Breaking Benjamin-The Diary Of Jane.mpg

```

---

### Post by rossmoore on 2010-04-07
Hmm, I see you're in /media/SONGS. That implies you're working with a mounted drive. What format is the drive? IIRC Fat32 doesn't support permissions, and that's why it works in your home drive (ext4?) and not on that file you're trying in /media/SONGS.

---

### Post by abhilashm86 on 2010-04-07
> **rossmoore said:**
> Hmm, I see you're in /media/SONGS. That implies you're working with a mounted drive. What format is the drive? IIRC Fat32 doesn't support permissions, and that's why it works in your home drive (ext4?) and not on that file you're trying in /media/SONGS.

yes rossmoore, its an drive mounted on /media,
```
/dev/sda7: LABEL="SONGS" UUID="71B1-0D79" TYPE="vfat" 
```

So file system other than ext type wont work?? whats other solution to lock and hide files in other type of file systems?

---

### Post by rossmoore on 2010-04-07
There are other file systems, apart from ext types, that will work. But FAT isn't one of them.
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)
[Look at the POSIX file permissions bit]
NTFS is one of the ones that will, mostly, work.

There are other options - you can control who has read and write access to the whole mount (i.e. eveything below /media/SONGS) by changing the options you use to mount it (in fstab, or manually with the mount command). Specifically you can change the owner of the mount, and change the umask.

Alternatively you might be able to achieve what you want with a bit of sleight of hand using symlinks, but I'm not sure:
[http://www.virtualblueness.net/wine-doc/vfat.html](http://www.virtualblueness.net/wine-doc/vfat.html)

But if you're going to that much effort you might better off reformatting (if that is even an option).

---

