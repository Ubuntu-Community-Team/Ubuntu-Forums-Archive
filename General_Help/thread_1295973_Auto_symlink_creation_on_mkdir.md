---
title: "Auto symlink creation on mkdir"
date: 2009-10-20
forum: General Help
---

### Post by Zorba_The_Freak on 2009-10-20
Hi, my first post here ;)

Next week I'll set up a ubuntu server 9.10 machine.

There will be a Files folder where users will move files they downloaded in their home dir.

What I need your help for, is a way to _**automatically**_ create a soft link in a different folder called New_Files _**each time**_ a new folder is created in the Files folder.

So I will be able to check the New_Files folder and know what was uploaded so I can download the files I like to my desktop machine through ftp.

Then I will manually delete the soft links I'm not interested in and wait for the next uploads.

Sorry for my poor english and I hope you understand what I need.

Thanks in advance.

---

### Post by bruno9779 on 2009-10-20
I don't have a direct answer to your question, but I would do it in a different way.

You could write a simple bash script to check what is in the files folder and have a cronjob to run it as often as you need.

You can have the output as a file or creating the sim-links for you or else.

---

### Post by Zorba_The_Freak on 2009-10-20
Thanks for your answer!

Well I'm total linux noob so I won't be able to write the script myself and also I want each symlink created only once when the directory is originally created. I don't want the same file linked to the New_Files folder on the next cron run.

If that can be done with a cron job then I don't mind the time delay between 2 cron runs

---

### Post by StuartN on 2009-10-20
> **Zorba_The_Freak said:**
> What I need your help for, is a way to _**automatically**_ create a soft link in a different folder called New_Files _**each time**_ a new folder is created in the Files folder.

Okay, I have a similar issue in managing photographs from multiple users that I want to place on a NAS - each user has a private photo library, but the NAS shares some folders to everyone.

This is not automatic, but could be called by a file monitor or run as a cron job:

```
for file in ~/temp1/* ; do
{
 filename=${file##*/}
 if [ ! -e "temp2/$filename" ] ; then ln -s "$file" ~/temp2 ; fi
} done

```

For each file in temp1, if it does not exist in temp2, then make a symlink to it. Each run will therefore add every missing file (including replacing any symlinks you have deleted). You can adapt this to copy directories in temp1 using ! -d, and you could replace the ~/temp1/* with a dated find to only add links newer than the last run.

---

### Post by Zorba_The_Freak on 2009-10-20
That seems to be the answer but I don't know how to do the changes :(

Can you point me to some man page or something relevant to read?

---

### Post by StuartN on 2009-10-20
> **Zorba_The_Freak said:**
> That seems to be the answer but I don't know how to do the changes :(

Can you point me to some man page or something relevant to read?

Somebody recently pointed to this introduction to Bash scripting that might be helpful: [http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

There is also a man page describing the test function in line 4 at: [http://linux.die.net/man/1/test](http://linux.die.net/man/1/test)

If you save the text in the Code box as a file and make it executable, then it should run on your system. Change ~/temp1 (in line 1) into the source directory that you are copying from. Change ~/temp 2 (twice in line 4) into the destination directory where you want to make links. The script will then create a destination symlink to any file or any directory that exists in the source.

---

### Post by Zorba_The_Freak on 2009-10-20
Yes I understood that part :) 

Where I have no clue is this:

> **StuartN said:**
> You can adapt this to copy directories in temp1 using ! -d, and you could replace the ~/temp1/* with a dated find to only add links newer than the last run.

---

### Post by StuartN on 2009-10-20
> **Zorba_The_Freak said:**
> Where I have no clue is this:

The code as it is will symlink any missing file or directory, but the remaining problem is not creating symlinks again after you delete them. Try this:

```
for file in ~/temp1/* ; do
{
 filename=${file##*/}
 if [ ! -e "~/temp2/$filename" ] && [ "~/temp1/$filename" -nt ~/temp2 ] ; then
  ln -s "$file" ~/temp2 ;
 fi
} done
touch ~/temp2
```

So in line 4 I have added a second test - if the file in the source (temp1) does not exist in the destination (temp2) AND the file in the source is newer than the destination directory, then make a symlink. Now it will only copy files newer than the destination directory (temp2).

In line 9 the command touch adjusts this date to the date the script is run - so everything added since the last run will be symlinked. If you delete a symlink, then it will not be recreated.

(Maybe somebody else can do this in one line with find, and possibly more elegantly, but it does work)

---

### Post by Zorba_The_Freak on 2009-10-20
THANK YOU VERY VERY MUCH!!!!! for your time and effort.

So I paste this code into a new file and make it executable, then add a new cron job, right?

And it will symlink files AND folders???

THANKS AGAIN!!!

---

