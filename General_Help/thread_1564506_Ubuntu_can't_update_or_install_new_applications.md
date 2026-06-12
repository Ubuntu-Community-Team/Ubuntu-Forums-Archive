---
title: "Ubuntu can't update or install new applications"
date: 2010-08-30
forum: General Help
---

### Post by trunkmonkeytoo on 2010-08-30
I have been trying to update Ubuntu, and install applications, but for some reason, when I go to the update manager, it says "It is unknown when the package information was updated last." and shows an error message, that says the repository indexes could not be downloaded, and shows this.

```
E: Could not open lock file /var/lib/apt/lists/lock - open (20: Not a directory)
E: Unable to lock the list directory
```How can I fix this so I can update Ubuntu and install software from the software center?

---

### Post by arpanaut on 2010-08-30
This is usually the error msg. when more than one package manager is open.
Close all apps. i.e. Synaptic, update manager, software center. 
Then try to run Update manager again, selecting check first.

Post any errors.

---

### Post by trunkmonkeytoo on 2010-08-30
Here are some screenshots of what it does.

[IMG]http://ubuntuforums.org/picture.php?albumid=1992&pictureid=6691[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=1992&pictureid=6692[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=1992&pictureid=6693[/IMG]

---

### Post by arpanaut on 2010-08-30
Weird...
Have you checked your Software Sources?  System>Administration.Software Sources.
Since you installed have ever been able to update or install anything?

In software sources try to change the server you Download from:

---

### Post by trunkmonkeytoo on 2010-08-30
When I first installed Ubuntu on my laptop, I was able to install packages while connected to the internet with a cord, because at the time my wifi card didn't work with Ubuntu, I was able to update and install software, but not after my wifi card started working with Ubuntu.

And in Software Sources, mine is set for the "Server for the United States" but there is another option, the Main Server. Should I use that one?

---

### Post by arpanaut on 2010-08-30
Yeah goathead and try that it might shake out some cobwebs.

Strange that you can access the net with wifi but not updates etc.

Try Applications>Accessories>Terminal:

```
Sudo apt-get update
```
and post the result.

---

### Post by trunkmonkeytoo on 2010-08-30
It came out with 

steve@ubuntu:~$ sudo apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (20: Not a directory)
E: Unable to lock the list directory
steve@ubuntu:~$

---

### Post by arpanaut on 2010-08-30
Okay I've done some searches on this issue. It seems that the solution is to
remove the lock file, then to reboot then run updates.
The lock file will be reproduced when updates are done so no worries.

Just explaining as using the rm command can cause problems if not used correctly.

So in the terminal: cut and paste

```
sudo rm /var/lib/apt/lists/lock
```

Then reboot, come back here and run:

```
sudo apt-get update && sudo apt-get upgrade
```

And hopefully things will be good to go.
Let us know...

---

### Post by trunkmonkeytoo on 2010-08-30
I put in the first code, and this came up...

steve@ubuntu:~$ sudo rm /var/lib/apt/lists/lock
[sudo] password for steve: 
rm: cannot remove `/var/lib/apt/lists/lock': Not a directory
steve@ubuntu:~$ 

Now I'm going to restart and put in the other code.

---

### Post by trunkmonkeytoo on 2010-08-30
After restarting and putting in the second code, I got this...

steve@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for steve: 
E: Could not open lock file /var/lib/apt/lists/lock - open (20: Not a directory)
E: Unable to lock the list directory
steve@ubuntu:~$

---

### Post by Miljet on 2010-08-30
I ran across this thread in another forum. It indicates that somehow the "partial" directory has been changed to a file. You can check this by running 
```
ls -l /var/lib/apt/lists
```
Find the entry for "partial". It should look like this
```
drwxr-xr-x 2 root root     4096 2010-08-30 12:45 partial
```
If the first letter is a d, then this is not your problem. However if the first entry is a dash (-), then you need to follow these instructions.
```
For those who are having this problem and can't understand whats up, I was able to fix it by deleting the partial "file" and replacing it with a partial "directory", commands as follows:

## to get to the directory

cd /var/lib/apt/lists/

## to remove the partial file (no directory was present)

sudo rm partial

## to create the partial directory

sudo mkdir /var/lib/apt/lists/partial

AND............it worked.
```
Here is the link to the entire thread:  [http://ubuntuforums.org/archive/index.php/t-217744.html](http://ubuntuforums.org/archive/index.php/t-217744.html)

I just checked mine and /var/lib/apt/lists/partial is indeed a directory. And it is completely empty. And /var/lib/apt/lists/lock is a file, as it should be.

---

### Post by trunkmonkeytoo on 2010-08-30
With ls -l /var/lib/apt/lists, I get this...

```
-rwxr-xr-x 1 root root 86828 2010-03-12 02:05 /var/lib/apt/lists
```So I'll go by what you posted, and see if that works, and post the outcome. Thanks!

---

### Post by trunkmonkeytoo on 2010-08-30
I went through those commands in the terminal, and this is the outcome.

```
steve@ubuntu:~$ cd /var/lib/apt/lists/
bash: cd: /var/lib/apt/lists/: Not a directory
steve@ubuntu:~$ sudo rm partial
[sudo] password for steve: 
rm: cannot remove `partial': No such file or directory
steve@ubuntu:~$ sudo mkdir /var/lib/apt/lists/partial
mkdir: cannot create directory `/var/lib/apt/lists/partial': Not a directory
steve@ubuntu:~$ 
```I'll see if I can update now, but it doesn't look like it worked...:(


ADDED ON:

I am still unable to update...

---

### Post by arpanaut on 2010-08-30
Sorry Man!

I thought for sure that was going t work, 
I'm at a loss now, Hopefully someone will come around 
who knows the cure.  I'll keep looking.

Later...

---

### Post by trunkmonkeytoo on 2010-08-30
That's okay. If I can't get it working, I'll just reinstall it, because my main use is for school, and video/audio creation and editing, and once I finish a project, I back it up in Windows, so to reinstall wouldn't be a problem if it's the only way to fix this. 

Thanks for helping me with this problem! I'll look for a solution for a while, before I go and reinstall it, and if I find something before that, I'll be sure to post it! ;)

---

### Post by wojox on 2010-08-30
Try

```
sudo rm -rf /var/lib/apt/lists
```

---

### Post by Miljet on 2010-08-30
It sounds like your /var/lib/apt/lists is not a directory. So take this one step at a time. First run 
```
 cd /var
ls -l
```
Make sure that you have a directory called lib. If so run
```
 cd lib
ls -l
```
Make sure that you have a directory called apt. If so run
```
cd apt
ls -l
```
Make sure that you have a directory called lists. I am beginning to think that here is where you will find the problem. If you do not have a directory, let us know and we will help create one. In case you do have a directory called lists, run
```
 cd lists
ls -l
``` and post the results here.

---

### Post by Miljet on 2010-08-30
It sounds like your /var/lib/apt/lists is not a directory. So take this one step at a time. First run 
```
 cd /var
ls -l
```
Make sure that you have a directory called lib. If so run
```
 cd lib
ls -l
```
Make sure that you have a directory called apt. If so run
```
cd apt
ls -l[/code
```
Make sure that you have a directory called lists. I am beginning to think that here is where you will find the problem. If you do not have a directory, let us know and we will help create one. In case you do have a directory called lists, run
```
 cd lists
ls -l
``` and post the results here.

---

### Post by Miljet on 2010-08-30
Sorry for the double post. Anytime that you try to cd to a subdirectory or list the contents of a subdirectory and get the "No such file or directory" message, work your way down the path to see where the path is broken. Then you are not just shooting in the dark.

---

### Post by Miljet on 2010-08-30
It looks like the /var/lib/apt/lists directory should contain an empty file called lock and an empty directory called partial. Everything else in there seems to be copied from your /etc/apt/sources.list and will probably be added automatically.

---

