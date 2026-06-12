---
title: "installing applications without internet connection"
date: 2009-12-31
forum: General Help
---

### Post by joamon on 2009-12-31
Hi,
I am a new Linux user and am trying Ubuntu 8.10 and do not have internet connection.
Basically I found that i need 
Wine - to support windows applications 
VLC - to play mp3 and dvd
NTFS 3g - to access my 2nd HDD,
i have downloaded the tar.gz files for the above and my problems are,
1. i am not sure that they are the correct version for my OS as they require other link files to install,
eg: wine requires flex and i cannot find how to install flex.
i have unzipped flex.tar.gz and do not find a .pl file to run and i find configure etc files in it which are not executable.
2. which files are executable  and which files are not ?
some files are shown in red and blue color and what does that mean,
3. where/what path is the installed application installed to.
Please help ,or else i have to turn back to windows.
 :confused:

---

### Post by lswb on 2009-12-31
One of the easiest ways is to use Synaptic package manager to select the packages you want to install. Then from the Synaptic menu select File/Generate Package Download Script. This creates a download script using the wget command line tool that can be run on another linux box, or it is easy to print out and take it to a Windows or Mac and download the files using a web browser or ftp. You can transfer them to your ubuntu system with a thumb drive or any other convenient method.

If you copy them all to a single directory on the ubuntu system, they can be installed with the command line "sudo dpkg -iR directoryname"

---

