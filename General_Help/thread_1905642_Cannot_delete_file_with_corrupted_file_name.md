---
title: "Cannot delete file with corrupted file name"
date: 2012-01-07
forum: General Help
---

### Post by squenson on 2012-01-07
Hello,

I have a file that I cannot delete. The name of the file was supposed to be Baldo_2006-07-01.gif but it appears, with the command ls, as Baldo_2006-07-01?gif. If I run the command rm *, I get the following message:```
rm: cannot remove `Baldo_2006-07-01\016gif': No such file or directory
```
I have try many other commands, like sudo rm *, sudo rm -r *, sudo shred * and I always get an error message. I think the file name was corrupted during a copy process.

Any idea of a command I could use to get rid of it?

---

### Post by Basher101 on 2012-01-07
look closeley to your command, you typed the file name wrong > cannot remove `Baldo_2006-07-01\016gif instead of the backslash "\" you need a " - " and no 16 at the end.

so your correct command should look like this ```
rm Baldo_2006-07-01.gif
``` but this will also not delete it. You must point the command in what directory your file is (is it on the desktop?) if it is on the desktop type ```
rm /home/user_name/Desktop/Baldo_2006-07-01.gif
```

write instead ot user_name your actual username.

regards

---

### Post by squenson on 2012-01-07
I type the command rm * which should remove all the files. This file which has a strange name and it resists to deletion and the error message is exactly as posted, with the \016 instead of the '.'

---

### Post by jerrrys on 2012-01-07
Wonder if it could be repaired.

[ATTACH]210399[/ATTACH]

---

### Post by toyoracer on 2012-01-07
You could try gksudo nautilus and send it to trash. Just make sure you have the right file, as it will be deleted.

---

### Post by ajgreeny on 2012-01-07
Have you tried to rename it with a right click in nautilus?  If you can not remove it, you probably can not rename either, but it must be worth trying.

---

### Post by squenson on 2012-01-07
I also tried sudo nautilus but I also get the similar error message. The problem is not linked to the permissions, just the file name which is corrupted and resists to all changes, deletion, etc. I am looking for a low level command to rename the file and replace the '\016' character with a simple dot.

I am currently installing the Nautilus extension suggested by jerrrys.

---

### Post by blackbird34 on 2012-01-07
> **toyoracer said:**
> You could try sudo nautilus and send it to trash. Just make sure you have the right file, as it will be deleted.

Not "sudo nautilus" but ```
gksudo nautilus
```I've been told off for that one. See here [U][COLOR=Blue][http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
:popcorn:
[/COLOR][/U]

---

### Post by toyoracer on 2012-01-07
Thanks for that information blackbird. I corrected my post.

---

### Post by bluexrider on 2012-01-07
> **squenson said:**
> Hello,

I have a file that I cannot delete. The name of the file was supposed to be **[COLOR=Red]Baldo_2006-07-01.gif[/COLOR]** but it appears, with the command ls, as [COLOR=Blue]**Baldo_2006-07-01?gif**[/COLOR]. If I run the command rm *, I get the following message:```
rm: cannot remove `Baldo_2006-07-01\016gif': No such file or directory
```I have try many other commands, like sudo rm *, sudo rm -r *, sudo shred * and I always get an error message. I think the file name was corrupted during a copy process.

Any idea of a command I could use to get rid of it?
Which file are you trying to remove the one in red or the one in blue.

According to your statement the file that failed was the one in red. And that file doesn't exist. note the [COLOR=Blue]**"?"**[/COLOR]

Try retyping the correct file name exactly, using your CLI

---

### Post by squenson on 2012-01-07
> Which file are you trying to remove the one in red or the one in blue.I am trying to remove the only file left in this folder with the command rm *
The name in red is what the file name should be. The file in blue is how it appears with the command ls. The question mark seems to be the hexadecimal character \016 as it appears in the first post as an error message to the command rm *.

---

### Post by squenson on 2012-01-07
I can't make the Nautilus extension work... I have installed the package, rebooted (to be sure) and I don't see the option when I right-click.

---

### Post by carranty on 2012-01-07
We don't have enough information to give you an exact command.  Using the terminal please navigate to the folder this file is in and paste to this thread both the following commands and their outputs

```
pwd
```

and

```
ls -al
```

---

### Post by squenson on 2012-01-07
```
pwd
/media/HD_1000GB/_bd/Baldo/Baldo_2006

squenson@Desktop:/media/HD_1000GB/_bd/Baldo/Baldo_2006$ ls -al
total 136
drwx------ 1 squenson squenson 94208 2012-01-07 18:10 .
drwx------ 1 squenson squenson  4096 2012-01-07 16:45 ..
-rw------- 8 squenson squenson 40960 2012-01-07 17:03 Baldo_2006-07-01?gif

```

---

### Post by Habitual on 2012-01-07
> **squenson said:**
> Hello,

I have a file that I cannot delete. The name of the file was supposed to be Baldo_2006-07-01.gif but it appears, with the command ls, as Baldo_2006-07-01?gif. If I run the command rm *, I get the following message:```
rm: cannot remove `Baldo_2006-07-01\016gif': No such file or directory
```I have try many other commands, like sudo rm *, sudo rm -r *, sudo shred * and I always get an error message. I think the file name was corrupted during a copy process.

Any idea of a command I could use to get rid of it?

cd to the directory that has Baldo*.gif in Terminal and type
```
ls -i [COLOR=Red]2064227[/COLOR] Baldo_**tab tab**
```[COLOR=Red]
[COLOR=Black]You should see a number next to the file.[/COLOR]
[COLOR=Black]Then use that number to nuke it to orbit with[/COLOR]
[/COLOR]```
find . -inum [COLOR=Red]2064227[/COLOR] -exec rm {} \;
```

---

### Post by carranty on 2012-01-07
Looking at the code in post #14 I think  your problem is that you have 8 hard links of the file i.e. the file has 8 different names.  To find them all type 
```

sudo find / -xdev -samefile "Baldo_2006-07-01?gif"
```and post the results.

EDIT : Ignore the above, Habitual's tip should do the trick.

I think the problem is wth the special character ?, it may need escaping.  
```

rm Baldo_2006-07-01\?gif
```may do it, notice I've put a \ in front of the ?.

---

### Post by killermist on 2012-01-07
Maybe the literal:
```
rm -f "Baldo_2006-07-01?gif"
```

[edit]
Of course the alternative is backup everything else of value, reformat the filesystem, and restore the content.

---

### Post by squenson on 2012-01-07
Thank you all for your help, here is the status:

ls -i 2064227 Baldo_**tab tab** gives the following output:
ls -i 2064227 Baldo_2006-07-01^Ngif Baldo_2006-07-01^Ngif
which gives:
ls: cannot access 2064227: No such file or directory
898654 Baldo_2006-07-01?gif  898654 Baldo_2006-07-01?gif

I then run:
find . -inum 898654 -exec rm {} \;
rm: cannot remove `./Baldo_2006-07-01\016gif': No such file or directory

Note each time how the "faulty" character is replaced either by an exclamation mark, ^N or an escape sequence \016

---

### Post by carranty on 2012-01-07
Habitual had a typo in his post, ignore the red number in the first step
```

ls -i Baldo_**tab tab**

```this command will return a number which you then plug into the 

```
find . -inum #### -exec rm {} \;
```command i.e. replace #### with the number you get for the first bit.

---

### Post by squenson on 2012-01-07
I already ran that command:
```
find . -inum 898654 -exec rm {} \;
```
And I got:
```
rm: cannot remove `./Baldo_2006-07-01\016gif': No such file or directory
```

---

### Post by carranty on 2012-01-07
> **squenson said:**
> I already ran that command

Apologies, I didn't read your post properly.  I've never known that method to fail.......I'm out of ideas.  Sorry :confused:

---

### Post by squenson on 2012-01-08
I have tried again many things this morning:
 - Write a python program with the special character in the file name -> didn't work
 - Go to Windows VirtualBox and delete the file from Windows -> didn't work
 - Write a c program -> didn't work

In despair (not that much!:D) I opened Nautilus and deleted the parent folder -> it worked! I am 100% sure I tried this before, so my guess is that one of the previous attempts did the trick, most probably the command with find and the inode number.

Thank you all for your precious help and have a wonderful Sunday!

---

