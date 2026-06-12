---
title: "How to change files permission with single command"
date: 2011-02-20
forum: General Help
---

### Post by s.a.patil on 2011-02-20
Respected community members, while experimenting with various PHP CMS on my local-host I need to "chmod" the large quantity of directories and files with single command, to achieve this I use the following command for directory "sudo find /var/www/cms/ -type d -print0 | xargs -0 sudo chmod 777" and it works without any flaw, but when I use "sudo find /var/www/cms/ -type f -print0 | xargs -0 sudo chmod 777" for files it gives me this error "sudo: unable to execute /bin/chmod: Argument list too long", I request any learned member to guide me on the issue. Thanks a lot in advance.

---

### Post by Habitual on 2011-02-20
777 is very insecure

**Be CAREFUL**

---

### Post by cjhabs on 2011-02-20
> **s.a.patil said:**
> Respected community members, while experimenting with various PHP CMS on my local-host I need to "chmod" the large quantity of directories and files with single command, to achieve this I use the following command for directory "sudo find /var/www/cms/ -type d -print0 | xargs -0 sudo chmod 777" and it works without any flaw, but when I use "sudo find /var/www/cms/ -type f -print0 | xargs -0 sudo chmod 777" for files it gives me this error "sudo: unable to execute /bin/chmod: Argument list too long", I request any learned member to guide me on the issue. Thanks a lot in advance.

Try running this under the Bourne shell - /bin/sh

---

### Post by Morbius1 on 2011-02-20
I am most defiantly not a "learned member" but I see nothing wrong with your commands. It's possible that the "Argument list too long" is referring to the number of files it has to process and not the length of the command. 

I am rather curious however why you are choosing to do it this way. You usually use those commands to do the opposite of what you are trying to achieve. 

If you do the following command:
```
sudo chmod -R 0777 /var/www/cms
```That will change the permissions on every directory and every file to 777 which from a Linux purist's point of view is a bad thing since you just made every file executable.

You use your way when you want directories to be 777 and files to be 666 or at least something that doesn't make files executable.

---

### Post by s.a.patil on 2011-02-20
Respected Habitual, cjhabs, and Morbius1, thanks a lot for the reply, I found this command here [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions), now I will try "sudo chmod -R 0777 /var/www/cms"

---

### Post by hakermania on 2011-02-20
you could do something like
```

for file in $(command that will output the list of files); do
chmod 0777 $file
done
```
Yes, you could also use the -R option of chmod.

---

### Post by s.a.patil on 2011-02-20
Respected members, thanks a lot for reply. Comrades the command "sudo chmod -R 0777 /var/www/cms" changes the permission of both directory and files that reside in it, what I wanted to achieve is different permission for directory and files. In "sudo find /var/www/cms/ -type d -print0 | xargs -0 sudo chmod 755" command the shell will first find directory "cms" and change its permission and not the files that reside in it, where as "sudo find /var/www/cms/ -type f -print0 | xargs -0 sudo chmod 777" will find directory "cms" and change the permission of all files inside the directory "cms" and not directory "cms". But if I type the "sudo find /var/www/cms/ -type f -print0 | xargs -0 sudo chmod 777" command to change the permission of files that reside in "cms" I get the following error "sudo: unable to execute /bin/chmod: Argument list too long" is there any way around? Please help. Thanks a lot in advance.

---

### Post by Morbius1 on 2011-02-20
Your requirements seemed to have changed.

On a hunch I did find a reference to that error message and an unusually high number of files being processed: [http://johnmcgough.com/linux.htm](http://johnmcgough.com/linux.htm)> ***[B]2.9.8 Error With High Number Of Files***[/B]

 To resolve the following error:
 sudo: unable to execute /bin/chmod: Argument list too long
 The example below is for issuing a 'chmod 0644' command on a very high number of files.
  sudo find . -type f -exec chmod 0644 {} \; -print

So to convert it to your situation the expression would become:[FONT=sans-serif]
[/FONT]```
sudo find /var/www/cms -type f -exec chmod 0777 {} \; -print
```Never having run that before I did test it on a test directory and it did work. It will also work without the "-print" at the end but I suspect you want that there since this looks like it would take such a long time to process that without printing the file name to the terminal you might think the process stalled.

---

### Post by s.a.patil on 2011-02-20
Respected Morbius1, a huge thanks for helping me:):). It worked like charm:):). Thanks once again for your kind help.

---

