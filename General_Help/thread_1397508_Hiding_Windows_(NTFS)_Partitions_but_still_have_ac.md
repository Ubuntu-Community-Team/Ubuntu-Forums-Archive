---
title: "Hiding Windows (NTFS) Partitions but still have access"
date: 2010-02-03
forum: General Help
---

### Post by VideoRoy on 2010-02-03
Like many here, I still have to dual boot with Windows (for now!) but having the various NTFS partitions show up in Nautilaus, etc. is a problem.

Also I would like to share some data between Win7 and Ubuntu 9.10 but I cannot create any more partitions due to well know limitations.  In my case I already have 3 primary Windows partitions that I want to keep and 1 primary Linux with ext4 and swap as logicals for Ubuntu.  BTW my laptop had all 4 primaries used up an I got rid 1 for Ubuntu.  I could get rid of more but really do not want to now.

I found many great ideas and suggestions here in the forums but could not find exactly what I was looking for so I cobbled together a couple of I ideas and I think I have a working solution.

First to hide a Windows partition and protect it this works great when you add this line to fstab:

> /dev/sda2 /Windows/sda2      ntfs-3g    defaults,umask=777    0    0


Of course change your partition to the correct one and make sure the /Windows directories are created.

I have used this many times and it works great except I want to have access to 1 or 2 directories without exposing the whole drive.

I turned to symbolic links to help solve but when sda2 is "hidden" with the above there is a rights problem for my normal user.  I could probably solve it with umask somehow but I just did this instead:

> /dev/sda2 /Windows/sda2 ntfs-3g defaults,locale=en_US.utf8 0 0

I found this allows me to access the directory but it is still hidden from Nautilaus.  I am guessing it is because it is mounted in a location it does not normally look in.

After this I created a symbolic link to the directories I want access like this:

> ln -s /Windows/sda2/Temp /home/myuser/windir

Note I did not use sudo here because that was causing me rights problems at one time.  This is permanent until you rm the windir file since symbolic links are just special files.

So now I can access windir in my home directory on the NTFS partition without me accidentally messing up my other Windows system files.  If I try hard I can mess it up but this provides just enough protection for me.  I can also drag the link to my desktop or the Naultilaus left nav pane and it acts like a regular directory.

I sure there are a 100 ways to achieve what I wanted to do but thought I would share this method since it took me a while to figure it out.   Maybe it will help someone else.

---

### Post by VideoRoy on 2010-02-03
One tweak to this:

> /dev/sda2 /Windows/sda2 ntfs-3g defaults,locale=en_US.utf8 0 0                      
Changed to this:
> /dev/sda2 /Windows/sda2 ntfs-3g defaults,[COLOR=Blue]**umask=022**[/COLOR],locale=en_US.utf8 0 0                      
Although the first one did not hurt anything, if you did an "ls - l" all the files were showing up +x by default.

umask=022 allows anyone to look at the files which is fine for me and allows my normal user to access / change the files on the NTFS drive.  Since it is my laptop this is fine.

If you want a different set of permissions for the defaults files you might want to spend some time learning about umask.  Good reference here:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

