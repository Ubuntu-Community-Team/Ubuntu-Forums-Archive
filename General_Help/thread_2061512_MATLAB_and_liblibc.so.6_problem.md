---
title: "MATLAB and lib/libc.so.6 problem"
date: 2012-09-22
forum: General Help
---

### Post by Alcidious on 2012-09-22
So whenever i run matlab on my precise 12.04 32 bit laptop i have to cd to the compete pathway in to my filesystem and then run ./matlab -glnx86 (cumbersome to say the least).

Anyway, the program will run, but the terminal always displays:

./matlab: 1: /usr/local/MATLAB/R2012a_Student/bin/util/oscheck.sh: /lib/libc.so6: not found

I found someone with the very same problem, and it was resolved, at 
[http://askubuntu.com/questions/40416/why-is-lib-libc-so-6-missing](http://askubuntu.com/questions/40416/why-is-lib-libc-so-6-missing)

they used find | grep libc.so.6 to locate the scripts location.  He was then able to create a symlink using 

sudo ln -s /lib/i386-linux-gnu/libc.so.6 /lib/libc.so.6

But when I ran find | grep libc.so.6 my terminal displayed no output.  How can I find the information I need to create a symbolic link and fix this?  Thanks!

---

### Post by matt_symes on 2012-09-22
Hi

> **Alcidious said:**
> So whenever i run matlab on my precise 12.04 32 bit laptop i have to cd to the compete pathway in to my filesystem and then run ./matlab -glnx86 (cumbersome to say the least).

Anyway, the program will run, but the terminal always displays:

./matlab: 1: /usr/local/MATLAB/R2012a_Student/bin/util/oscheck.sh: /lib/libc.so6: not found

I found someone with the very same problem, and it was resolved, at 
[http://askubuntu.com/questions/40416/why-is-lib-libc-so-6-missing](http://askubuntu.com/questions/40416/why-is-lib-libc-so-6-missing)

they used find | grep libc.so.6 to locate the scripts location.  He was then able to create a symlink using 

sudo ln -s /lib/i386-linux-gnu/libc.so.6 /lib/libc.so.6

But when I ran find | grep libc.so.6 my terminal displayed no output.  How can I find the information I need to create a symbolic link and fix this?  Thanks!
 
Welcome to the forums Alcidious.

First about the find statement. The original poster was using the find command pipped into the grep command.

You do not really need the pipe as you can specify what to search for using find.
```

matthew-Aspire-7540:/home/matthew % sudo find / -name "libc.so.6"
/lib/x86_64-linux-gnu/libc.so.6
/lib/i386-linux-gnu/libc.so.6
matthew-Aspire-7540:/home/matthew %
```Second, the find command as typed by the orginal poster of that question i.e (find | grep ...) will start searching in the current working directory and sub directories, so if you are in your home directory you will miss all the system directories where the library files are stored. I suspect this is what happened to you.
```

matthew-Aspire-7540:/home/matthew % pwd
/home/matthew
matthew-Aspire-7540:/home/matthew % find | head -n5
.
./.zshrc
./.rtorrent.rc
./storage
./storage/kernel
matthew-Aspire-7540:/home/matthew % 
```As you can see from above, my current directory is my home directory and the find command starts searching in the "." (currently) directory. This search will miss out all the system directories.

If you need help creating the symbolic link then post back.

Kind regards

---

### Post by Alcidious on 2012-09-22
Thanks so much! That makes perfect sense.  But where should I be looking? in the directory my I've put MATLAB? Or should I be searching some other directory in the filesystem?

-slowly but surely i am improving in linux!

---

### Post by matt_symes on 2012-09-24
Hi

> **Alcidious said:**
> Thanks so much! That makes perfect sense.  But where should I be looking? in the directory my I've put MATLAB? Or should I be searching some other directory in the filesystem?

-slowly but surely i am improving in linux!

I am sure you are aware of the caveats as stated in the post you linked regarding the symbolic link.

What the poster did was to create a symbolic link for libc.so.6 in /lib to point to the correct library in /lib/i386-linux-gnu/libc.so.6.

Assuming matlab is a 32 bit application then this should work for you (from your first post).

```
sudo ln -s /lib/i386-linux-gnu/libc.so.6 /lib/libc.so.6
```You can check the link using 

```
ls -l /lib/libc.so.6
```or

```
readlink -f /lib/libc.so.6
```/lib/i386-linux-gnu/libc.so.6 itself is a symbolic link that points to the correct libc library

On my system...
```

matthew-Aspire-7540:/home/matthew/Music % ls -l /lib/i386-linux-gnu/libc.so.6
lrwxrwxrwx 1 root root 12 Sep 12 13:27 /lib/i386-linux-gnu/libc.so.6 -> libc-2.15.so*
matthew-Aspire-7540:/home/matthew/Music % readlink -f /lib/i386-linux-gnu/libc.so.6
/lib/i386-linux-gnu/libc-2.15.so
matthew-Aspire-7540:/home/matthew/Music % 
```Where on you file system is matlab installed ?

Kind regards

---

### Post by Alcidious on 2012-09-25
MATLAB is installed in /usr/local/MATLAB

but to access it i have to cd to /usr/local/MATLAB/R2012a_Student/bin 
and then type ./matlab -glnx86

I would love to not have to do that. But I was able to create the symlink, finally, but I tested to it with both commands, and I got two slightly different answers? When I ran matlab the libc-not found error is no longer there, hurray!  If everything is good to go, then thanks so much! And on to the next little issue...


alcidious42@IronMan:~$ ls -l /lib/libc.so.6
lrwxrwxrwx 1 root root 29 Sep 25 01:00 /lib/libc.so.6 -> /lib/i386-linux-gnu/libc.so.6
alcidious42@IronMan:~$ readlink -f /lib/libc.so.6
/lib/i386-linux-gnu/libc-2.15.so

---

### Post by matt_symes on 2012-09-26
Hi

Add  this path ( /usr/local/MATLAB/R2012a_Student/bin ) to your PATH environmental variable.

Copy and paste this into the terminal.

 ```
echo 'export PATH=$PATH:/usr/local/MATLAB/R2012a_Student/bin' >> ~/.bashrc
``` 

You should then not have to navigate to the directory. (or you could create a launcher)

Kind regards

---

### Post by Alcidious on 2012-09-27
Thanks for all your help matt!

---

