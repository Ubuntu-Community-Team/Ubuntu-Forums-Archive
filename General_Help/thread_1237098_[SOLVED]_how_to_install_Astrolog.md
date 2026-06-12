---
title: "[SOLVED] how to install Astrolog"
date: 2009-08-11
forum: General Help
---

### Post by traynor on 2009-08-11
Hi - I found a nifty app that's not in Synaptic and I want to install it.

The only way to get it is to download a tar.gz file.

I'm running Ubuntu 9.xx

1)In what folder do I save the tar.gz file?

2)To what folder do I extract the tar.gz files?

3)How do I install the application once I've extracted the files from tar.gz?

Thanks for any help!

---

### Post by mthalis on 2009-08-11
Read this
[http://ubuntuforums.org/showthread.php?t=246092](http://ubuntuforums.org/showthread.php?t=246092)

---

### Post by roharme on 2009-08-11
tar.gz is just a compressed archive.
Extract it.
If you have a
1. .deb file inside it,Double click to install.
2 .rpm ,use alien <filename> to generate .deb and install.
3. .run , use sh <filename>

---

### Post by traynor on 2009-08-11
I read the thread there from 2006. Somewhat helpful but I'm still stuck.

I've downloaded the tar.gz and extracted it to my desktop. In the folder is the "executable" but when I open it nothing happens. So I drag and drop it into home/linux/ and try to open it from there and still nothing happens.

Any idea what I might be missing here?

thanks

---

### Post by nothingspecial on 2009-08-11
Navigate to the executable folder

```
cd Desktop/extracted_folder
```

Then
```
./executable
```

If it says permission denied then from the extracted folder

```
chmod a+x executable
```

Then try again.

You have to change "extracted_folder" and "executable" to their actual names and remember linux is case sensitive.

---

### Post by kn100 on 2009-08-11
what is the app? there is probably a debian package

---

### Post by aysiu on 2009-08-11
> **kn100 said:**
> what is the app? there is probably a debian package
And, if not, the instructions vary depending on how it's packaged.

It could be source. It could be a precompiled binary.

Either way, we need to know what the application is you're trying to install.

---

### Post by traynor on 2009-08-11
you all rock.

The app is called Astrolog (it's an astrology chart creator). 

I've navigated to the folder in terminal by typing cd Desktop/astrolog and that worked ok. I'm in the folder in terminal. (it says ~/Desktop/astrolog$ at the prompt)

The name of the executable is "astrolog" (lower case)

So next I typed "./astrolog" and terminal returns "bash: ./astrolog: No such file or directory" and returns me to ~/Desktop/astrolog$

So what now?



thanks

---

### Post by traynor on 2009-08-12
anyone have any idea where I'm going wrong above with the install?

---

### Post by cocopuffz on 2009-08-12
Are you sure it's a linux app? I looked for it online and only found a windows version and a unix version. There was also a source code download, but I'm pretty sure you'd have to compile that to run it.

Do you have a DL link to the linux version?

---

### Post by nikhilk on 2009-08-12
> **traynor said:**
> anyone have any idea where I'm going wrong above with the install?

Could you post the output of
```
ls -l ~/Desktop/astrolog/
```

---

### Post by traynor on 2009-08-12
linux@daedelus:~$ ls -l ~/Desktop/astrolog/
total 844
-rwxr-xr-x 1 linux linux 429515 1996-06-20 13:40 astrolog
-rw-r--r-- 1 linux linux   1424 1996-06-20 13:44 astrolog-5.20.lsm
-rw-r--r-- 1 linux linux   7808 1996-06-20 13:40 astrolog.dat
drwxr-xr-x 2 linux linux   4096 1996-06-20 13:43 docs
-rw-r--r-- 1 linux linux    778 1996-06-20 13:40 file_id.diz
-rw-r--r-- 1 linux linux 384886 1996-06-20 13:40 helpfile.520
-rw-r--r-- 1 linux linux  14401 1996-06-20 13:40 readme.520
drwxr-xr-x 2 linux linux   4096 1996-06-20 13:42 src
linux@daedelus:~$


What does that mean? (I hadn't thought that perhaps a Unix program won't work in Linux)

---

### Post by nikhilk on 2009-08-12
> **traynor said:**
> linux@daedelus:~$ ls -l ~/Desktop/astrolog/
total 844
-rwxr-xr-x 1 linux linux 429515 1996-06-20 13:40 astrolog
-rw-r--r-- 1 linux linux   1424 1996-06-20 13:44 astrolog-5.20.lsm
-rw-r--r-- 1 linux linux   7808 1996-06-20 13:40 astrolog.dat
drwxr-xr-x 2 linux linux   4096 1996-06-20 13:43 docs
-rw-r--r-- 1 linux linux    778 1996-06-20 13:40 file_id.diz
-rw-r--r-- 1 linux linux 384886 1996-06-20 13:40 helpfile.520
-rw-r--r-- 1 linux linux  14401 1996-06-20 13:40 readme.520
drwxr-xr-x 2 linux linux   4096 1996-06-20 13:42 src
linux@daedelus:~$


What does that mean? (I hadn't thought that perhaps a Unix program won't work in Linux)

You have a binary named "astrolog" under ~/Desktop/astrolog, alright. The permissions on it also look OK. Even if it is a UNIX binary, you should not have gotten a "No such file or directory" error.
See what happens when you run these commands
```
cd ~/Desktop/astrolog
bash ./astrolog
```

Also, post the output of
```
file ~/Desktop/astrolog/astrolog
```

---

### Post by traynor on 2009-08-12
Like this?:


linux@daedelus:~$ cd ~/Desktop/astrolog
linux@daedelus:~/Desktop/astrolog$ bash ./astrolog
./astrolog: ./astrolog: cannot execute binary file
linux@daedelus:~/Desktop/astrolog$ cd
linux@daedelus:~$ file ~/Desktop/astrolog/astrolog
/home/linux/Desktop/astrolog/astrolog: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), not stripped
linux@daedelus:~$ 

what now? (thanks!)

---

### Post by jerome1232 on 2009-08-12
Maybe your missing some libraries? Is there any documentation in those readme.520 or helpfile.520? What about in the doc directory are there any installation/running guides in there?

---

### Post by aysiu on 2009-08-12
You know what's weird.

*astrolog* was in Dapper (Ubuntu 6.06), but it doesn't appear to be in any support repositories.

Maybe try this?

**Step 1**
Download the [astrolog .deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/a/astrolog/astrolog_5.40-2_i386.deb) to your desktop

**Step 2**
Double-click it to install it with GDebi

**Step 3**
Run it from the terminal with the command ```
astrolog
```

---

### Post by nikhilk on 2009-08-13
> **traynor said:**
> Like this?:


linux@daedelus:~$ cd ~/Desktop/astrolog
linux@daedelus:~/Desktop/astrolog$ bash ./astrolog
./astrolog: ./astrolog: cannot execute binary file
linux@daedelus:~/Desktop/astrolog$ cd
linux@daedelus:~$ file ~/Desktop/astrolog/astrolog
/home/linux/Desktop/astrolog/astrolog: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), not stripped
linux@daedelus:~$ 

what now? (thanks!)

So it is a UN*X binary, I suppose. I am not sure if that works on Linux, I have never ever used UN*X so I have no idea.
First see if what aysiu suggested works. If it doesn't I think there might be no easy way to directly use a pre-compiled binary.
But it seems the source code is available, in which case compiling it yourself might be the best option.

---

### Post by traynor on 2009-08-14
Success! the link asyiu provided worked perfectly.

Thanks for everyone's help!!! You've proven I'm ready to wipe Windoze Vista off this box completely. I'm taking the full plunge into Ubuntu...

Cheers!

---

