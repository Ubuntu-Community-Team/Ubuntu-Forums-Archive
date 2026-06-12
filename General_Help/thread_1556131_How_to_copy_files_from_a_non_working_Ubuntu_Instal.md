---
title: "How to copy files from a non working Ubuntu Install"
date: 2010-08-19
forum: General Help
---

### Post by tomreid on 2010-08-19
Hi

My father in law had a problem with his Ubuntu system. After quite some playing around, we discovered that an update had damaged or removed the graphics driver and the system was stuck in non graphics mode.

This thread refers: [http://ubuntuforums.org/showthread.php?t=1457402](http://ubuntuforums.org/showthread.php?t=1457402)

Rather than spend much more time trying to figure out how to re-install a graphics driver without a graphical user interface, I decided to cut my losses and re-install Ubuntu.

Before I did this though, I had some files to recover. So I burned a Live CD and booted from that. 

But my problem is that I can't copy all the files from the home directory of the hard drive. I get a permissions error when I try to copy or view the files. I'm assuming that, as the system does not see I'm the original user, that it won't let me access the files.

This must be a fairly common problem, does anyone know how I can recover all the files? I just want to use the live CD to provide a working OS to allow me to copy and paste the files onto an external HD.

The Live CD is actually the Lubuntu variant, I wanted a real lightweight OS to use on a live CD. I assumed that wouldn't make a difference.

Oh, and of course, if there is a real simple solution to my original problem of a broken graphics card driver, I'd be interested in that too.

cheers

---

### Post by Neezer on 2010-08-19
I'm not sure about the graphics because I am pretty new at this, but if you just boot up normally you have a prompt? You can use the command line to copy the files to your external drive. 

there a a few basic commands that you'll need.

ls - this will list all of the files in your working directory

pwd - this will print working directory. (when you start up it should be /home/yourusername/. This is called your home directory)

cd - this will change directory to one that you specify. us ls first to see what the other directories are. in your working directory. to change your working directory use 
```

cd directoryyouwanttochangeto

```

another feature of cd is that if you don't use any arguments if will take you to your home directory. 
```

cd

```
that is all you need to get back to /home/yourusername


now you're going to have to find where the external drive mounts on the system....it is usually in /media. there are 2 ways to get there...relative path, which is always relative to your working directory, and absolute path, which defines a path from the beginning of the mount point which is /
to get to /media from /home/yourusername

absolute path
```

cd /media

```
The /media defines that absolute location of media on your file system so you don't have to go into media's parent folder which is /.


relative path
```

cd /
cd media

```

cd / will always get you to the top of your system. then you can just follow each file down....for example to get into your home directory you can type 
cd /
cd home
cd yourusername

or you can type
cd /home/yourusername

both of the two previous examples are trivial because you can also use cd to accomplish the same thing.

Once you are inside /media you'll have to look to see what is inside the folder. so do an ls search and it will show you what you have. something should ring a bell about your external drive.

the last thing you'll need is cp. 
cd just copies a file from one place to another. it is not cut and paste. it is copy and paste.

so once you find the documents/stuff on your computer you want, you can just copy them to the external disk....

cp /path/to/file/you/want/to/copy /path/that/you/want/to/copy/it/to

it will be something like this

cp /home/yourusername/Documents/documentname.txt /media/nameofexternaldrive

I hope this helps....I never realized what was involved in copying a file via command line...I'm sure there are shorter ways to do it, but I am assuming 0 experience with command line.

---

### Post by darolu on 2010-08-19
I suppose you can log in to the computer, via CLI that is; so before you start reinstalling try to run:
```
startx
```
And see if you can get the GUI back, you may find it easier to (try to) fix the graphics driver problem you mentioned.

Copying files with super-user powers (or root access) should work, when you boot the LiveCD try to open Nautilus with:
```
gksu nautilus
```
I think LXDE default file manager is PCMan but I'm not sure how to run it, I suppose you can try with "sudo pcmanfm" but I'm not sure.
The recommended option would be to use your terminal of course, you can gain root access with:
```
sudo -i
```

Good luck.

---

### Post by tomreid on 2010-08-19
Thanks guys. I had forgotten about the "GKSU" command. I ran the whole thing as root and was able to copy the files. In Lubuntu the command is "gksu pcmanfm".

cheers

---

