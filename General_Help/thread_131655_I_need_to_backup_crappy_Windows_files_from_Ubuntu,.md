---
title: "I need to backup crappy Windows files from Ubuntu, and I am having problems."
date: 2006-02-16
forum: General Help
---

### Post by shootingstars on 2006-02-16
Yesterday, I had some power malfunction while booted into Windows, and it will not reboot worth a damn now. There is quite a bit of stuff that I really would not like to see lost (ie. my profile for Thunderbird), but I am not able to copy files from my Windows partition to Ubuntu. I am pretty much a brand-newbie, and the only method I have performed/been able to find is using nautilus to try to grab the files. Any suggestion would really be great. I am working on a proposal for a research project at the moment, and if I can work this out, I need to do so ASAP. Thanks everybody!

---

### Post by mustang on 2006-02-16
Will the drive not boot or the windows OS not boot?

If the drive is intact, try mounting it in Ubuntu: [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by shootingstars on 2006-02-16
The drive does boot, just not the Windows partition. When I try to boot in safe mode, it hangs at some point in loading the system drivers. I am pretty sure the partition is already mounted in Ubuntu since I can view, and even open some, files. It just will not let me copy them to a folder etc.

```
neptune@JUDAS:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: /dev/hda1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/hda1 is mounted on /media/hda1
```

---

### Post by mustang on 2006-02-16
What does Nautilus tell you when you try to copy files from your windows partition?

If it doesn't tell you much, try copying in the terminal with the "cp" command. 

In case you don't know how to use it:

```
sudo cp /media/windows/findsomefile /home/
```

---

### Post by shootingstars on 2006-02-16
I'll give the copy command a try in terminal, and for the meanwhile here is what terminal tells me when I try to copy the files in nautilus:

```
neptune@JUDAS:~$ sudo nautilus
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: No OLE2 signature
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
error: The metadata does not have a thumbnail property
```

---

### Post by shootingstars on 2006-02-16
Did I do something wrong here? Thank you for the help!

```
neptune@JUDAS:~$ sudo cp "/media/hda1/Documents and Settings/Root/My Documents" /home/
cp: omitting directory `/media/hda1/Documents and Settings/Root/My Documents'
```

---

### Post by mustang on 2006-02-16
I'm not sure if those problems are related to you not being able to copy from your windows partition. 

Not sure if it makes a difference but did you try running nautilus as a normal user and not a super user (i.e. just "nautilus" in the terminal vs "sudo nautilus")?

---

### Post by shootingstars on 2006-02-16
When I try to do that it tells me that I do not have permission. Any other suggestions?

---

### Post by hellerite on 2006-02-16
You can use firefox, but it should be your last option, because it is a slow process. Start Firefox and in the address bar type the following /media/windows drive name. you can point and click afterwards to the folders you need to back up. This is a slow process because you will have to right click every file you need and use the save link as. I have used this method before but like I said it is SLOW!

---

### Post by shootingstars on 2006-02-16
That sounds pretty crappy, but I just might have to resort to that. Thanks. If anybody comes up with something better I would appreciate it.

Is there a was I could resize my Linux partition and install a different installation  of Windows on it to access the files?

---

### Post by hellerite on 2006-02-16
Try 'emelfm' this is an X file manager. Open your console and type:

sudo apt-get install emelfm

after it finishes the installation you can run it by typing the following:

/usr/X11R6/bin/emelfm

It has a split window gui pretty easy to understand.

---

### Post by shootingstars on 2006-02-17
I am still going to check out emelfm, but I ended up working out my problem. I found a program that builds a live Windows environment ISO/disc from the Windows install files which you can then boot from. This then allowed me to copy the necessary files pretty easily. It also has a few useful applications for other purposes. Thanks for all of the help everybody, and here is the link for any people with my problem in the future:

Bart's Preinstalled Environment (BartPE) bootable live windows CD/DVD
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by steve.horsley on 2006-02-17
This is daft. I don't know what's up with nautilus, but whatever it is won't stop you copying files with the command line. If you need to have root privilege to read the files, use the command **sudo su** to get a # prompt. Use **cd** to move around, and **cp** to copy files, like this:
```
cd /media/drive_c/mystuff (names with spaces must be quoted in single quotes like this:)
cd '/media/drive_c/my stuff'
cp music /home/steve
```
You can copy individual files or directories full of files by name.

---

