---
title: "The easiest way to share files on a dual-boot?"
date: 2009-12-18
forum: General Help
---

### Post by freestyleren on 2009-12-18
What would be the easiest way to share documents and music on dual-boot with Vista and Ubuntu? So I wouldn't have to have the same music in two places.

---

### Post by Grenage on 2009-12-18
Store them on the vista partition.  Ubuntu can read NTFS, no problem.

---

### Post by Matt__ on 2009-12-18
```
sudo apt-get install ntfs-config
```To mount your ntfs windows drive on ubuntu desktop (or create shortcut launcher to music folder)
select drives to mount and enable write support when prompted.

---

### Post by indytim on 2009-12-18
Or, if you already have your partitions formatted to ext3 and populated and don't want to go through the headache of re-formatting and populating to NTFS, from the windows side:

[http://http://www.fs-driver.org/]("http://http://www.fs-driver.org/")

IndyTim

---

### Post by Matt__ on 2009-12-18
really Indy, never go to THAT side! lol.

---

### Post by warfacegod on 2009-12-18
Use a seperate hard drive either internal or external formatted to NTFS.

---

### Post by freestyleren on 2009-12-18
So I've created the folders on separate hard drive, but is there any way I can make these folders(music, documents, etc) show up instead of those in the home folder in Ubuntu?

---

### Post by Grenage on 2009-12-18
You can mount the drive and use links (shortcuts) to your home folder.  Since you will undoubtedly want the drive mounted every time you been up. you'll need to add it to /etc/fstab.

I won't go into that here, there are a hundred guides if you google *ubuntu fstab mount drive* etc.

---

### Post by Confuzius on 2009-12-18
If I'm dual booting with Windows I usually set 4 partitions

Windows (NTFS) 23%
Media (NTFS) 50%
Linux (ext4)25%
Swap (swap) 2%

Percentages are roughly averaged based depending on harddrive size. Then all of my music, movies and docs go in the Media partition.

---

### Post by northern lights on 2009-12-18
> **indytim said:**
> ...from the windows side:

[http://http://www.fs-driver.org/]("http://http://www.fs-driver.org/")Personally, I'd advise against this. I'd hate a Redmond OS to access (and possibly destroy) my ext2,3 filesystems.

[fstab HowTo]("http://www.tuxfiles.org/linuxhelp/fstab.html")
[man mount]("http://linux.die.net/man/8/mount")
[symlinks]("http://kb.iu.edu/data/abbe.html")

Partitions will appear under the Places menu. Also you can bookmark 'em in nautilus (drag&drop into left-hand pane).

---

### Post by freestyleren on 2009-12-18
So what I'm trying to do is to mount the second hd automatically?

---

### Post by Grenage on 2009-12-18
Correct.  By adding the drive to /etc/fstab you can mount it every time the computer boots.  You don't have to, but it makes for an easy life.

---

### Post by freestyleren on 2009-12-18
I looked at the links but it's very confusing. What's the name for another harddrive?

---

### Post by Darael on 2009-12-18
Almost certainly /dev/sdb.

---

### Post by Grenage on 2009-12-18
Let's assume that your second drive is /dev/sdb and that it contains 1 partition,  You'll be referencing /dev/sdb1.

First you need a mount point; in Ubuntu I recommend putting one in /media.

```
sudo mkdir /media/music
```

Assuming your second drive is FAT32, in /etc/fstab add a line like this:

```
/dev/sdb1 /media/music vfat rw,uid=1000,gid=1000 0 0
```

Type the following and watch for errors:

```
sudo mount -a
```

Assuming you have none, it should have mounted your drive to /media/music.  Now you might want a link/shortcut to your home folder:

```
ln -s /media/music /home/**yourusername**/mymusic
```

Make sense?

---

### Post by freestyleren on 2009-12-18
Yes, thank you. The drive is NFTS though, how would I write that?

---

### Post by Darael on 2009-12-18
Simply replace "vfat" in the line given with "ntfs-3g". That should be enough.

---

### Post by gadolinio on 2009-12-18
As I am not very familiar with the command line, I use disk-manager (find it in synaptic or [http://packages.ubuntu.com/search?disk-manager](http://packages.ubuntu.com/search?disk-manager)). Once installed, you'll find it in system-->administration--> disk manager.
This application lets you set your partitions to be automatically mounted every time you start your system; they will always be available, like in windows.
NTFS partitions are shown as ntfs-3g (if not, edit that partition from the list you have in the application; it's really easy to use, you'll see).
Then you can create links to your windows folders (my images, etc), and put those links inside your ubuntu's user folder; the links will behave as if they were folders inside ubuntu's user.
That's it.

---

### Post by oldfred on 2009-12-18
I directly mount my windows shared drive to my /home.

# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

This does put all the directories in shared one level down, but I am now 90% Ubuntu and mount a ext3 /data directory and use the mapping commands from that to the top level of /home. You can only have one directory with the same name. So my ~/Pictures is my /data partition and my /shared/photos is my windows share. Even my  wife down not understand but it works.

---

