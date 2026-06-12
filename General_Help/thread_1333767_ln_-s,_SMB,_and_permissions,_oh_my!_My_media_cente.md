---
title: "ln -s, SMB, and permissions, oh my! My media center setup needs help."
date: 2009-11-21
forum: General Help
---

### Post by ttilberg on 2009-11-21
Hello, and thanks for reading.
My current set up is this:
2 HDs: 
200 GB NTFS (for WinXP as I do a lot of music production)
80 GB linux (on which I have 20:/ and 60:/home)

I have a lot of media files on the 200 GB drive, which I have mounted at boot with /etc/fstab. I recently made some symlinks in order to more easily access some of these files in my ~/Music and ~/Video directories.

Works great.

The interesting part comes when I add SMB into the mix, for networking to my media center computer running XBMC in another room. 

What I wanted was to set up only SMB://linuxcomputer/home/ttilberg/Music on the mediacenter computer, and have magic access to all my symlinked files as well.

Problem is, permissions won't allow it (I understand it's a security thing). Currently the symlinked files belong to Root, and group Hotplug. Others do not have any permissions.

Is there a way to configure smb to ignore such things, or configure my ntfs mount in fstab to allow me to have permissions of the NTFS partition?

I googled around a bit and couldn't find what I needed.


Another question is: Is there a way to remove one more level of directories? Currently I have /media/ntfs/audio/ -> ~/Music/
The command I used was 
ln -s /media/ntfs/audio/ ~/Music/

This created a link to "audio" in the Music directory. 
Is there a way to dump audio/ INTO the Music directory? 
ie audio/foo1 audio/foo2 can now be seen as ~/Music/foo1 ~/Music foo2 without using ln -s path/*? (That doesn't work because if I add files to /audio later, it doesn't keep them updated.)  I'd like to retain the files that are in ~/Music and add the extra files in as well, not just replace the ~/Music folder with the one on the NTFS.

Sorry about -v. Whoo.
Thanks for the help.

---

### Post by ttilberg on 2009-11-22
I have now figured out the first part, using umask=000 in fstab. I figured 777 was what it should have been, but apparently umask's values are inverted.

I am still seeking help on the second part however:

Adding the contents of one directory on a separate filesystem into the directory of another

/foo/foo1
/foo/foo2
/foo/foo3

gets dumped into

/bar/bar1
/bar/bar2
/bar/bar3
>/bar/foo1
>/bar/foo2
>/bar/foo3

ln -s /from/* /to/ 
doesn't work because it doesn't keep things updated (if I add another file to the /from/ directory, it doesn't get put into /to/

---

### Post by kadeous on 2009-11-22
Are you using a GUI or Command Line system?
 
If Command line I'd recommend webadmin, or ISPConfig 3. Both will help you setup samba shares very easily.
 
Sorry I can't be of much help, I'm still learning myself.

---

