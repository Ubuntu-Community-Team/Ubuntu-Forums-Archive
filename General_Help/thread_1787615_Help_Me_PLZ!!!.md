---
title: "Help Me PLZ!!!"
date: 2011-06-21
forum: General Help
---

### Post by sinanwawa on 2011-06-21
Hi there,
 
i am new on linux OS
 
i have a file i want to make it executble
 
the file located on the hdd in a folder called temp
 
i ran Terminal and type 
sudo chmod +x mkesxiaio_3.9.6.sh
while (mkesxiaio_3.9.6.sh) is the file that i want to make it exutble
 
when i hit enter i get the following massage
 
chmod: cannot access `mkesxiaio_4.3.1.sh': No such file or directory
 
why i got this massage???? please help me

---

### Post by nomko on 2011-06-21
First of all: never download files to the /tmp folder. Always use your Download folder => /home/{username}/Downloads. Or in your situation a folder called temp.
 
I'm not quit sure, correct if i'm wrong, but i think you don't have writing access to the /tmp folder (or your temp folder). So best is to move/copy the file to your download folder. And when you want to use that command again, try adding **sudo** before the command, this will give you root priviliges to execute that command.
 
**sudo chmod +x {filename}**

---

### Post by sinanwawa on 2011-06-21
> **nomko said:**
> First of all: never download files to the /tmp folder. Always use your Download folder => /home/{username}/Downloads. Or in your situation a folder called temp.
 
I'm not quit sure, correct if i'm wrong, but i think you don't have writing access to the /tmp folder (or your temp folder). So best is to move/copy the file to your download folder. And when you want to use that command again, try adding **sudo** before the command, this will give you root priviliges to execute that command.
 
**sudo chmod +x {filename}**
 
 
Hi Nomko
 
thnak you for ur help
actualy im using ubuntu live cd, not installed ubuntu, it works on live or not? please advise and thanks

---

### Post by 3xp10r3r|X13 on 2011-06-21
I doubt that it is down to any privileges, because you've executed it as root. But just for fun - The usual stuff: A standard user is only able to do changes to his home directory and therefore not to the rest of your system. The root user or superuser (sudo=superuser do) is allowed to do anything he wants. This feature was designed to prevent harmful software accessing your actual system without your permission. 

However, if you want to make something executable (in general), you have to right click it and select properties. Once there, you're able to tick a little box which says executable.

Just a question:

are you sure, you typed in the right stuff, because you're talking about two different versions.

By typing:
```

ls -l

```

you can have a closer look at the permissions already assigned to the files (first column)

To sum up:
just move the file to your home directory (as already suggested), mark it as executable and run it by opening the termnal, navigating to that directory and typing:

```

./executable

```
to run the program as root or as a standard user (if you need root privileges log in as root first - "su" )

I hope this helped 
Questions?

---

### Post by 3xp10r3r|X13 on 2011-06-21
ok, I've just seen your post. This changes the whole situation!!! It is just not able to install it, because you're running the system from a live cd.

Just keep the rest I've written in mind anyway...

---

### Post by WorMzy on 2011-06-21
> **sinanwawa said:**
> 
i ran Terminal and type 
sudo chmod +x mkesxiaio_3.9.6.sh
while (mkesxiaio_3.9.6.sh) is the file that i want to make it exutble
 
when i hit enter i get the following massage
 
chmod: cannot access `mkesxiaio_4.3.1.sh': No such file or directory

Did you cd to the temp directory before running this? Why are you using sudo?

```
cd /path/to/temp
chmod +x filename.sh
./filename.sh
```

---

### Post by sinanwawa on 2011-06-21
> **3xp10r3r|X13 said:**
> I doubt that it is down to any privileges, because you've executed it as root. But just for fun - The usual stuff: A standard user is only able to do changes to his home directory and therefore not to the rest of your system. The root user or superuser (sudo=superuser do) is allowed to do anything he wants. This feature was designed to prevent harmful software accessing your actual system without your permission. 
 
However, if you want to make something executable (in general), you have to right click it and select properties. Once there, you're able to tick a little box which says executable.
 
Just a question:
 
are you sure, you typed in the right stuff, because you're talking about two different versions.
 
By typing:
```

ls -l

```
 
you can have a closer look at the permissions already assigned to the files (first column)
 
To sum up:
just move the file to your home directory (as already suggested), mark it as executable and run it by opening the termnal, navigating to that directory and typing:
 
```

./executable

```
to run the program as root or as a standard user (if you need root privileges log in as root first - "su" )
 
I hope this helped 
Questions?
 
 
hi 3xp10r3r|X13;10964503
 
thank u for ur help, i am currently performing full instalation on my pc i hope it will work
 
thank u again

---

### Post by nothingspecial on 2011-06-21
> **sinanwawa said:**
> Hi there,
 
i am new on linux OS
 
i have a file i want to make it executble
 
the file located on the hdd in a folder called temp
 
i ran Terminal and type 
sudo chmod +x mkesxiaio_3.9.6.sh
while (mkesxiaio_3.9.6.sh) is the file that i want to make it exutble
 
when i hit enter i get the following massage
 
chmod: cannot access `mkesxiaio_4.3.1.sh': No such file or directory
 
why i got this massage???? please help me

You say you typed mkesxiaio_3.9.6.sh

yet the error says mkesxiaio_4.3.1.sh

---

### Post by sinanwawa on 2011-06-21
> **nothingspecial said:**
> You say you typed mkesxiaio_3.9.6.sh
 
yet the error says mkesxiaio_4.3.1.sh
 
 
no no this is a mistake while copying the lines,
 
both were  mkesxiaio_4.3.1.sh
the file inside temp folder is also mkesxiaio_4.3.1.sh
 
thanks

---

### Post by nomko on 2011-06-21
> **sinanwawa said:**
> no no this is a mistake while copying the lines,
 
both were mkesxiaio_4.3.1.sh
the file inside temp folder is also mkesxiaio_4.3.1.sh
 
thanks
 
Move that mkesxiaio_4.3.1.sh file to your own /home directory ( /home/{username}/Downloads). Then open a terminal and go to your download folder: cd /home/{username}/Downloads . Type the command sudo chmod +x mkesxiaio_4.3.1.sh. Then type in ./mkesxiaio_4.3.1.sh. What happens then?

---

### Post by sinanwawa on 2011-06-21
> **nomko said:**
> Move that mkesxiaio_4.3.1.sh file to your own /home directory ( /home/{username}/Downloads). Then open a terminal and go to your download folder: cd /home/{username}/Downloads . Type the command sudo chmod +x mkesxiaio_4.3.1.sh. Then type in ./mkesxiaio_4.3.1.sh. What happens then?
 
 
(SOLVED)thank you very much Nomko it worked like a charm after i follow ur steps
i waste my past 24 hours just becouse of these steps
 
thank u man god bless u

---

### Post by nomko on 2011-06-21
> **sinanwawa said:**
> thank u man god bless u

Your welcome! Nice to see that my solution works. And a lesson learned for you. Also something not to forget.

---

