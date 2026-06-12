---
title: "Wierd! Source.list is full, while Synaptic-&gt;Repositories is empty"
date: 2006-05-12
forum: General Help
---

### Post by Isoss on 2006-05-12
Ok, I am newbie and still learning ... I've been using ubuntu for a month now! I've leaned most common linux commands and how to work with repositories. Correct me if I'm wrong, but that's what I've "noticed" that when I add the repositories manually using synaptic, they should be written automatically in source.list. Now I have deleted the ones in synaptic, and then edited source.list and copied the the original repositories:
```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

```
Now when I run apt-get update it only outputs this:
```
isos@ubuntu:~$ sudo apt-get update Reading package lists... Done
isos@ubuntu:~$

```
as if source is empty. When I start synaptic it only displays INSTALLED packages, all marked in green. And of course repositores are empty.

Any help or suggestion will be appriciated.

---

### Post by Sutekh on 2006-05-12
Can you check that the path of the apt-get sources list is
```
/etc/apt/sources.list
``` Capital letters (even though there are none) and spelling must be exact

---

### Post by Isoss on 2006-05-12
OOPS! Sorry for this mistake .. I was editing the wrong file. I should've edited sources.list and not source.list.

Pardon!

---

### Post by Sutekh on 2006-05-12
NP!  Its an easy mistake to make.  

Try using the <TAB> button to help complete the names of files.  If you start typing the path/filename and press <TAB>, if there is a unique path/filename then the terminal will complete the rest for you. 

For example, editing the sources.list
```
sudo gedit /e <TAB> apt/so <TAB> 
```
Is all I need to type.  Hope thats not confusing.

---

### Post by Isoss on 2006-05-12
Actually, I use this, but I thought there is nothing else but source.list ... so when you do <TAB> it gives you source first then I continued and typed .list by myself ... 

But I just wanna know. if sources.list is the list of synaptic repositories. Then does source.list do? I don't remember whether it was empty or not .. so should it be empty or what?

---

### Post by Sutekh on 2006-05-12
There shouldn't be a source.list at all, it shouldn't exist.

Synaptic is just a GUI for apt-get, so they both use sources.list.  

You may have accidently created the file source.list, possibly by creating a backup?
```
sudo cp /etc/apt/sources.list /etc/apt/source.list
```
It'd be an easy thing to do.

---

### Post by Isoss on 2006-05-12
Yes, that could be right. anyway, I'll delete source.list. i guess everything works fine now.
Thanks

---

