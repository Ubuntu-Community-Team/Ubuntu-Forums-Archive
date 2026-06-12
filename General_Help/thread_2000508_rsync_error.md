---
title: "rsync error"
date: 2012-06-09
forum: General Help
---

### Post by qwertyjjj on 2012-06-09
rsync seems to error on this:

```

j-media-centre@jmediacentre-A880G:~/.gvfs/backups on iomega$ **sudo rsync -azvv /home/j-media-centre/ /home/j-media-centre/.gvfs/backups\ on\ iomega/**
sending incremental file list
rsync: readlink_stat("/home/j-media-centre/.gvfs") failed: Permission denied (13)
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: ERROR: cannot stat destination "/home/j-media-centre/.gvfs/backups on iomega/": Permission denied (13)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(583) [Receiver=3.0.8]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.8]


```

any ideas what causes that?
I'm trying to backup /etc and /home to a network drive and then also a list of installed software.
I reckon I could probably do a full restore from that if something went wrong.

---

### Post by papibe on 2012-06-10
Hi qwertyjjj.

The ~/.gvfs is the underlying support for the desktop automount system. It doesn't work very well when accessed from the terminal.

I would recommend explicitly mounting the share in a directory and then rsync as it were a local directory.

First, you would need to install cifs-utils:
```
sudo apt-get install cifs-utils
```
Then you would be able to mount the share:
```
mkdir  ~/mnt

sudo mount -t cifs  //iomega/backups  mnt/
```
Where iomega is the name of the server, and backups the name of the share.

Then you would be able to rsync like this:
```
rsync -azvv  /home/j-media-centre/  ~/mnt
```
I hope that helps, and tell us how it goes.
Regards.

---

### Post by qwertyjjj on 2012-06-10
> **papibe said:**
> Hi qwertyjjj.

The ~/.gvfs is the underlying support for the desktop automount system. It doesn't work very well when accessed from the terminal.

I would recommend explicitly mounting the share in a directory and then rsync as it were a local directory.

First, you would need to install cifs-utils:
```
sudo apt-get install cifs-utils
```
Then you would be able to mount the share:
```
mkdir  ~/mnt

sudo mount -t cifs  //iomega/backups  mnt/
```
Where iomega is the name of the server, and backups the name of the share.

Then you would be able to rsync like this:
```
rsync -azvv  /home/j-media-centre/  ~/mnt
```
I hope that helps, and tell us how it goes.
Regards.

seems to have started to work but I get a lot of failed directories:
```

pg": Permission denied (13)
.grsync/
rsync: failed to set times on "/home/j-media-centre/mnt/.grsync": Operation not permitted (1)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.grsync/grsync.ini": Permission denied (13)
.gstreamer-0.10/
rsync: failed to set times on "/home/j-media-centre/mnt/.gstreamer-0.10": Operation not permitted (1)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.gstreamer-0.10/registry.i686.bin": Permission denied (13)
.gvfs/
rsync: failed to modify permissions on "/home/j-media-centre/mnt/.gvfs": Operation not permitted (1)
rsync: failed to set times on "/home/j-media-centre/mnt/.gvfs": Operation not permitted (1)
.gvfs/backups on iomega.local/
rsync: recv_generator: mkdir "/home/j-media-centre/mnt/.gvfs/backups on iomega.local" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***



```

Also...for the /etc folder do I need to use sudo?

Is it enough to backup home and etc?

I also need a list of installed software I think then on a restore, I could just install from the OS CD and put etc and home back in place.
[B]j-media-centre@jmediacentre-A880G:~$ sudo dpkg --get-selections > ~/mnt/installed-software.log
bash: /home/j-media-centre/mnt/installed-software.log: Permission denied[/B]

---

### Post by papibe on 2012-06-10
Since the ~/.gvfs is still mounted, I believe your are facing problem with circular reference.

You are copying your home directory to the share, but there's a directory in your home (~/.gvfs) that points to the share.

You need to use an exclude rule, or simple add the -x option to exclude reference to different filesystems:
```
rsync -azvv **[COLOR="Red"]-x[/COLOR]**  /home/j-media-centre/  ~/mnt
```
Hope it helps,
Regards.

---

### Post by qwertyjjj on 2012-06-10
> **papibe said:**
> Since the ~/.gvfs is still mounted, I believe your are facing problem with circular reference.

You are copying your home directory to the share, but there's a directory in your home (~/.gvfs) that points to the share.

You need to use an exclude rule, or simple add the -x option to exclude reference to different filesystems:
```
rsync -azvv **[COLOR="Red"]-x[/COLOR]**  /home/j-media-centre/  ~/mnt
```
Hope it helps,
Regards.

same problem:

```

rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/cddb_local_path.history": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/cddb_search_string.history": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/cddb_search_string_in_result.history": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/default_path_to_mp3.history": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/default_tag_comment.history": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/easytag.log": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/easytagrc": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/file_to_load.history": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/play_list_name.mask": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/playlist_content.mask": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/rename_directory.mask": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/rename_file.mask": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/run_program_with_directory.history": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/run_program_with_file.history": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/scan_tag.mask": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.easytag/search_file.history": Permission denied (13)
.filezilla/
rsync: failed to set times on "/home/j-media-centre/mnt/.filezilla": Operation not permitted (1)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.filezilla/bookmarks.xml": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.filezilla/filezilla.xml": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.filezilla/filters.xml": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.filezilla/layout.xml": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.filezilla/lockfile": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.filezilla/queue.sqlite3": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.filezilla/recentservers.xml": Permission denied (13)
.fontconfig/
rsync: failed to set times on "/home/j-media-centre/mnt/.fontconfig": Operation not permitted (1)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.fontconfig/0e9bbb1b381dc0aebe04d090cf30906a-le32d4.cache-3": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le32d4.cache-3": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.fontconfig/5c568772b6f555ec9101966aad8a986b-le32d4.cache-3": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.fontconfig/e3fa16a14183b06aa45b3e009278fd14-le32d4.cache-3": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.fontconfig/ea47318ec9849e1a71e80a5d69d13859-le32d4.cache-3": Permission denied (13)
.furiusisomount/
rsync: failed to set times on "/home/j-media-centre/mnt/.furiusisomount": Operation not permitted (1)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.furiusisomount/FuriusMountHistory.txt": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.furiusisomount/FuriusMountLog.txt": Permission denied (13)
rsync: recv_generator: failed to stat "/home/j-media-centre/mnt/.furiusisomount/settings.cfg": Permission denied (13)
.gconf/
rsync: failed to set times on "/home/j-media-centre/mnt/.gconf": Operation not permitted (1)
.gconf/apps/
rsync: recv_generator: mkdir "/home/j-media-centre/mnt/.gconf/apps" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
^Crsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(549) [sender=3.0.8]
rsync: writefd_unbuffered failed to write 97 bytes to socket [generator]: Broken pipe (32)
j-media-centre@jmediacentre-A880G:~$ 


```

---

### Post by SeijiSensei on 2012-06-10
I'm guessing the backup device isn't formatted with a *nix filesystem like ext4 but some Microsoft format like FAT32 or NTFS.  Rsync isn't happy backing up to a filesystem like that because it doesn't have the necessary filesystem primitives to preserve things like permissions.

Your best bet would be to reformat the backup device with ext4, but if you need to access it from Windows as well as Linux that isn't going to work for you.  The other option is to back up by creating a "tarball" of the directories and storing that on the backup device instead.  

```

cd /
sudo tar cjvpf /path/to/backup/backup.tar.bz2 etc home

```

will create a single file compressed with bzip2 containing the contents of /etc and /home.

---

### Post by qwertyjjj on 2012-06-10
> **SeijiSensei said:**
> I'm guessing the backup device isn't formatted with a *nix filesystem like ext4 but some Microsoft format like FAT32 or NTFS.  Rsync isn't happy backing up to a filesystem like that because it doesn't have the necessary filesystem primitives to preserve things like permissions.

Your best bet would be to reformat the backup device with ext4, but if you need to access it from Windows as well as Linux that isn't going to work for you.  The other option is to back up by creating a "tarball" of the directories and storing that on the backup device instead.  

```

cd /
sudo tar cjvpf /path/to/backup/backup.tar.bz2 etc home

```

will create a single file compressed with bzip2 containing the contents of /etc and /home.

I tried this tarball method once before and it seemed to tsake forever to run the backup.
Would cp work?

---

### Post by SeijiSensei on 2012-06-10
It shouldn't take a whole lot longer to create a tarball than it does to use rsync.  You should expect it to take a while if you're backing up all of /home, especially if you have multiple users with lots of files.

You could copy the files with cp, I guess, but you can't use "cp -a" since that would expect to be able to copy the permissions and date stamps.

Tar works because all of the filesystem information is stored in the tarball.  The result is just a file that can be copied anywhere.

Can you re-partition the backup drive and create a separate ext4 filesystem in one partition for these backups and create an NTFS filesystem in the other if you need access from Windows?

---

### Post by qwertyjjj on 2012-06-11
> **SeijiSensei said:**
> It shouldn't take a whole lot longer to create a tarball than it does to use rsync.  You should expect it to take a while if you're backing up all of /home, especially if you have multiple users with lots of files.

You could copy the files with cp, I guess, but you can't use "cp -a" since that would expect to be able to copy the permissions and date stamps.

Tar works because all of the filesystem information is stored in the tarball.  The result is just a file that can be copied anywhere.

Can you re-partition the backup drive and create a separate ext4 filesystem in one partition for these backups and create an NTFS filesystem in the other if you need access from Windows?
It's an iomega drive so I think if I repartition it, I will lose the functionality it has for torrents and other stuff.

Also, I cannot remove any of the files created with rsync:

j-media-centre@jmediacentre-A880G:/mnt$ sudo rm -rf *
j-media-centre@jmediacentre-A880G:/mnt$ chown -R root:root /mnt
chown: changing ownership of `/mnt': Operation not permitted

---

### Post by SeijiSensei on 2012-06-11
> j-media-centre@jmediacentre-A880G:/mnt$ chown -R root:root /mnt

You need to use sudo.

> It's an iomega drive so I think if I repartition it, I will lose the functionality it has for torrents and other stuff.


Why?  It's just a hard drive like any other with a bit of electronics to enable it to connect over USB.  Windows won't see the Linux partition, but Linux can see both.  (Actually if you format the Linux partition as ext2 or ext3 you can install the [ext driver for Windows]("http://www.fs-driver.org/") and see both partitions from both operating systems.)

---

### Post by qwertyjjj on 2012-06-11
> **SeijiSensei said:**
> You need to use sudo.



Why?  It's just a hard drive like any other with a bit of electronics to enable it to connect over USB.  Windows won't see the Linux partition, but Linux can see both.  (Actually if you format the Linux partition as ext2 or ext3 you can install the [ext driver for Windows]("http://www.fs-driver.org/") and see both partitions from both operating systems.)

The files have the lock symbol on them.
When I try to list them in the terminal they do not show up.

---

### Post by SeijiSensei on 2012-06-11
Which files?  The ones you created with rsync onto the NTFS partition which has the issues I described earlier? As the errors you listed show, those files are going to have dicey permissions. Can you not list them if you use sudo?  What if you connect the device to a Windows machine; can you delete them that way?

I'll admit to being confused now.  You have this Iomega device.  Does it have a Windows filesystem like NTFS on it?  How is it connected to the system you want to back up?  Is it simply mounted to /mnt as a "fuse" filesystem?  Can you list the other files on the device but not the ones created by rsync?  Can you show us 

```
mount | grep /mnt
```

so we can see the options used to mount it?

You really only have a couple of options.  If you want to keep the Iomega device formatted with FAT32 or NTFS, then you can't use rsync.  You'll need to write a tarball to the device.  If you want to use rsync, you'll need to write the backup to a standard POSIX filesystem like ext4.  That means partitioning the Iomega device or using a different device for backups.

---

### Post by qwertyjjj on 2012-06-12
> **SeijiSensei said:**
> Which files?  The ones you created with rsync onto the NTFS partition which has the issues I described earlier? As the errors you listed show, those files are going to have dicey permissions. Can you not list them if you use sudo?  What if you connect the device to a Windows machine; can you delete them that way?

I'll admit to being confused now.  You have this Iomega device.  Does it have a Windows filesystem like NTFS on it?  How is it connected to the system you want to back up?  Is it simply mounted to /mnt as a "fuse" filesystem?  Can you list the other files on the device but not the ones created by rsync?  Can you show us 

```
mount | grep /mnt
```

so we can see the options used to mount it?

You really only have a couple of options.  If you want to keep the Iomega device formatted with FAT32 or NTFS, then you can't use rsync.  You'll need to write a tarball to the device.  If you want to use rsync, you'll need to write the backup to a standard POSIX filesystem like ext4.  That means partitioning the Iomega device or using a different device for backups.

j-media-centre@jmediacentre-A880G:~$ cd /mnt
j-media-centre@jmediacentre-A880G:/mnt$ ls -al
total 169495948
drwxr-xr-x  2 root root         4096 2012-06-11 07:53 .
drwxr-xr-x 23 root root         4096 2012-05-26 10:59 ..
-rw-r--r--  1 root root 173563813888 2012-06-12 08:01 backup.tar.bz2
j-media-centre@jmediacentre-A880G:/mnt$ mount | grep /mnt
//iomega.local/backups on /home/j-media-centre/mnt type cifs (rw)

and attached folder screenshot with lock icons:

---

### Post by qwertyjjj on 2012-06-13
Somehow the mkdir command created a directory on the hardrive called mnt and filled it up. Did I do something wrong there?

Still can't remove those files created by rsync - how can I format the iomega drive over the network? I tried the disk utility but it doesn't pick it up.

```

j-media-centre@jmediacentre-A880G:~/.gvfs$ ls -l
total 0
drwx------ 1 j-media-centre j-media-centre 0 2012-06-11 08:09 backups on iomega.local
j-media-centre@jmediacentre-A880G:~/.gvfs$ l -al
total 16
dr-x------  3 j-media-centre j-media-centre     0 2012-06-13 19:20 ./
drwxr--r-- 60 j-media-centre j-media-centre 16384 2012-06-13 19:20 ../
drwx------  1 j-media-centre j-media-centre     0 2012-06-11 08:09 backups on iomega.local/
j-media-centre@jmediacentre-A880G:~/.gvfs$ sudo rm- rf backups*
[sudo] password for j-media-centre: 
sudo: rm-: command not found
j-media-centre@jmediacentre-A880G:~/.gvfs$ sudo rm -rf backups*
rm: cannot remove `backups on iomega.local': Permission denied
j-media-centre@jmediacentre-A880G:~/.gvfs$ cd backups*
j-media-centre@jmediacentre-A880G:~/.gvfs/backups on iomega.local$ ls -l
total 48
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 apm
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 apparmor
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 dhcp
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 dpkg
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 fonts
drwx------ 1 j-media-centre j-media-centre     0 2011-10-12 15:30 ifplugd
-rwx------ 1 j-media-centre j-media-centre 48780 2012-06-11 08:09 installed-software.log
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 network
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 rc0.d
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 rc1.d
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 rc2.d
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 rc3.d
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 rc4.d
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 rc5.d
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 rc6.d
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 rcS.d
drwx------ 1 j-media-centre j-media-centre     0 2012-06-11 07:52 ssl
j-media-centre@jmediacentre-A880G:~/.gvfs/backups on iomega.local$ sudo rm -rf *rm: cannot remove `apm': Permission denied
rm: cannot remove `apparmor': Permission denied
rm: cannot remove `dhcp': Permission denied
rm: cannot remove `dpkg': Permission denied
rm: cannot remove `fonts': Permission denied
rm: cannot remove `ifplugd': Permission denied
rm: cannot remove `installed-software.log': Permission denied
rm: cannot remove `network': Permission denied
rm: cannot remove `rc0.d': Permission denied
rm: cannot remove `rc1.d': Permission denied
rm: cannot remove `rc2.d': Permission denied
rm: cannot remove `rc3.d': Permission denied
rm: cannot remove `rc4.d': Permission denied
rm: cannot remove `rc5.d': Permission denied
rm: cannot remove `rc6.d': Permission denied
rm: cannot remove `rcS.d': Permission denied
rm: cannot remove `ssl': Permission denied
j-media-centre@jmediacentre-A880G:~/.gvfs/backups on iomega.local$ 

```

---

### Post by qwertyjjj on 2012-06-13
I get an error trying to mount it:

j-media-centre@jmediacentre-A880G:/media/iomega$ sudo mount -t cifs ~/.gvfs/backup\ on\ iomega.local/ /media/iomega/
[sudo] password for j-media-centre: 
mount.cifs: bad UNC (/home/j-media-centre/.gvfs/backup on iomega.local/)
j-media-centre@jmediacentre-A880G:/media/iomega$ sudo mount -t cifs ~/.gvfs/backup\ on\ iomega.local /media/iomega/
mount.cifs: bad UNC (/home/j-media-centre/.gvfs/backup on iomega.local)
j-media-centre@jmediacentre-A880G:/media/iomega$

---

### Post by papibe on 2012-06-13
cifs is to be used to mount network shares, not already mounted shares.

You should do something like this:
```
sudo mount -t cifs  //iomega/backups  mnt/
```
where 'iomega' is the name of the host sharing the share 'backups', and 'mnt' is a local directory where you want the share to be mounted.

Regards.

---

### Post by qwertyjjj on 2012-06-14
> **papibe said:**
> cifs is to be used to mount network shares, not already mounted shares.

You should do something like this:
```
sudo mount -t cifs  //iomega/backups  mnt/
```
where 'iomega' is the name of the host sharing the share 'backups', and 'mnt' is a local directory where you want the share to be mounted.

Regards.

When I created /mnt last time and started backing up it filled up my local drive rather than the network drive?!

---

