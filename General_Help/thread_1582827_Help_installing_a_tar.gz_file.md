---
title: "Help installing a tar.gz file"
date: 2010-09-27
forum: General Help
---

### Post by olimb on 2010-09-27
I need help using the terminal please
1.
I can change the directory to home
t2@taptop:~$ cd /home
t2@taptop:/home$
but I can’t get any further
t2@taptop:/home$ cd/home/t2
goes back to
t2@taptop:~$

2.
Trying to install a Scribus add-on file, imposition-20070820.tar.gz
t2@taptop:~$  -zxvf imposition-20070820.tar.gz
-zxvf: Command not found

t2@taptop:~$ ./configure
bash:  ./configure: No such file or directory

The imposition-20070820.tar.gz file is in the directory “home/t2”
But I can’t change the directory to “home/t2”
and  I can’t copy/paste the file from t2 to home.

---

### Post by Hakunka-Matata on 2010-09-27
if you CD to a different directory, type ls for a listing of what's in the directory, then cd again to another folder within that directory

---

### Post by mendhak on 2010-09-27
When you're here:

t2@taptop:~$

Try typing 

cd /home/

Then don't press enter, press tab. 


For your second question, you won't be able to do ./configure until you've extracted the .tar.gz.  You can right click the .tar.gz and extract it that way or you can try it via command line:


t2@taptop:~$ **tar**  -zxvf imposition-20070820.tar.gz

---

### Post by Hakunka-Matata on 2010-09-27
Once you get to t2@taptop:/home$
if t2 is a subdirectory of /home then type
cd t2
you'll switch from /home to /home/t2

---

### Post by olimb on 2010-09-27
t2@taptop:/home$ ls
t2
{the t2 displayed is in a light blue color and change directory won’t change to it}

t2@taptop:/home$ {press tab}
brings up a list of 2000+ commands, "tar" is in there but “configure and zxvf” are not listed.

---

### Post by lisati on 2010-09-27
> **olimb said:**
> 
t2@taptop:/home$ {press tab}
brings up a list of 2000+ commands, "tar" is in there but “configure and zxvf” are not listed.

You need to do what mendhak said for it to show up:
```
tar -zxvf imposition-20070820.tar.gz
```
then do the "cd" to the appropriate directory.

---

### Post by olimb on 2010-09-27
Tried from both directories I can get to
t2@taptop:/home$ tar -zxvf imposition-20070820.tar.gz
t2@taptop:~$ tar -zxvf imposition-20070820.tar.gz
same results
tar: -zxvf imposition-20070820.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: Exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

---

### Post by gandaran on 2010-09-27
> **olimb said:**
> Tried from both directories I can get to
t2@taptop:/home$ tar -zxvf imposition-20070820.tar.gz
t2@taptop:~$ tar -zxvf imposition-20070820.tar.gz
same results
tar: -zxvf imposition-20070820.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: Exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
you cant just cd to home! you have to cd to home user if the package in in the home user directory or cd to desktop if the package is in the desktop.

---

### Post by VCoolio on 2010-09-27
To elaborate: the /home directory is where the users' main directories are. Most of the time, THOSE are referred to as 'home', or ~ . So your home dir is /home/olimb for example. Just enter 'cd' to get (back) there. You don't want to extract and build packages in /home, you won't have the permissions. Read [this](https://help.ubuntu.com/community/UsingTheTerminal) for an introduction to the commandline. Also, if you ever get to the point where you need 'sudo make install' use [checkinstall](https://help.ubuntu.com/community/CheckInstall) instead to prevent problems with cluttered files that can't be removed and a package manager that doesn't know about these.

---

### Post by olimb on 2010-09-27
In the Using the Terminal documentation it says 
As another example, "cd ~/Desktop" will move you to the Desktop subdirectory inside your home directory.
When I try that I get 
bash:  cd: /home/t2/desktop:  No such file or directory


When I begin a new terminal it starts at the user,
t2@taptop:~$
I can change the directory down a level from there
but I can’t get to a higher level from there

I also tried cd.. /desktop
cd..: command not found
and if I try cd .. /desktop  (leaving a space after cd it goes down a level not up)
t2@taptop:/home$

---

### Post by gandaran on 2010-09-27
> **olimb said:**
> In the Using the Terminal documentation it says 
As another example, "cd ~/Desktop" will move you to the Desktop subdirectory inside your home directory.
When I try that I get 
bash:  cd: /home/t2/desktop:  No such file or directory


When I begin a new terminal it starts at the user,
t2@taptop:~$
I can change the directory down a level from there
but I can’t get to a higher level from there

I also tried cd.. /desktop
cd..: command not found
and if I try cd .. /desktop  (leaving a space after cd it goes down a level not up)
t2@taptop:/home$
desktop is with a D capital letter
```
/home/t2/Desktop
```

---

### Post by olimb on 2010-09-27
Thanks gandaran that capitol letter makes all the difference
Thanks to everyone else who replied
I’m going to call this one solved because I have managed to unzip the tar file using –zxvf
I haven’t got to install it yet but if I need further help I’ll start a new thread as this one was sidetracked with Terminal command errors.

---

### Post by SeijiSensei on 2010-09-27
One other thing I'll mention is this line from your original posting:

t2@taptop:/home$ cd/home/t2

If you're coming from Windows, this line seems perfectly fine, but Unix shells like bash require a space between the "cd" and the "/home/t2".  In general, you need to make sure you have spaces between every field in a command.

As you discovered with "desktop" and "Desktop" Unix is also case sensitive.

---

