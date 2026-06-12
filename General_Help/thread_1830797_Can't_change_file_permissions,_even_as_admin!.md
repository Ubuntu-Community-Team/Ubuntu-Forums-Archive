---
title: "Can't change file permissions, even as admin?!"
date: 2011-08-22
forum: General Help
---

### Post by equusaustralus on 2011-08-22
Hi, 

I've been having a very strange problem, and not sure for how long... but basically, my system wont allow me to change file permissions, even in root mode!

I run Ubuntu 10.10 with Gnome and LXDE, kernel 2.6.35-30-generic. 

It's particularly problematic if I want to run some binaries or programs that you need a shell script to start up (i.e. any new version of Firefox). The usual right-click then going into permissions doesn't work, it just resets whatever changes I make. 

The weirdest thing is that using the chmod command as root also has no results! The files keep the exact permissions they had before...

Am I missing something obvious? :confused: I used to be able to modify files as I pleased...

Thanks in advance, any help would be greatly appreciated!

---

### Post by seawolf167 on 2011-08-22
It doesn't work in the command line either?

A test:

change to desktop, make new "test" folder

```
cd ~/Desktop
mkdir test
cd test
```make test file, show default permissions (post this output please)

```
touch test
ls -l
```chmod the test file to 777 permissions, list output (post this output please)

```
sudo chmod 777 test
ls -l
```remove file and directory

```
rm test
cd ..
rmdir test/
```

---

### Post by nothingspecial on 2011-08-22
Just a guess

Are these files on a non native linux file system? Because if they are you cannot change the permissions because the file system doesn't support it, although you can set the permissions of the file system itself at when mounting.

---

### Post by equusaustralus on 2011-08-29
Sorry for the delayed reply! 

All of the files are on an ext3 partition, so that shouldn't be a problem.

Here's the result of the first output: 

```
equus@laptop:~/Desktop/test$ ls -l
total 0
-rw-r--r-- 1 equus equus 0 2011-08-30 00:38 test
```

and the second: 

```
equus@laptop:~/Desktop/test$ sudo chmod 777 test
equus@laptop:~/Desktop/test$ ls -l
total 0
-rwxrwxrwx 1 equus equus 0 2011-08-30 00:38 test

```

Which means it worked.

I had an idea after running this test that it might have something to do with the fact that I use Gnome's File Roller v2.32 to unpack all of the archives that I download... 

So I tried using Xarchiver instead. Lo and behold, it unzips the files as they're supposed to be, with executable privileges! Problem solved, which means that it was File Roller giving me all of the hassle for so log! 

Still can't understand what File Roller had to do to the files to make chmod not work even as root, but at least it works now :)

Thanks for the help guys! :guitar:

---

### Post by equusaustralus on 2011-08-29
P.S. @nothingspecial  I just triple-checked and realised that I missed something glaringly obvious... I recently moved the folder with all of the downloaded programs from the ext3 partition to an ntfs partition in order to save space... I was so used to running it off the linux partition that I didn't even notice! Hence why chmod didn't work... Sorry, my mistake, you were right! :)

---

