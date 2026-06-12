---
title: "My projects folder got disappeared on Ubuntu 9.04"
date: 2009-11-16
forum: General Help
---

### Post by kronomia on 2009-11-16
[SIZE=3]Dear Ubuntu user,

Please, I faced a problem last night which is totally strange; _**My projects folder simply got disappeared as if it was permanently deleted.**_ This is the first time i encouter such an event in an Ubuntu System. Please anyone have any idea what happened? Is this a bug or something. I am quite sure that i didn't do anything abnormal on that day. I am not new to Ubuntu. I was used to work with Fedora and Unix-based systems before. I hope the Debian-based Ubuntu is not the cause of the problem.

[B]_I am using the following:_
*Ubuntu 9.04- the Jaunty Jackalope - 32bit edition
*GNOME Version: 2.26.1
*The folder that disappeared is located in sub-folder in my home directory: home/user/myFiles/myFolder
[/B]
I will be waiting for your help,

Thanks a lot and regards,[/SIZE]

---

### Post by blazemore on 2009-11-16
Okay I'm going to assume it was projects with a small 'p', if it wasn't, please substitute the correct capitalisation:

Do this in the terminal:
```
ls -R -a /home | grep projects
```

That will list EVERY SINGLE FILE in your home directory, including hidden files, with one on each line.
however, it will only display lines containing the word "project".

Good luck!

Secondly, if it really doesn't come up, see if anyone else has had access to your computer and may have deleted it.
if not, don't rule out hardware failure. Back up immediately and switch to a new drive.

---

### Post by kronomia on 2009-11-16
[COLOR=Navy]**Thanks man for your post, here are some more information**[/COLOR][U][B]

Here are more details:[/B][/U]
*I am the only user and admin on the computer.
*This is only one operating system that is running: Ubuntu 9.04
*There is no partitions at all... I have only one partition which the operating system resides on.
*The type of the partition is: ext3. I used to feel comfortable with ext3.

_**What i think:**_

**Reason #1:** I used to to do "suspend" a lot during the day while programs are running which may cause loss of data.
**Reason #2:** My Hard drive has experiences some bad sectors in the past but i managed to isolate them successfully. Still though, it might have something to do with that.

_**What i tried to do before posting:**_

_**Try #1:**_ I tried to recover deleted files assuming that my files got deleted somehow. 
I used the following commands:


```
foremost -v -q -t cpp -i /dev/sda1 -T
foremost -v -t cpp -i /dev/sda1 -T
```But really both of them were no use... It was taking more than 6 hours without any progress. As you can see i lost (.cpp) files as I am a C++ programmer. :wink:

_**Try #2:**_ Then i decided to check if that is the only file that got deleted. It seems that indeed it was the only one. So i proceeded to the next step which it was making sure if the files are exist or not. So i carried an intensive search for specific files. No results found.

_**Try #3:**_ I applied all your directions starting with:

ls -R -a /home | grep projects
Technically specaking it was giving me ssome results from the folder named "output", you know that folder that is used by "formost tool" of recovery to output the results of headers or footers that are previously deleted. I was despritaly trying to recover deleted files through formost of course after assuming that they were deleted and not disappeared. It kind of spooky when i think about it.

_**What am sure of:**_
1. I am quite sure that the night where the event happened I was doing ordinary everyday stuff.
2. I didn't upgrade or download anything.
3. I didn't delete the files by mistake - unless if i completely lost it! 
4. I didn't install or removed any programs.
5. No one accessed my PC, as I am the only owner and user of it.

[COLOR=Navy]**Thanks again for everything man, I really appreciate your time, help and support. :KS**[/COLOR]

---

