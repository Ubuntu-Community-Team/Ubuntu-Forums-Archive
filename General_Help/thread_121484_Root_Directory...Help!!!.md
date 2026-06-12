---
title: "Root Directory...Help!!!"
date: 2006-01-25
forum: General Help
---

### Post by bfonseca on 2006-01-25
Hi,
For some odd reason my root directory is no longer a directory but a file (wierd) Inside the / Directory my root permissions are 755 but there is no d for directory.  It all started with a error at startup...the error was Duplicate or bad block in use! so from here I did a e2fdsk /dev/sda and that fixed my problem but then left me with this other problem.

So my question is how do I restore the root directory? or How do I change a file to a direcctory...because my root file(directory) shows there are files in there, but  I can not cd into it(and I know its because it is not a directory) but I am thinking that if I some how am able to make it a directory(the file) then that may fix my problem.
Any help would be greatly appreciated
Thanks
Brian

---

### Post by rmjokers on 2006-01-25
I guess I'm not understanding exactly what the problem is.  How did you determine that the root directory is being treated as a file?  How can your system even be started if this is the case?  Assuming you have logged in and opened a terminal window, what happens if you type

ls -l /

and also

sudo ls -l /

What application are you using that tells you / is a file?  It sounds to me more like there is some sort of permissions problem with the root directory.

---

### Post by bfonseca on 2006-01-25
rmjokers,
the / directory is a directory inside of that is a root directory and that root directory has some how change to a file. i dont know how that would be possible. i did a ls -l inside the / directory and it says the root/ permissions are 755 but it is not showing that it is a directory(when it should be a directory) it should look like this drwxr-xr-x but it looks like this -rwxr-xr-x

If you go to cd / and then ls -l there is a root directory and that is the problem.
thanks for your quick response. Any ideas one what to do.
Brian

---

### Post by bfonseca on 2006-01-25
hi all again,
the problem i am having has to do with a subdirectory inside the / directory When i do a cd / and then an ls -l i get a subdirectory called root/ and many others the problem is with root/ this has some how change from a dir to a file and i have no idea how that would be possible. If anyone knows please help me figure this out. I should be getting drwxr-xr-x  for root/ but instead I get this -rwxr-xr-x

I will keep hacking away at it but soon i will just give up and create a tar file from my father in-laws root/ directory with all subdirectories and replace the one i am having problems with. I sure would rather fix my problem because I am sure someone else will end up getting the same problem eventually.I hope i cleared up any confusion if not please let me know. I dont wanna take the tar file solution.
Thanks for all your help
Brian

---

### Post by bfonseca on 2006-01-25
hi sorry one more addition. :) the /root subdirectory is the home directory of the root user account and this is where the problem is. thats all unless someone has any questions.
Brian

---

### Post by rmjokers on 2006-01-26
Well, the structure on disk that stores the file type is called an inode for an ext2/3 file system.  Looks kinda like this (/usr/include/linux/ext2.h):

struct ext2_inode {
        __le16  i_mode;         /* File mode */
        __le16  i_uid;          /* Low 16 bits of Owner Uid */
        __le32  i_size;         /* Size in bytes */
        __le32  i_atime;        /* Access time */
.....

Inodes are stored in the filesystem metadata that should only be accessible by the kernel.  Directories are just a special type of file with a different i_mode value than normal files.  What it sounds like is somehow, the filesystem driver screwed up and marked the /root directory as a regular file rather than a directory.  I dont know how you could go back and fix this without manually finding the inode entry on disk and changing the i_mode field....which could be VERY dangerous.  Not aware of any regular tools capable of this.

One good thing though is you may possibly be able to at least identify what was in the root directory.  As I said, a directory is just a normal file with a special i_mode and special data inside.  It should just be an array of ext2_dir_entry structures like this:

struct ext2_dir_entry {
        __le32  inode;                  /* Inode number */
        __le16  rec_len;                /* Directory entry length */
        __le16  name_len;               /* Name length */
        char    name[EXT2_NAME_LEN];    /* File name */
};

This means if you open the /root as a file in an editor like vim or a hex editor, you should just see a list if inode numbers and filenames for every file / directory that was in the /root directory.  With some additional effort, you could actually track down the inodes of the files and recover them assuming they have not been unlinked (deleted) mistakenly by the filesystem.

The fact that this actually occured seems to indicate there may be some other issues with your filesystem or hardware.  Better make sure you've done a backup of any other data on the disk soon.

I know this was a technical post and probably confusing, so let me know if you have any questions.

---

### Post by steve.horsley on 2006-01-26
If the file contents of the old /root directory aren't important to you, you could just delete the /root file and then create a new /root directory, like this:
> sudo rm /root
sudo mkdir /root

I assume that e2fdsk in a typr and you meant e2fsck? You might want to run it a second time after the above changes, just in case. Also, keep backups in case the hard disk is on the way out.

---

### Post by bfonseca on 2006-01-26
I took the /root from a working computer and used that to replace my old one and everything seems to work. I talk to a professor at the school I go to and he had mentioned something about the inodes but he didnt have a solution to my problem. Thanks for all your help rmjokers and steve.horsley.  I was wondering if let say I were to use what steve said about deleting the /root dir and just redoing my e2fsck would that create all missing files needed to operate my machine.

Steve I think you are right I think i had done a e2fdsk and not the e2fsck...the rreason I wanna know about the delete and redo over is because I am not sure if the /root that I used to replace my /root is how much different there is from what my old /root was and if there is a difference then there may be some applications that willn ot work properly...Or are all /root directorys the same.(i dont think they are, but what do i know Im here because I ruined my /root directory in the first place.) 

rmjokers as to what you had mentioned about there may be some indications of other issues with my filesystem or hardware. I did have an error that lead me to a check disk inside a failsafe terminal (this failed to) but from here I was able to maually run the e2fsck which I think accidentlly I did the e2fdsk.  but how do I tell if there is a hardware or filesystem error. Is there a solution through the terminal.
Thanks
Brian

---

### Post by rmjokers on 2006-01-27
There shouldnt be anything important in the /root directory.  It is just the home directory of the root user...and since you probably dont operate as this user very often, if ever considering Ubuntu disables it, it should have been practically empty.  If you ran a filesystem check and everything appeared OK, I wouldnt worry about it for now.  Just make sure you are backing up any important information on the drive...which is a good habit anyway.

---

### Post by bfonseca on 2006-01-27
Thanks for your help.
Brian

---

