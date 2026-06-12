---
title: "Search then delete files"
date: 2012-10-08
forum: General Help
---

### Post by slippyjim on 2012-10-08
Hiya,

I have lubuntu 11.10 installed on Acer Revo 3610 

I have always used windows and have recently changed my media PC to Lubuntu. All I want to do at the moment is search for all teh files on my PC with a certain file extension and delete them, a trivial thing to do in Windows.
So far Ive had to download & install Cat Fish and so now I can search for them and find them all, but once it has completed the search I cant do a select all and delete. I can't do anything useful with the files once I have found them at all.

How do I delete all these files?

TIA,

---

### Post by The Cog on 2012-10-08
A command like this should do it (assuming you want to delete .xyz files):
```
find / -name '*.xyz' -delete
```
You may need to use sudo in front of the command if you don't have rights to delete all the files yourself.
```
sudo find / -name '*.xyz' -delete
```

---

### Post by agillator on 2012-10-08
Doing that broad a search/remove without intervention is dangerous. Any little mistake and you have wiped out your machine. 

First, since you are new to linux, learn to use the man command. This will help you use specific commands (once you know what they are, of course). In this case the two commands you would want are find and rm. 

man find will tell you how to use find which will locate the files you want.

man rm will tell you how to remove them - you will want to use wildcards and recursion. However, BE CAREFUL. Also realize you will need correct permissions. 

Since you were not more specific, I will leave the details up to you. As I said, though, blindly and automatically removing broad batches of files is very dangerous. A minor mistype and you have wiped out everything.

---

### Post by Wim Sturkenboom on 2012-10-08
Although I've not used above command myself, I think a warning to the latter command will be in place. Use it incorrectly and you might render your installation useless.

The '/' indicates the root directory, so it might delete everything. If these files that you want to delete are in your home directory, navigate there first and replace '/' by '.'

Or use ~username (which will expand to /home/username)

```

find ~wim -name *.jpg

```
will just find and display them; add '-delete' if you want to delete them.

Note:
running it from the root directory will also wipe the (backup) data from external hard disks.

---

### Post by slippyjim on 2012-10-08
> **agillator said:**
> Doing that broad a search/remove without intervention is dangerous. Any little mistake and you have wiped out your machine. 


Its OK, I'm not deleting system files or anything like that, it is some partially downloaded files with a  specific file extension

---

### Post by slippyjim on 2012-10-08
> **Wim Sturkenboom said:**
> Although I've not used above command myself, I think a warning to the latter command will be in place. Use it incorrectly and you might render your installation useless.

The '/' indicates the root directory, so it might delete everything. If these files that you want to delete are in your home directory, navigate there first and replace '/' by '.'

Or use ~username (which will expand to /home/username)

```

find ~wim -name *.jpg

```will just find and display them; add '-delete' if you want to delete them.

Note:
running it from the root directory will also wipe the (backup) data from external hard disks.

I was just about to ask how to specify a directory and you beat me to it, perfect, all done and dusted now!!

As a slight aside, as an expert windows user for many years (its my job) switching to Linux is a lot harder than I thought. Things I take for granted in wondows are not always simple in Linux

---

### Post by The Cog on 2012-10-08
The warnings about that command are right. When used with sudo, it could delete parts of your system.

> find ~wim -name *.jpg will not work. You must put quotes round the '*.jpg' or the command interpreter will expand it into a list of all jpeg file **in the current directory** before it even reaches the find program.

Things are not generally harder in Linux, just different. Take my word for it, when a Linux user tries to use Windows occasionally he really wonders why Windows has to make simple things so hard.

---

### Post by slippyjim on 2012-10-08
> **The Cog said:**
> Things are not generally harder in Linux, just different. Take my word for it, when a Linux user tries to use Windows occasionally he really wonders why Windows has to make simple things so hard.

Haha, yeah you're probably right. Out of interest what does a linux user find difficult in windows?

---

### Post by agillator on 2012-10-08
Almost everything. In my opinion it is a matter of 'way of thinking'. I came to Linux from Windows and will never go back. In my opinion, which admittedly is years old,  . . . .

Windows is ok as long as you don't care about security and are willing to do things the way others (Bill Gates and Company) think you should do them. The thinking is similar to Ford's 'They can have any color car they want as long as it is black.' You also have to realize that you will most likely live with any bugs until the new edition comes out and you spend money on it. The structure is totally different and requires getting used to. You are forced to use 'drives' and working on a network is a pain since Windows was not originally designed for networks. Oh, and try to get Windows to recognize a non-windows file system . . . . Another difference is that Windows programs tend to try to do everything. The Linux user is used to programs being designed to do one thing and do it well, but the system is designed to let these programs be tied together to do the big things - far more flexible.

Linux, on the other hand, gives the user much more control and much more power. For that reason, if for no other, it is often a little difficult to learn. But once you understand the way of thinking and how to get information I actually found it easier to use than Windows. One example. To Linux, everything is a file. You do not have to care where something physically is located unless you want to. You only need to know where in the file structure. Documentation in Linux tends to be far better, in my experience. If there is a bug in a program, it is probably going to be found, fixed, and available far sooner  (and without cost). Since Linux was designed for networks, networking is relatively easy and almost transparent. Security is much tighter. To someone new the permission system gets in the way. But you learn how to deal with that very quickly and soon are relying on it and miss it when you have to deal with Windows file systems that don't know about permissions. 

My opinions. Your mileage will vary.

---

