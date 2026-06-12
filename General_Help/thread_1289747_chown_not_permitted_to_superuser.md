---
title: "chown not permitted to superuser"
date: 2009-10-12
forum: General Help
---

### Post by SuperRook on 2009-10-12
I have a unique environment where I use the superuser "dbuild" to create a directory called /views. I do chown dbuild /views. Now I have to create a sub-directory to /views called /views/myclient.  I chown myclient /views/myclient. I ssh in as myclient to sync my source files and I ssh in as dbuild to build. A build script that I have no control over is attempting to chmod a file in a sub-directory of myclient. The result is permission denied which causes the build to Error. Is there a way to give dbuild superuser permissions in myclient such that no password is required and chmod w/o sudo prefix will work? I was told that I can edit the etc/sudoers file using sudo visudo to accomplish this. I have added the following lines but still nogo:
Defaults: dbuild !authenticate 
dbuild ALL = NOPASSWD: ALL

Any help would be greatly appreciated. 
Thanks

---

### Post by penguintutor on 2009-10-12
What do you mean by dbuild being a superuser? Do you mean this is the root user (ie. UID & GID = 0 - in which case it would have full root permissoins) or do you just mean part of an admin group etc? In a normal set-up you only have one superuser called root, all the others are just users with additional privilages / group membership.

The sudoers file will not have any affect unless using sudo. You will need to prefix running the build script with sudo to elevate privilages. Ie if you run the script with elevated permissions then the call to chmod will also have those privilages.

---

### Post by SuperRook on 2009-10-13
dbuild is the name of the group that myclient is a member of. Sorry for the confusion. I tried starting the build script with sudo and it will not run.

---

### Post by penguintutor on 2009-10-13
Ah that's clearer now.

What error message do you get trying to run the build script using sudo? Normally most programs will run with elevated privilages using sudo (there can be problems using scripts as suid, but should not have those with sudo). It's possible that the script is checking to see if you are an appropriate user to run the build.

What is the chmod command trying to do?
To change most permissions using chmod then you need to be the owner of the file (or root). Perhaps being a member of the dbuild group is not enough - if the file is being created as user dbuild then maybe you need to run as that user not just be a member of the group. 

sudo can be used to run as any other user (not just the superuser) so that may be an avenue worth exploring. 

eg.
sudo -u dbuild <command>

Other than that it is going to be difficult to fix without seeing the what the build script is doing.

---

### Post by SuperRook on 2009-10-14
The command that I normally enter is "bc all".
When I enter "sudo bc all" it returns "File all is unavailable" The script most likely parses the parameters and adding a third parameter causes this failure.
 
the offending command is:
 
 @chmod +x ./$(GEN)

where :
 GEN=ap_gen

The frustrating part is that ap_gen already has exicutable attributes as retrieved in perforce so the chmod is unnecessary.
 
**To change most permissions using chmod then you need to be the owner of the file (or root). Perhaps being a member of the dbuild group is not enough - if the file is being created as user dbuild then maybe you need to run as that user not just be a member of the group.** 
 
I am logged in as dbuild which is the group name. myclient is a member of dbuild. dbuild owns the directory /views. myclient owns the sub directory /views/myclient where the source files exist and where the build scripts are located.
 
**sudo -u dbuild <command>**
same results as sudo
 
I can get the command chmod to work if I enter:
sudo chmod +x ap_gen
 
I need to be able to do this without adding "sudo"

---

### Post by SuperRook on 2009-10-19
Bump

---

### Post by SuperRook on 2009-10-29
Bump - Again.

---

