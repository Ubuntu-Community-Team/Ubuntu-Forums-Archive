---
title: "Where are user folders hidden ?"
date: 2010-05-18
forum: General Help
---

### Post by Amused2Death on 2010-05-18
I had a minor disaster and lost a lot of data. I used PhotoRec to see what it could recover, it saved them to my home directory.

488 folders i cant do anything with as i dont have permission?? i set up root and gave myself admin power but still cant delete them.

If i log in as root, where can i find my home folder so i can delete the majority of these folders. Most unfortunately have nothing of value in them.

Cheers

---

### Post by KdotJ on 2010-05-18
Are the folders all in one folder? If so, go to the terminal and change directory to the folder above the photo folder. 

Eg. If the photo folders you wish to delete are in /home/your_name/Pictures/recovered , then cd to /home/your_name/Pictures
then if you want to delete the recovered folder, type 

```
sudo rm -rf recovered
```

or are the folders just all sitting in your home directory?

---

### Post by Swagman on 2010-05-18
press alt & f2 and enter 

```
gksudo nautilus
```

navigate to dir with uber privs

**Warning.. Now you can really stuff up your system with great gusto.**

---

### Post by revidnus on 2010-05-18
Be carefull using the (rm) command you can wipe out everything and it won't be pretty!

A few commands you can use in terminal to find out where the files are;

pwd (print working directory) where you are at now.
ls list the files in directory.
ls -l (will show the permissions)
ls -la (will list all files) hidden files
cd /(name of directory) to change to the directory
cd ~ to move back to home directory

---

### Post by Amused2Death on 2010-05-18
PhotoRec simply put all the folders in my [username] home directory. 
Even with admin power it refuses to let me do anything with them as i dont have permission, they all belong to root. Strange since i ran Photorec under my [username].

I can't stuff anything up more than it is, i presently have 2 hdd's one 500 gig and one 200 gig, both with Ubuntu Lucid installed and nothing else. SATA order in bios is what makes the 500's OS boot and the data i was trying to recover is on the 200.

A small percentage of data was recovered, and i would like to be able to save it off before blowing away the hdd's and starting again.

This brings me back to the beginning, i dont have permission to do anyting with it, and as root i dont know where my [username] home folder is hidden.

I can, login as root and rerun the program if all else fails i suppose.

---

### Post by mike555 on 2010-05-18
if your looking for home folders in Ubuntu go to Places > computer (or the partition your trying to get to) > File system > Home ............ the users home folders should be there .

---

### Post by revidnus on 2010-05-18
Changing permissions on directories can be tricky. If your not sure what your doing you might not get what you expected and end up preventing access to files and subdirectories accidentally.
If you have a lot of data to recover from a second hard drive you may want to invest in a Multi-function cable. One cable for 2.5"/3.5"/5.25" IDE/SATA Device. Brand Name for it is (coolgear).
Mine cost about $35.00 but I saved data from two hard drives with it. Large files that would have been hard to otherwise. I also set up a raid drive with it.

---

### Post by Amused2Death on 2010-05-19
Thanks, in front of my face, .... can't see the wood for the trees syndrome

---

### Post by revidnus on 2010-05-19
Here is the message that has just been posted:
***************
i am looking for the home folder, but i need to find [username] home folder when i'm logged in as root
***************

If you need to find the home folder when you log in as root this is what I do.
type sudo -i to log in
After typing password in terminal as root you are probably at the /root
(directory) you can type pwd to find out.
Type cd /home/yourusername hit enter
type pwd
you should be at the /home/yourusername

---

