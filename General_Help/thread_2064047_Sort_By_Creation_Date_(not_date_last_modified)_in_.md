---
title: "Sort By: Creation Date (not date last modified) in folder structure?"
date: 2012-09-28
forum: General Help
---

### Post by 777funk on 2012-09-28
I am having a problem finding picture folders now on Ubuntu. I'd like to sort the folders by date created (i.e. a picture folder shot in 2005 would be far below the ones shot this year). 

All I have is Modified Date sorting in Ubuntu. Is there a way to sort by Created date? I'm getting modified dates for folders shot long ago in this year (almost all my picture folders).

---

### Post by Vaphell on 2012-09-28
afaik you can't get the creation time
when you run stat command you get access, modification and change time.

[http://unix.stackexchange.com/questions/2802/what-is-the-difference-between-modify-and-change-in-stat-command-context](http://unix.stackexchange.com/questions/2802/what-is-the-difference-between-modify-and-change-in-stat-command-context)

Simply rename the folders so they have year at the beginning.
in case you needed automatic renaming, if the pictures themselves are with old timestamps you could take advantage of it, or if the pictures contain exif data.

---

### Post by lechien73 on 2012-09-28
If you're running ext4, you can get the creation time, but you need to run debugfs and know the file or folder's inode. For example, for a folder on my system, the following command:

```
sudo debugfs -R 'stat <20447529>' /dev/sda2
```

Produces the following output:

```
Inode: 20447529   Type: regular    Mode:  0664   Flags: 0x80000
Generation: 1641156306    Version: 0x00000000:00000001
User:  1000   Group:  1000   Size: 204800
File ACL: 0    Directory ACL: 0
Links: 1   Blockcount: 400
Fragment:  Address: 0    Number: 0    Size: 0
 ctime: 0x5045d5a9:e9ddeb78 -- Tue Sep  4 11:19:21 2012
 atime: 0x5045d7a2:98cd0e7c -- Tue Sep  4 11:27:46 2012
 mtime: 0x4ea05640:00000000 -- Thu Oct 20 18:11:28 2011
crtime: 0x5045d5a9:940943a0 -- Tue Sep  4 11:19:21 2012
Size of extra inode fields: 28
EXTENTS:
(0-49):81841269-81841318
```

crtime is the creation time. However this isn't particularly useful for sorting folders!

---

### Post by drmrgd on 2012-09-28
Dumb thought:  since these are photos, which are unlikely to be modified once they are placed in a folder, can't one use mtime or ctime to sort them?  Or, do those stats get modified when one moves the files (i.e. ctime will reflect when one moves a photo to a different folder)?  

If this won't work well enough, then I think that parsing the exif data and using that for a sort would be the best option.  Probably not too bad for a little quick script.  Had a quick look and found this, if it helps:

[http://www.linuxquestions.org/questions/programming-9/search-recursively-by-exif-date-790443/](http://www.linuxquestions.org/questions/programming-9/search-recursively-by-exif-date-790443/)

---

### Post by matt_symes on 2012-09-28
Hi

There is no easy way to do this as others have pointed out. 

You can use find, -exec and debugfs though.

This will search for directories in my home folder. It is horribly slow and should be optimised to speed it up.

```
find /home/matthew/* -maxdepth 0 -type d -exec bash -c " sudo debugfs -R 'stat \"{}\"' /dev/sda1 2>/dev/null | sed -n -e '10p' | tr '\n' ' '; echo \"{}\" " \; | sort
```I would wrap it up in a function.
```

matthew-Aspire-7540:/home/matthew % head -n 4 .functions 
function crd
{
        find /home/matthew/* -maxdepth 0 -type d -exec bash -c " sudo debugfs -R 'stat \"{}\"' /dev/sda1 2>/dev/null | sed -n -e '10p' | tr '\n' ' '; echo \"{}\" " \; | sort;
}
matthew-Aspire-7540:/home/matthew %
```This is the output
```

matthew-Aspire-7540:/home/matthew % crd
crtime: 0x4f05d6a4:b3e8709c -- Thu Jan  5 16:58:12 2012 /home/matthew/Desktop
crtime: 0x4f05d6a4:b3e8709c -- Thu Jan  5 16:58:12 2012 /home/matthew/Templates
crtime: 0x4f05d7e8:93ec6958 -- Thu Jan  5 17:03:36 2012 /home/matthew/storage
crtime: 0x4fabce13:a1f830c4 -- Thu May 10 15:17:55 2012 /home/matthew/sshfs_media
crtime: 0x4fabd2d3:0f17dd04 -- Thu May 10 15:38:11 2012 /home/matthew/sshfs_home
crtime: 0x500ca217:a1332c10 -- Mon Jul 23 02:00:07 2012 /home/matthew/mail
crtime: 0x50150f70:57fc9010 -- Sun Jul 29 11:24:48 2012 /home/matthew/Ubuntu One
crtime: 0x50326694:64a1e5bc -- Mon Aug 20 17:32:20 2012 /home/matthew/fontconfig
crtime: 0x505b5d4d:1a02fb64 -- Thu Sep 20 19:15:41 2012 /home/matthew/vim
matthew-Aspire-7540:/home/matthew % 
```You could pass parameters to the function to make it more useable or use the current working directory
```

find $(pwd)/* -maxdepth 0 -type d -exec bash -c " sudo debugfs -R 'stat \"{}\"' /dev/sda1 2>/dev/null | sed -n -e '10p' | tr '\n' ' '; echo \"{}\" " \; | sort;
``````

matthew-Aspire-7540:/home/matthew/Desktop % pwd
/home/matthew/Desktop
matthew-Aspire-7540:/home/matthew/Desktop % crd
crtime: 0x5065c23b:936259e8 -- Fri Sep 28 16:28:59 2012 /home/matthew/Desktop/a
crtime: 0x5065c23e:026ba704 -- Fri Sep 28 16:29:02 2012 /home/matthew/Desktop/aaa
crtime: 0x5065c241:4eb5109c -- Fri Sep 28 16:29:05 2012 /home/matthew/Desktop/abbbb
matthew-Aspire-7540:/home/matthew/Desktop % 
```The main thing i would do is to speed it up though.

Kind regards

---

