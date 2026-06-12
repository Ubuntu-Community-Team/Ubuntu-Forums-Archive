---
title: "Want to install packages (no internet)"
date: 2006-03-31
forum: General Help
---

### Post by NoteMe on 2006-03-31
I am pretty new to Linux, so don't laugh too much. But after a bit back and forth, I managed to install ubuntu yesterday on a machine that won't have internet for an other two weeks. But I am eager to get started, and want to install things like Emacs, Mono, and Monodevelop and stuff like that as fast as possible. So my question is, what is my possebilities. 

- Can I bring them on a USB Stick and still use Apt-Get?
- Burn them on a CD, and still use ?
- Or do I have to compile them my self now?


And where do I get them from?


An other side question is. That for some security reason I can't log in as root from that "bootup screen", but how can I log in for root (I mean not just using 'su')? Because I tried to click on the "Install aditional packages", and the "change login options" thingies in the menu, and nothing happend. So I guess I have to be root to do that? Or am I wrong?


Thanks in advance.
- ØØ -

---

### Post by Mustard on 2006-03-31
With regards to the root questions please read this page.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Ideally you would not log in as root, as it's disabled by default in an Ubuntu install and we use sudo instead.  If you really must have a root login for whatever reason, it is possible.  It's just not necessary.

With regards to installing stuff offline, it's not going to be an easy process. All the packages are available at this location [http://packages.ubuntu.com](http://packages.ubuntu.com) but you are going to have to not only download the packages you want, but the dependencies for those packages.  Working out those dependencies is going to be a time consuming process.

You would install them using the dpkg command an example of this is below..

```
sudo dpkg -i packagename.deb

#installing multiple packages at one time 
#you can write them all on the same line

sudo dpkg -i packagename.deb packagename2.deb packagename3.deb

```

---

### Post by NoteMe on 2006-03-31
[QUOTE=Mustard]With regards to the root questions please read this page.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Ideally you would not log in as root, as it's disabled by default in an Ubuntu install and we use sudo instead.  If you really must have a root login for whatever reason, it is possible.  It's just not necessary.
[/QUOTE]

Ok, got you. Never used that before, but it looks easy. 

But I still don't then get why the meny items: "Add new application" and "change log on screen" is there. If you have to be root to click them, but root is disabled. Arn't they just waste of space then? Or am I missing something?


[QUOTE=Mustard]
With regards to installing stuff offline, it's not going to be an easy process. All the packages are available at this location [http://packages.ubuntu.com](http://packages.ubuntu.com) but you are going to have to not only download the packages you want, but the dependencies for those packages.  Working out those dependencies is going to be a time consuming process.

You would install them using the dpkg command an example of this is below..

```
sudo dpkg -i packagename.deb

#installing multiple packages at one time 
#you can write them all on the same line

sudo dpkg -i packagename.deb packagename2.deb packagename3.deb

```[/QUOTE]


Ohh, didn't think about that. Then mono and monodevelop might be overkill, but I guess I can still try Emacs. I do indeed have two weeks on me anyway, it can't me THAT many..:)

Thanks a lot.
- ØØ -

---

### Post by Mustard on 2006-03-31
[QUOTE=NoteMe]But I still don't then get why the meny items: "Add new application" and "change log on screen" is there. If you have to be root to click them, but root is disabled. Arn't they just waste of space then? Or am I missing something?[/QUOTE]

Yeah, you are missing something.  The password it is asking for is your **user password**, because there is no root password.  You are not the first to be confused by this either. Many have come before you. ;)

-edit-

I should mention that there is a community inspired project underway to create an ADDON CD for those who don't have an internet connection.  I can't recall where in the forum this discussion is going on, nor do I know how far it has progressed.

---

### Post by NoteMe on 2006-03-31
> **Mustard]Yeah, you are missing something.  The password it is asking for is your **user password**, because there is no root password.  You are not the first to be confused by this either. Many have come before you.  said:**
> 

I am not sure if we are talking about the same here right now. Since I'm obviously not sitting in Ubuntu right now, I had to google for some images. here are the two menu items I mean.


[img]http://www.noteme.com/images/ss/ubuntu.gif[/img]

[img]http://www.noteme.com/images/ss/ubuntu2.gif[/img]


When I press those, I can see the machine is working, but then nothing happens. They never ask me for any password at all. Thats why I thought I had to run as root. Am I misstaken. Has something gone wrong during install after all, and they where supposed to show up something even if I am not root?




[QUOTE=Mustard]
I should mention that there is a community inspired project underway to create an ADDON CD for those who don't have an internet connection.  I can't recall where in the forum this discussion is going on, nor do I know how far it has progressed.


Thanks, I'll have a look for it. Sounds like exactly what I need.

- ØØ -

---

### Post by Mustard on 2006-03-31
Ah ok... Did you use expert install?  The default install sets up the first user account with superuser privileges.  The expert install option sets up a normal user account (no superuser privileges), but asks you to set a root password in the install process.

Do you remember setting a root password during install?

Either way, lets test if you have superuser access...

Type this in terminal (the terminal is in Applications>>Accessories menu)..

```
sudo whoami
```

It should tell you that you are 'root' if you are a superuser.  If it doesnt I suspect your current user is not set up to be a superuser.

---

### Post by NoteMe on 2006-03-31
[QUOTE=Mustard]Ah ok... Did you use expert install?  The default install sets up the first user account with superuser privileges.  The expert install option sets up a normal user account (no superuser privileges), but asks you to set a root password in the install process.

Do you remember setting a root password during install?
[/QUOTE]

You read me like an open book. You must be terrible gifted, you surely know what you are talking about. 

Yes I did an expert install, since I wanted to chose my own Kernel. I did that when I installed Debian. 

But if that is causing it, then I guess it wasn't a smart idea after all. When I get home tonight I will install it over again. It is just stupid of me to pretend I am an expert at this stage anyway..:)

Thanks a lot.

[QUOTE=Mustard]
Either way, lets test if you have superuser access...

Type this in terminal (the terminal is in Applications>>Accessories menu)..

```
sudo whoami
```

It should tell you that you are 'root' if you are a superuser.  If it doesnt I suspect your current user is not set up to be a superuser.[/QUOTE]


I think we know the answer to this already. But I will do it when I get home tonight just in case. Thanks


- ØØ -

---

### Post by Mustard on 2006-03-31
[QUOTE=NoteMe]You read me like an open book. You must be terrible gifted, you surely know what you are talking about. 

Yes I did an expert install, since I wanted to chose my own Kernel. I did that when I installed Debian. 

But if that is causing it, then I guess it wasn't a smart idea after all. When I get home tonight I will install it over again. It is just stupid of me to pretend I am an expert at this stage anyway..:)

Thanks a lot.




I think we know the answer to this already. But I will do it when I get home tonight just in case. Thanks


- ØØ -[/QUOTE]

It's not necessary to reinstall at this stage.

Use the su command in a terminal and then enter your root password.

```
su
```

Once at the root prompt you can use this command to edit the /etc/sudoers file..

```
visudo  #this command does on thing.  It opens the sudoers file for editing
```

My sudoers file looks like this.  Note the last line where I give my user sudo privileges.  This is the line that would need to be added by those who, for whatever reason, don't have sudo privileges.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mustard ALL=(ALL) ALL

```

You can see my username on the bottom line.  You would need to add your username to the bottom as I have done.

Assuming your user name was "bob'', then the line that would need to be added would be..
```
bob ALL=(ALL) ALL
```

This is just one way of doing it.  Some sudoers files are set up with an admin group called 'adm'.  Users are then added to the adm group, and a line in the sudoers file that looks like this below gives members of the 'adm' group admin access.
```
%adm ALL=(ALL) ALL
```

If you decided to do it this way you would create the line above at the bottom of your sudoers file then do this command (substituting your username in the appropriate place)..

Save the sudoers file and exit visudo.

```
adduser your_username adm
```

You should now be a superuser with your user account.

---

### Post by NoteMe on 2006-03-31
Thanks a million, you just saved me an hour of installation too. 

Ubuntu looks like everything I missed with Debian already, and I already like the communtity around Ubuntu too. 

Thanks a lot for all your help. You have no idea how much I appreciate it.
- ØØ -

---

### Post by red_shrike on 2006-03-31
There are Torrent DVD images for Main, Universe and Multiverse. Theay contain everything you will ever need in your life on your Ubuntu machine. For the sake of root, you can enable it from a console
1. $ sudo passwd root
2. $ type and confirem ur password
3. ctrl+alt+f1 
4. login with ur new root user password
5. $ startx

Voila, GDM will start .....

---

### Post by NoteMe on 2006-04-01
Thanks, got sudo up and running, and emacs is installed with all its shiny bling bling..:)

But I have one more questions about how to use this sudo stuff. I can see that Ubuntu have mounted (at least it looks like it) some random NTFS partitions. But they are all owned by root. Doing:

sudo chown myusername:myusername hda2

does nothing. It just prints out:

"chown: changing ownership of 'hda2'. Read only file system"

Am I supposed to be able to get access to these partitions in some way with my own user account? If so how?


- ØØ -

---

### Post by Mustard on 2006-04-01
In this link below it shows the changes you need to make if you want to temporarily mount NTFS or FAT32, and also how to make those changes permanent.  Read all four examples, but the ones that are relevant to you are going to be the NTFS ones of course.  Choose whether you want to mount them permanently or just mount temporarily and then go with the method that suits you. One important bit of information is that NTFS is read only in linux.  You won't be able to write to your NTFS partitions from linux, only FAT32 partitions will allow that (at this current point in time)

[http://easylinux.info/wiki/Ubuntu#Windows](http://easylinux.info/wiki/Ubuntu#Windows)

Any questions you have put them in this thread. :)

---

