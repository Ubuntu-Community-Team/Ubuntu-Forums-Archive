---
title: "Trouble with MATLAB installer"
date: 2010-10-11
forum: General Help
---

### Post by SCUEY on 2010-10-11
Hi, I'm trying to install MATLAB on Ubuntu 10.10 and am having trouble getting the installer script to run. I am using these links as a reference (after trying the MATLAB manual):

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)
[http://linux.dsplabs.com.au/forums/u...ubuntu-t8.html](http://linux.dsplabs.com.au/forums/u...ubuntu-t8.html)

I have an ISO, installation key, and license.dat.txt file from my university. I have placed the licence.dat.txt file in my installation directory as the second link suggests.

The result is that I run the install script and it does nothing. I cannot even run ./install -h to see the help, so something is wrong.

Here are the exact steps I'm taking:

sudo mkdir /mnt/MATHWORKS_R2010A
sudo mkdir /opt/matlab
sudo mount /<path to my ISO> /mnt/MATHWORKS_R2010A -o loop
cd /opt/matlab
sudo sh /mnt/MATHWORKS_R2010A/install



I've also tried changing the permissions of the /mnt/MATHWORKS_R2010A folder to the most favorable possible. No luck.

Any ideas? Thanks.

---

### Post by 3Miro on 2010-10-11
Do you get any error messages?

MATLAB uses java, make sure to install Ubuntu-restricted-extras (I am not sure about the exact package within the extras).

PS can you run the script as a regular user (use nautilus to go to /mnt/MAT... and then right-click on install to tell it to run) As a regular user you can only make it install into your /home/you folder, so you probbaly don't want to do the entire installation, however, it will e good to know if it at least starts.

---

### Post by SCUEY on 2010-10-11
No, it did not give me any error messages.  I do have ubuntu-restricted-extras installed.

---

### Post by SCUEY on 2010-10-11
So I just tried this: mount the ISO to a folder and then copy the folder's contents to a new folder before running install.  Still no luck.  Note when doing this I had issues copying all the files - it said input/output error as the reason.

Anyway, my problem is still the same: any time I try to run the install script, it just does nothing and gives me no feedback or errors.

---

### Post by SCUEY on 2010-10-11
OK, now I think I've realized what the problem is.  When I mount the ISO, it extracts the ISO into the folder it's mounting to.  But then I don't have execution permissions.  When I sudo chmod 777 the folder it's mounted to, it tells me it's a read-only file system.

Also, I'm wondering if I need to specify my licence BEFORE running the install script.  The matlab installation instructions do not specify this, and everyone else's instructions are just very simple as in the first two links I provided, so I don't know.  

Please let me know if you have any insight on this!

Thanks.

---

