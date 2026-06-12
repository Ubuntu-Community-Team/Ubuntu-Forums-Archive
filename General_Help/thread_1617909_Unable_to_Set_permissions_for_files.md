---
title: "Unable to Set permissions for files"
date: 2010-11-09
forum: General Help
---

### Post by Jabez on 2010-11-09
I am using Ubuntu 10.10 Meerkat and everytime I attempt to edit the permissions of a file either using the command line or gui it does not stick. When I use the gui and click in the permissions tab and then choose execute file the check mark appears and then immediately disappears.

When I attempt to change permissions via the command line and execute a script even if the script was created by me it does not work and when I check the permissions there is no changes from the original before my attempt to add execute permissions.

Even when I change permissions for read and write they don't stick.

I had no problem when I was using 10.04 and need to get this fixed.

PS. I made sure I am changing permissions using root privileges.

---

### Post by dogbite3000 on 2010-11-10
Im having a similar problem.  I try to access files on my c: drive , but, ill right click on the drive after it is mounted, and it says "The permissions of "F000D02400CFEFA0" could not be determined." 

I would like to do this mainly so i can run .exe files, such as winamp or games without having to install 2 copies on the same hard drive.

Id like to figure this out, even when i copy paste the files from the drive to my linux portion,i will try and edit their permissions.  When i do so, the GUI ill click executable, it automatically unchecks its self.

Any tips be great!!! thanks =]

---

### Post by dogbite3000 on 2010-11-11
A quick note, my Hard drive is internal, and its in ntfs format.

Any suggestions?

---

### Post by garuhhh on 2010-11-11
have the same problem :(
still waiting for any answers..

there are a lot of threads with similar problems, but theirs is more on adding "executability" to their files. same case, the drive is on windows partition, and they can't change any of the permissions, even using command line, or GUI. No solution found yet.

This problem i think started with Ubuntu 10.10

---

### Post by dogbite3000 on 2010-11-18
Bump...

Still unable to do things, nor can i open the ntfs-config gui under the systems tab.  Am i doing it wrong?

---

### Post by dogbite3000 on 2010-11-18
So i found a solution to my problem, but it really is just a work around.  Instead of setting permission after mounting, if you mount the drive on boot up, its permission will be set, with everything being read/wright executable. 

I used this guide to do it. 

[http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Auto-Mount-Drives-at-System-Startup](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Auto-Mount-Drives-at-System-Startup)

---

### Post by asmoore82 on 2010-11-18
DOS filesystems cannot store UNIX ownership and permissions.

---

### Post by galvatron408 on 2010-11-18
I had that problem with a file that I downloaded too. KDE wouldn't allow the permissions to stick so I said.... wanna bet... and typed "sudo chmod 755 file" and it was done.

---

