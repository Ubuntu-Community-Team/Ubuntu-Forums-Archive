---
title: "Issue with shared folder..."
date: 2009-10-10
forum: General Help
---

### Post by kfitzenreiter on 2009-10-10
What I'm trying to accomplish is to give all my windows machines access to the fourth partition on my ubuntu box.
 
First I created the directory /home/kurt/Desktop/mycomputer/sda4 as a regular user.
 
Second I "sudo apt-get install samba".
 
Then I edited /etc/fstab and entered a line reading...
 
"/dev/sda4 /home/kurt/Desktop/mycomputer/sda4 vfat user,auto,fmask=0111,dmask=0000 0 0" 
 
doing so as root.
 
Then I right click the sda4 folder to set up sharing, but this requests an edit to 
the file /etc/samba/smb.conf. First of all, I forgot to mention setting the "workgroup=Mshome". But also, I add "usershare owner only = False"
 
The problem comes when I try to go in from windows xp. It gets to the folder okay but then asks for a user name and a password. I enter the names from the ubuntu box but it rejects it. I even tried "sudo smbpasswd -a username" but this did not solve the problem.
 
Any thoughts???

---

