---
title: "Linked scripts won't run"
date: 2012-08-29
forum: General Help
---

### Post by JohnCraick on 2012-08-29
Problem : linked shell scripts won't run at the command prompt

Short Version :

Scripts run when directly present in my working directory or when linked from a nearby folder. They will NOT run when linked from a "distant" folder, i.e. one on a different data disk.

Why is this ?

Can I, perhaps, only run scripts directly if they are in my home filespace ?
Is this some weird kind of security feature ?

I can get round the problem in several ways but I'd like to know what's causing it

Thanks,

JohnC
-----------------------

Long Version 



In my current working directory, ~/aawork, I have an executable test script called ms (abbr for "myscript"). It just echos to the screen a text message. I have a copy of the script in a sibling directory, "~/aascripts/ms" and another in a "distant" directory, "/media/NewHome20G/JohnData/aascriptlib/ms". The distant directory is a folder in a partition on a different physical disk. See below, listing 1, lines 1 - 7

So ...

base script : myscript (ms)

folders :
aawork         where everything is run
aascripts    sibling folder with copy of myscript
aascriptlib    "distant" folder with a copy of myscript = /media/NewHome20G/JohnData/aascriptlib

Observations

O1 I can run the script directly in the usual manner - see listing 1 lines 8 - 13 (L1,8-13)

O2 I can run the script from ms1 which is a link to the real script in the sibling directory - see L1,14-19

O3 I can NOT run the script from ms2 which is a link to the real script in the distant directory - see L1,20-21

O4 I CAN run the ms2 script from a shell command - see L1,22-28


Listing 1 (L1)

1    john@john-pc1204:~/aawork$ ll
2    total 12
3    drwxrwxrwx  2 john john 4096 Aug 29 12:41 .
4    drwxr-xr-x 62 john john 4096 Aug 29 12:10 ..
5    -rwxrwxrwx  1 john john  217 Aug 29 12:40 ms
6    lrwxrwxrwx  1 john john   15 Aug 29 12:22 ms1 -> ../aascripts/ms
7    lrwxrwxrwx  1 john john   41 Aug 29 12:23 ms2 -> /media/NewHome20G/JohnData/aascriptlib/ms

8    john@john-pc1204:~/aawork$ ./ms
9    ________________________________
10    Hello World
11    Script is working as at Wed Aug 29 12:41:27 EST 2012
12    I am running as user john
13    ________________________________

14    john@john-pc1204:~/aawork$ ./ms1
15    ________________________________
16    Hello World
17    Script is working as at Wed Aug 29 12:41:35 EST 2012
18    I am running as user john
19    ________________________________

20    john@john-pc1204:~/aawork$ ./ms2
21    bash: ./ms2: Permission denied

22    john@john-pc1204:~/aawork$ sh ms2
23    ________________________________
24    Hello World
25    Script is working as at Wed Aug 29 12:41:57 EST 2012
26    I am running as user john
27    ________________________________
28    john@john-pc1204:~/aawork$ 

Over in the distant directory, all the ownership & permissions seem to be set up OK - as per ...

john@john-pc1204:~$  cd /media/NewHome20G/JohnData/aascriptlib
john@john-pc1204:/media/NewHome20G/JohnData/aascriptlib$ ll
total 12
drwxrwxrwx  2 john john 4096 Aug 29 12:24 .
drwxrwxrwx 18 john john 4096 Aug 29 11:23 ..
-rwxrwxrwx  1 john john  217 Aug 29 12:40 ms
john@john-pc1204:/media/NewHome20G/JohnData/aascriptlib$ 

Now I try to run the script directly in the distant directory

1    john@john-pc1204:/media/NewHome20G/JohnData/aascriptlib$ ./ms
2    bash: ./ms: Permission denied

3    john@john-pc1204:/media/NewHome20G/JohnData/aascriptlib$ sh ms
4    ________________________________
5    Hello World
6    Script is working as at Wed Aug 29 14:07:16 EST 2012
7    I am running as user john
8    ________________________________
9    john@john-pc1204:/media/NewHome20G/JohnData/aascriptlib$ 

As previously, it fails to run directly but will run under the shell. (i.e. as per O4 above) 

So can anyone explain this ?

Can I, perhaps, only run scripts directly if they are in my home filespace ?
Is this some weird kind of security feature ?

---

### Post by Cheesemill on 2012-08-29
What is the output of:
```
mount
```It could be that your other drive is mounted with the noexec option, which surprisingly enough doesn't allow execution of programs.

How are you mounting your other drive, is it done automatically or do you have an entry in /etc/fstab for it?

Edit - Another question, what filesystem is the other drive? NTFS and FAT formatted drives don't understand the linux permissions system meaning that you come across difficulties trying to set the executable bit.

---

### Post by JohnCraick on 2012-08-29
Thanks for your reply.

I have LOTS of drives and quite a long /etc/fstab file. Here are just a few lines from the mount -l command ...

/dev/sdc2 on /media/Kubuntu810beta type ext3 (rw,noexec,nosuid,nodev)
/dev/sdc4 on /media/PriLin20G type ext3 (rw,noexec,nosuid,nodev)
# next line is the relevant drive
/dev/sdc6 on /media/NewHome20G type ext3 (rw,noexec,nosuid,nodev) 
/dev/sda7 on /media/P7SuseHome40G type ext3 (rw,noexec,nosuid,nodev)

Here, I believe,  is the relevant line from my fstab file ...

 LABEL=NewHome20G    /media/NewHome20G    ext3    rw,nosuid,nodev,exec,users    0    2

As you can see, this is an ext3 partition & my fstab asks for the exec & users options. Judging by the mount listing, those options have not in fact been applied. 

I wonder if I have messed up somewhere or whether Ubuntu has decided to ignore the fstab file in the interests of security.  I shall continue to experiment with this mounting stuff (carefully !)

Thanks again. Any more clues ?

Regards

J

---

### Post by JohnCraick on 2012-08-29
SOLVED - thank you

Following up your clue, I re-read the man entries  for mount and fstab.  Then,logged on as root in a terminal,  I enter

mount  /dev/sdc6  -o exec

then 

mount | grep NewH

I get 

/dev/sdc6 on /media/NewHome20G type ext3 (rw,nosuid,nodev)

... i.e.  the previous noexec option no longer appears

I now find that the ms2 script previously discussed WILL run linked from the distant folder.

I have tried editing the fstab file and rebooting but Ubuntu seems to ignore my mods & use it's own defaults regardless. I'll look further into that. I don't think I had this problem with earlier versions of Ubuntu but I'll check.

Regards.

JohnC

Thanks again for your assistance

---

