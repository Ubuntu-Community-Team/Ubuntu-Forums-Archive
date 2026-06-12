---
title: "changing ext hd  ownership from root to user"
date: 2010-04-17
forum: General Help
---

### Post by dskyracer on 2010-04-17
I just got a 1.5 terrabyte  Western Digital My Book 1110 external usb 2 drive. I used Gparted to reformat the drive to ext3. The problem I have is I can't change the file permissions for the drive because it says the drive is owned by root. I can't back up my files into the drive because it won't allow me to. 

I am using Jaunty Jackalope and got this drive to back up my files so I can feel comfortable in upgrading to Karmic Koala in case there are major problems with the upgrade. 

I know someone out there in the community can tell me the commands to use in the terminal to let me gain ownership of this external drive from root so I can copy my files into it. 

 the entire drive itself is seen as /dev/sdb

One meg of the drive is unallocated and the part of the drive that I reformated  is seen as /dev/sdb1

my personal files are owned by the name of dave

Can someone give me the command to get dave to own the new external drive instead of root? Thanks for the help.

---

### Post by nitstorm on 2010-04-17
1.type ```
gksudo nautilus
``` and the file manager will open up.
2. navigate yourself to the drive, don't enter any sub-folders on the drive
3. right click and click on properties
4. go to the permissions tab
5. change the permissions as required to the username you want

now u should be able to use the drive

hope this helps, this worked on my partition that denied me permission

cheers!

---

### Post by colorlessprism on 2010-04-17
sudo chmod 777 -r <mount point>

---

### Post by Bachstelze on 2010-04-17
> **colorlessprism said:**
> sudo chmod 777 <mount point>

No, no, no, no, **no**. The only thing that should ever be chmodded 777 is /tmp.

@OP: use chown to give yourself ownership, you can leave the permissions at they are.

---

### Post by Morbius1 on 2010-04-17
> No, no, no, no, **no**. The only thing that should ever be chmodded 777 is /tmp.Then you'd better uninstall **nautilus-share** because it does that by default. :wink:

---

### Post by dskyracer on 2010-04-17
Ok!!! this worked in that the drive had a folder called lost and found.. I was unable to change the ownship of the  entire drive itself but could change the ownership of the folder lost and found to my own from root so now I can rename that folder from lost and found to Backups and have already started to copy some files into the new external drive using that folder. There are some other issues regarding some other stuff that exists on that drive but for now I feel I can go on with backing up some stuff and will address the other issues later.. thanks so much.. Ubuntu community members are the best!

---

### Post by dskyracer on 2010-04-17
> **nitstorm said:**
> 1.type ```
gksudo nautilus
``` and the file manager will open up.
2. navigate yourself to the drive, don't enter any sub-folders on the drive
3. right click and click on properties
4. go to the permissions tab
5. change the permissions as required to the username you want

now u should be able to use the drive

hope this helps, this worked on my partition that denied me permission

cheers!

Ok I mean this worked ... I wasn't clean about what worked in my last post. sorry.. and thanks

---

