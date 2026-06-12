---
title: "I think I lost my home folder"
date: 2011-05-25
forum: General Help
---

### Post by unbuntunewb on 2011-05-25
Last night I tried to configure sftp using this guide.

 [http://blog.markvdb.be/2009/01/sftp-on-ubuntu-and-debian-in-9-easy.html](http://blog.markvdb.be/2009/01/sftp-on-ubuntu-and-debian-in-9-easy.html)

unfortunately this did not work. When I restarted my computer I was greeted with an error saying it cannot find ICEauthority file, then another error saying I had a 256 sanity problem, and finally nautilus could not find my home directory. After some poking around I managed to get a desktop back, granted its bare bones and I have no access to my data, the desktop looks as it did after a fresh install. When I restart the computer I still get the ICEauthority error at login. Another interesting thing to note is that when I hit ctrl alt f1 and log into my user name I get a message saying I am not the owner of that encrypted folder.

Please does anyone know how to get my own home folder back? I have half a terabyte of stuff on there Id rather not let go.


Thank you.

---

### Post by hwttdz on 2011-05-25
Update: I just looked at those instructions, they look ridiculous.  Hold on one minute, should be ok, but that has to be the craziest tutorial ever.  

Update 2: in steps 7 and 8 you 1) gave ownership of your home directory to root.  This is weird, root doesn't need to own stuff to have permissions on it, you give things root ownership when you don't want other users screwing with them.  2) you changed your home directory to /, this doesn't make any sense, as you would either not have permissions to edit files in your home, or you would and you might screw up all sorts of system files.  
So what you need to do is change your home back to /home/username, and give ownership of /home/username back to username:username.  
So undoing step 7:
sudo chown username:username /home/username
and undoing step 8:
sudo usermod -d /home/username username

Update 3: Make sure you understand what you're doing when you're running commands, especially sudo commands.  This is less true if it's coming from a trusted source, i.e. I regularly allow things from the repository to run without checking everything out, i.e. I trust that Canonical isn't going to put something ridiculous in /usr/bin/sudo so I don't have to check the file every time it gets updated.  And for that matter I don't have to read the source of every package I'm updating before I update it.  But if joe-schmoe tells you run this command "sudo do-crazy-stuff" you better know what do-crazy-stuff does.  In general you can run "man do-crazy-stuff" and see what it's doing.  So you can see in undoing step 7, according to the man page, I am asking you to give yourself ownership of /home/username.  And in undoing step 8 I am asking you to use /home/username as your home directory.  

I'd do alt-ctrl-f1 and "cd /home" and then "ls" and see if your home directory is there.  If it is, no big worries.  It's probably that you're logging in as some other user or your home directory somehow got changed.  Do you have home on a separate partition?  All all your drives still being mounted correctly?  What does /etc/fstab look like?

---

### Post by unbuntunewb on 2011-05-25
I do not have separate partitions. I will have to check the other things later as I am heading out the door to go to work. Will be back at 5pm eastern time. Thank you for taking a look. I appreciate it.

---

### Post by zealibib slaughter on 2011-05-25
If you followed that tutorial step by step then you did the following.
 
```

[FONT=georgia]Step 7: Pass ownership of peter's directory you want to be sftp accessible to the superuser:[/FONT]
[FONT=Courier New]mark@neuskeutel:~$ sudo chown root.root /home/peter[/FONT]
[FONT=Courier New]which changed ownership (chown) to the root user

```[/FONT]
[FONT=Courier New]```
[/FONT][FONT=Courier New]

[/FONT][FONT=georgia]Step 8: Now we change peter's home directory (normally /home/peter) to /:[/FONT]
[FONT=Courier New]sudo usermod -d / peter[/FONT]
[FONT=Courier New]which changed your home directory to /user instead of /home/user[/FONT]


```
 
To fix this reverse these two steps with
```
 
sudo chown username /home/yourusernamehere
and 
sudo usermod -d /home yourusernamehere

```
 
I believe this should get your home folder back.
Here is the man page for usermod [http://linux.die.net/man/8/usermod](http://linux.die.net/man/8/usermod)
and the man page for chown [http://linux.die.net/man/1/chown](http://linux.die.net/man/1/chown)
Hope this helps

---

### Post by unbuntunewb on 2011-05-25
Hi everyone just checking in from work. Thanks for your tips. I have a question though. Do I run these commands in the terminal on the desktop, or should I put them in when I ctrl alt f1, or should I put them in when in recovery mode?

Thanks again.

---

### Post by zealibib slaughter on 2011-05-25
either with terminal or at the virtual terminal at ctrl+alt+f1.

---

### Post by unbuntunewb on 2011-05-25
I did the following 

> **zealibib slaughter said:**
> 
[/CODE]To fix this reverse these two steps with
```
 
sudo chown username /home/yourusernamehere
and 
sudo usermod -d /home yourusernamehere

```

this was the output

```
nunya@nunya-desktop:~$ sudo chown username /home/nunya
[sudo] password for nunya: 
chown: invalid user: `username'
nunya@nunya-desktop:~$ sudo chown nunya /home/nunya
nunya@nunya-desktop:~$ sudo usermod -d /home nunya
usermod: user nunya is currently logged in
nunya@nunya-desktop:~$ 


```


upon reboot I am no longer greeted with any errors but I am still missing all my data and my settings are basic as if it is a new install. How do I retrieve my old settings/data?

---

### Post by unbuntunewb on 2011-05-25
I found this within my file system, I am not sure what it is.

---

### Post by unbuntunewb on 2011-05-25
about the previous images I posted. I did what the text said and this was the outcome. Also it wants a passphrase? I didnt set any passphrase, its not my sudo password that much I know

---

### Post by unbuntunewb on 2011-05-25
I am rather certain that my files are in this protected "private" folder with the X on it. I cannot seem to gain access to it though. I am prompted I do not have permission.

---

### Post by unbuntunewb on 2011-05-25
Using GKSudo launcher I managed to make myself the owner of the Private folder, however everything in it is still encrypted as can be seen in the pic. I was correct this IS my stuff, I recognized a photo that showed up from my proper desktop. How do I decrypt this so I can save what i want and just wipe this clean and start over?

---

### Post by zealibib slaughter on 2011-05-25
try this
```
sudo chown -r nunya /home/nunya
```
the -r makes it recursive or maybe its -R (yes there is a difference) but either with a lowercase or uppercase r this should remove the ownership restrictions.

---

### Post by backu on 2011-05-25
> **zealibib slaughter said:**
> try this
```
sudo chown -r nunya /home/nunya
```
the -r makes it recursive or maybe its -R (yes there is a difference) but either with a lowercase or uppercase r this should remove the ownership restrictions.

This won't do any good. This only changes ownership of the files, not decrypt them. 

OP - Did you install Ubuntu with the encrypt home folder option? or encrypt the folder later?

---

### Post by unbuntunewb on 2011-05-26
I accidentally encrypted my home folder instead of creating an encrypted sftp folder. However I managed to fix this. I installed GKSudo launcher because I could not access the folder "Private" even in nautilus. The Private folder contained my old home folder. Using GKSudo launcher I was able to browse the entire filesystem as root. In GKSudo launcher I changed the permissions from the Private folder from root to my username then checked it again. Low and behold it was no longer restricted, however everything was still encrypted. I decided to try and mount the ecryptfs file (my home folder) and BAM, I had gotten my data unencrypted. I backed it up just in case. this is a pic of the moment everything came together, what you see is my original home folder made available to me again. After I backed up my data I restarted my computer and just like that my old desktop returned to me. I did lose 50 gigs of music by accident, but I kept 300 gigs of video so I take that as a win.

Thank you everybody for your help

---

### Post by caravaggisto on 2012-03-25
Congrats on saving your stuff! I have a similar problem; I recently booted up my computer to find my home folder encrypted, even though I'd never set up any such encryption. 

Quick question about something you said:

> **unbuntunewb said:**
> I decided to try and mount the ecryptfs file (my home folder) and BAM, I had gotten my data unencrypted.

What do you mean by the "ecryptfs file" that you mounted? Is that some sort of mount point somewhere that you mount with the "mount" command, or did you use "ecryptfs-private-mount"? If so: (1) did you do these functions as root or as your normal user self and (2) were you working from a live CD / USB setup or were you booted on the hard drive with your data, as usual?

Since your solution worked for you, I want to do exactly what you did! I have no idea how my home folder became encrypted. Indeed, I didn't even know the service / phenomenon existed until I found myself in this situation. I'm worried that I won't be able to mount my data without a mount password for ecryptfs-private-mount. I never set up the encryption, and as such I have no mount password. I've read something about a "wrapped-passphrase" file in /home/username/.ecryptfs/, but I don't know if I have that or not (I'm currently on another machine...).

I'm double-backing up my data this evening... then I'll play around. Until then, I want to learn about this problem as much as possible. Thanks, and I'm happy for you that you fixed your encryption issue!

Best,

caravaggisto

---

