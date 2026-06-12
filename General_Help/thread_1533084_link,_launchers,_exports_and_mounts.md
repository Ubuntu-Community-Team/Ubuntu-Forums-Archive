---
title: "link, launchers, exports and mounts"
date: 2010-07-17
forum: General Help
---

### Post by Simon Cropper on 2010-07-17
Hi,

I am getting the hang of Ubuntu/Linux but still wondering about links, launchers, exports and mounts. What are they, how do they differ and when should they be used.

:D I use exports to connect directories between two of my Ubuntu machines (NFS).

:D I have created launchers on my desktop pointing to a directory or file.

:D I have mounted disks to directories.

Are all these things just symlinks or do they fundamentally differ in some way?

I also have come across the "ln" command but am unclear how this differs from any of the above.

Another good example that confuses me :confused: is the "Examples" directory in everyones home folder. This is a link of some sort but I can't seem to see where it is defined. It is not in fstab or exports configuration files.

Does anyone understand what all these things are, how they relate and which should and which shouldn't be used?

Any information and explanation would be appreciated.

Simon

---

### Post by agnes on 2010-07-17
If you create a launcher on the desktop to an application, file or  directory, Ubuntu creates a .desktop file.
Go in a Terminal, go to the ~/Desktop directory, type "ls -al", you can see it are .desktop files. You can view the contents by typing e.g. "gedit your_file_name.desktop". The entries in your menu are also made of .desktop files. More [here]("http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/").


If I recall correctly the ~/Examples directory is a soft symbolic link to a  directory also called Examples on another place in the system. You can see if it's a soft link in the Terminal, if you type "ls -al" there will be a "l" before the permission-letters indicating it's a soft link. And it states where it points to. 
The "ln" command will make a "hard" link between two files (is unable to do that for directories) so that editing one will also edit the other. "ln -s" makes a soft link, a pointer to a file or directory.
Basically you could make a soft link on your Desktop instead of a .desktop file e.g. "ln -s /home/my_name/Downloads /home/my_name/Desktop/Downloads"

Both things are different from mounting a disk to a directory.
fstab is for mounting devices at startup.

---

