---
title: "Unable to run shell script"
date: 2012-06-26
forum: General Help
---

### Post by cinlung on 2012-06-26
Hi,

Can I add a rather related topic? I used ubuntu 10.04 LTS before and was able to run script by just typing ./scripttest.sh. Now, in ubuntu 12.04 LTS, I cannot do that anymore even with root account and chmod is set to 777 to the scripttest.sh file. I have to use sh scripttest.sh to make it run, otherwise, I will get permission denied message.

I cannot even perform auto file name completion by pressing tab for the script file (typing ./sc and tab should auto-complete the name of the file since there is only one file in the current folder).

Did ubuntu 12.04 change the security behavior? However, when I copied the file to /usr/local/bin, then I can call the file name from anywhere just by the file name only.

Please enlighten me.

Thanks
Rendra

---

### Post by oldos2er on 2012-06-26
Post moved to its own thread.

---

### Post by cortman on 2012-06-26
Don't know if it will solve it or not, but you can run

```
sudo chown your_user_name script_name
chmod a+x script_name
```

Note that I only used sudo for chown.

---

### Post by efflandt on 2012-06-26
Simplest way to handle your own scripts, if you have not already, is to **mkdir ~/bin**

Log out of X and log back in.  That **~/bin** directory will now be in your $PATH.

Then put your scripts in that bin, give them execute permission, and assuming they are properly written, they should be able to run with just the script name (without ./ prefix).

I don't know if the system is protecting you from yourself, but 777 permission is VERY insecure, because anybody could modify the script and it might do something unexpected when you run it.  Typical permission for scripts is 755, but could be as little as 700 if it is owned by you and only you should run or see it.

Note that the x bit on directories means something different, more like access or list permission instead of execute permission.  You need x permission on a directory to be able to list files in that directory (and likely also for bash file completion).

---

### Post by cinlung on 2012-06-27
> **efflandt said:**
> Simplest way to handle your own scripts, if you have not already, is to **mkdir ~/bin**

Log out of X and log back in.  That **~/bin** directory will now be in your $PATH.

Then put your scripts in that bin, give them execute permission, and assuming they are properly written, they should be able to run with just the script name (without ./ prefix).

I don't know if the system is protecting you from yourself, but 777 permission is VERY insecure, because anybody could modify the script and it might do something unexpected when you run it.  Typical permission for scripts is 755, but could be as little as 700 if it is owned by you and only you should run or see it.

Note that the x bit on directories means something different, more like access or list permission instead of execute permission.  You need x permission on a directory to be able to list files in that directory (and likely also for bash file completion).

Hi,

I realize about the 777 insecurity. But I was very curious on how it prevent me. So even after I set chmod 777 to the testscript.sh file, it still says that permission denied. And yest I did the a+x thing and still does not work.

Any ideas? I do not want to put my scripts to the standard ~/bin directory for ease of backup purposes. I am starting to think that ubuntu 12.04 server is designed in the way that all scripts outside /bin or ~/bin or /usr/local/bin is not runnable unless using sh <script file>.sh

Any comments?

---

### Post by CharlesA on 2012-06-27
How are you running the script? Copy/paste the terminal output if you can.

---

### Post by HiImTye on 2012-06-27
we need more info to help you

what is the script you are trying to run?
what is the output when you run it from a terminal? (include the line that has what you typed on it)

---

### Post by majikchicken on 2012-06-29
Hi, not to hijack this thread, but this is not a problem with the file.  I have the same issues on my ubuntu distro (except it's with an executable binary).  The file contents are unrelated to this bug...and this is an issue considering the handler of files like binary executables *is the kernel.*  I think this is an issue with the bash session within X.

I can reproduce the problem with :
```

casnix@ubuntu:/media/MATEOR/prlserverapi/cport/prlserverapi-gui$ ./main
bash: ./main: Permission denied.

```

Even with `chmod +x ./main` or `chmod a+x ./main` it won't work.  When I type `ls -al` I get:
```

total 20
drwx------ 2 casnix casnix 4096 2012-06-29 15:49 .
drwx------ 3 casnix casnix 4096 2012-06-29 15:42 ..
-rw-r--r-- 1 casnix casnix 7681 2012-06-29 15:49 main
-rw-r--r-- 1 casnix casnix 1409 2012-06-29 15:49 main.c

```

You can tell that chmod isn't working as expected.  I have the same issues as root user as well.

---

### Post by CharlesA on 2012-06-29
FAT32 and NTFS drives do not support Linux permissions. Permissions are set when you mount them.

---

### Post by majikchicken on 2012-06-29
EDIT:

Looking at an old post on a different forum, I found this.

```

$ file <file>
File type

```

To execute on 32 bit:
```

$ /lib/ld-linux.so.2 <binary exec>

```

So to run the bash script (for the OP) try 
```

$ bash <script name>

```

---

### Post by CharlesA on 2012-06-29
Run this:

```
mount
```

---

