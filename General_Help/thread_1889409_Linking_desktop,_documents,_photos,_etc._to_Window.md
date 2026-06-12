---
title: "Linking desktop, documents, photos, etc. to Windows folders?"
date: 2011-12-01
forum: General Help
---

### Post by derekcentrico on 2011-12-01
I've been reading about methods for linking Ubuntu and Windows so that you can access files and operate between the two systems on one machine seamlessly.

Most people say the same about Documents, Photos, Videos, and Music.  Create a separate partition for all of those files and modify the libraries on Windows to reflect it while deleting the folders on Ubuntu and creating a system link to the NTFS partition.

But, nobody has discussed the Desktop files.  How could I go about having Ubuntu link to the desktop folder in Windows instead of using its own "desktop" folder?  Could I just delete the folder in Terminal and create a symbolic link?

For that matter, if anyone has suggestions on mirroring the data folders between Ubuntu and Windows on one machine without replicating each file, please share.

---

### Post by Mark Phelps on 2011-12-01
> **derekcentrico said:**
> How could I go about having Ubuntu link to the desktop folder in Windows instead of using its own "desktop" folder? 
If your plan is to use a common "home" directory between Ubuntu and Windows -- DON'T!

The two filesystems use completely different permissions.  Writing into the "home" files from the "other" OS risks corrupting the filesystem and rendering the "other" OS unbootable.

---

### Post by derekcentrico on 2011-12-01
Do you have any advice on how to go about utilizing the OS's together to allow easy access to files back and forth?

Personally, I don't do the dual boot thing anymore anyway.  But, I want to convert my wife over to Ubuntu.  She won't just jump ship immediately, so I figured this sort of integration would work best.

EDIT:  duplication of files will just cause disk space to eat up fast.

---

### Post by Basher101 on 2011-12-01
you can link those together ([COLOR="Red"]except[/COLOR] [COLOR="Red"]/home[/COLOR], [COLOR="Green"]/music, documents etc are fine[/COLOR]) _**BUT**_ you need to place those shared folders on its own NTFS partition or you will render Windows or Linux unusable.

---

### Post by derekcentrico on 2011-12-01
> **Basher101 said:**
> you can link those together ([COLOR="Red"]except[/COLOR] [COLOR="Red"]/home[/COLOR], [COLOR="Lime"]/music, documents etc are fine[/COLOR]) _**BUT**_ you need to place those shared folders on its own partition or you will render Windows or Linux unusable.

Ah yeah, definitely.

I figured I'd split her disk as such:
Windows OS NTFS - 50GB
Ubuntu OS EXT4 - 100GB
Data Partition NTFS - 500GB
(leaves about 100GB for partition expansion as needed)

I'd modify Windows profiles to be on the data partition.  Then, I figured I'd just do "ln -s" on Ubuntu for all of the personal folders in the /home/user/ directory structure to the data partition on NTFS.

Would this be feasible?

I.e.:
/home/user/desktop is linked using ln -s to e:\users\desktop on the NTFS which would be mounted to whatever mount point.  I know the path would look different...maybe /media/datapartition/users/desktop...

---

### Post by ajgreeny on 2011-12-01
I can't comment about windows beyond XP, so will leave that to others, but if all ther data files that your wife uses are in the separate partition, you will never need 100GB for the / partition of ubuntu; 10 - 20GB should be plenty.

To save possible partition overload (a max of 4 primary, or 3 primary + 1 extended are possible with standard ms-dos MBR formatting) I suggest you install all of ubuntu, the root and swap and /home, if you have that separate, but with shared data that is not really necessary, in logical partitions within the one extended partition;  it makes life so much more flexible.  You will need to make sure that the ntfs partition is mounted at boot every time with ntfs-3g, so make sure that is installed.

Once you have done that, from ubuntu you can drag and drop the folders in the shared data ntfs partition into your ubuntu home folder in nautilus using the mouse middle button, and choose "Link here" when the menu appears.

---

### Post by derekcentrico on 2011-12-06
So far so good with symlinks to a data partition.  I used 20GB for Ubuntu and 50GB for Windows.  The rest of the disk is for Data.

However, I've run into what I consider to be an annoying circumstance.  Every folder, including the Ubuntu desktop, will show .lik and .ini files.  

Does anyone know if it's possible and how to hide these Windows-driven files that have no use in Ubuntu but to annoy the hell out of the user?

---

### Post by asvestomix on 2011-12-06
For me a simple shortcut that target to each folder would be enough.. For example place a link into the ubuntu's folder of music that it will redirect you to windows folder of music and etc..

---

### Post by derekcentrico on 2011-12-06
Well, I'm converting the wife to Linux...so need to be a bit more Windows-ish for the time being.

Anyone know how to have Unity hide certain extensions from being viewed as it would the standard ole ".filename" method?

---

### Post by Mark Phelps on 2011-12-07
Don't have an answer to your question about hiding files based on extension ... but if your plan is to "share" the same settings files between Ubuntu and Win7 -- be prepared to have either or both start crashing when you do that.

Data files (i.e., music, video, documents, PDFs, etc) are fine, but sharing settings files is likely to cause problems between the OSs.

---

### Post by derekcentrico on 2011-12-07
I have no intent on sharing settings.  I just want to hide the Windows "settings" files such as "desktop.ini" and "thumbs.db" because Ubuntu displays them.  Windows automatically hides its settings files in all directories.  

Also, I'd like to hide *.lnk files.  So, if I could hide "desktop.ini" "thumbs.db" and all ".lnk" files, there would be no confusion for my wife I'm sure.

Any thoughts?

---

