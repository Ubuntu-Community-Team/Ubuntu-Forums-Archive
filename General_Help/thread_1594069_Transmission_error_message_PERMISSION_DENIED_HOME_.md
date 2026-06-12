---
title: "Transmission error message PERMISSION DENIED HOME FOLDER/DOWNLOADS"
date: 2010-10-12
forum: General Help
---

### Post by Like67ninjas on 2010-10-12
Hey guys, recently i was trying to download some torrents and for whatever reason now my transmission gives me this Error: Permission Denied (home/user/downloads/Torrent name) message, and i go to my downloads folder and there is a padlock symbol above it and a program in there that I cant delete, I think its from when I tried to get runes of magic to work, but regardless, I cant remove it.  I thought my family had blocked p2p file sharing on me but I can still use frostwire and download other things, any help?

---

### Post by Like67ninjas on 2010-10-12
bump can someone please try and help me with this

---

### Post by WorMzy on 2010-10-12
What does ```
ls -l /home/user/downloads/
``` tell you?

---

### Post by yetiman64 on 2010-10-12
In the Downoads folder right click on the "Torrent Name" folder and choose Properties > Permissions tab.

Firstly you should own that folder, if this is the case, then it is as simple as adjusting the folder access to Create and Delete files and file access to Read and Write for yourself, also press the "Apply permissions to enclosed files" button at the bottom of the tab.

If root (or anyone else but you) is the owner of the folder then a simple terminal command can change it (chown) - it should be in your ownership though, let us know if it isn't.

---

### Post by Like67ninjas on 2010-10-13
> **yetiman64 said:**
> In the Downoads folder right click on the "Torrent Name" folder and choose Properties > Permissions tab.

Firstly you should own that folder, if this is the case, then it is as simple as adjusting the folder access to Create and Delete files and file access to Read and Write for yourself, also press the "Apply permissions to enclosed files" button at the bottom of the tab.

If root (or anyone else but you) is the owner of the folder then a simple terminal command can change it (chown) - it should be in your ownership though, let us know if it isn't.

Hey yeti, I was at a friends house last night and hes the one that got me into linux, he told me the padlock means it belongs to root now (which made me lol because of the way he said it) "It.....belongs to root now.." haha but in any case, he mentioned something about chown, could you tell me what I need to do for that, I dont know alot of the commands.

---

### Post by yetiman64 on 2010-10-13
Hi Like67ninjas, my previous post was the graphical interface means for you to _*check and set*_ the permissions (provided you own the folder - which it can also indicate to you).

> he told me the padlock means it belongs to root now It can mean exactly that (ownership) **or **if you own it, it is a read only folder (permissions). Either ownership or permissions issues or both together can cause the padlock on a folder.

We need to know what we are dealing with before chmod or chown are advised, so from terminal use what is basically WorMzy's 1st command (slightly altered only),

```
ls -l ~/Downloads | grep <torrent>
``` ~ is the same as /home/user to your system. 

Replace <torrent> with the actual folder name and enclose it in quotes **if** it contains any spaces. 

The "| grep <torrent>" is used to restrict the terminal output to the torrent folder (I don't think we need to see all your download folder contents just the torrent folder ;)) 

Also note the terminal is case sensitive, hence my capitalising the "d" in Downloads. Copying and pasting the above command into a terminal is the most accurate way to use the above command and when used, copy and paste the terminal output back here so we can help you sort the issue further.

---

### Post by Like67ninjas on 2010-10-13
> **yetiman64 said:**
> Hi Like67ninjas, my previous post was the graphical interface means for you to _*check and set*_ the permissions (provided you own the folder - which it can also indicate to you).

 It can mean exactly that (ownership) **or **if you own it, it is a read only folder (permissions). Either ownership or permissions issues or both together can cause the padlock on a folder.

We need to know what we are dealing with before chmod or chown are advised, so from terminal use what is basically WorMzy's 1st command (slightly altered only),

```
ls -l ~/Downloads | grep <torrent>
``` ~ is the same as /home/user to your system. 

Replace <torrent> with the actual folder name and enclose it in quotes **if** it contains any spaces. 

The "| grep <torrent>" is used to restrict the terminal output to the torrent folder (I don't think we need to see all your download folder contents just the torrent folder ;)) 

Also note the terminal is case sensitive, hence my capitalising the "d" in Downloads. Copying and pasting the above command into a terminal is the most accurate way to use the above command and when used, copy and paste the terminal output back here so we can help you sort the issue further.

I copied and pasted the command replacing the TORRENT with the name of the file, also enclosed it in quotes, then tried to download it again and it started to for a few seconds then gave me the same error message so idk what to do, btw its just the office season 1 lol, but Its really annoying that I cant use torrents at the moment, just wanna get it straightened out idk how I lost permissions to my downloads folder honestly.

I hardly ever use the terminal for anything so I dont know commands and alot of the technical terms associated with the terminal.

---

### Post by yetiman64 on 2010-10-13
> **Like67ninjas said:**
> I copied and pasted the command replacing the TORRENT with the name of the **file**, also enclosed it in quotes, then tried to download it again and it started to for a few seconds then gave me the same error message so idk what to do, btw its just the office season 1 lol, but Its really annoying that I cant use torrents at the moment, just wanna get it straightened out idk how I lost permissions to my downloads folder honestly.

I hardly ever use the terminal for anything so I dont know commands and alot of the technical terms associated with the terminal.

Note, the command I and wormzy have given is to gather information to help you out, not to actually fix the problem (that is the next step along, don't try using transmission till the permissions problem is sorted).

Also in my previous posts I assumed that <torrent> was a folder not a file, however it doesn't make any difference to the command or process (a bit maybe for a file - but we can sort that :).)

You have 2 options

1. use the method I described in post #4, only adjust it by doing it on the Downloads folder itself.
2. use terminal commands to gather info **and later on** fix any problem. We can talk you through the process step by step if necessary ;). 

You could also check the permissions of the downloads folder itself with
```
ls -l ~/ | grep Downloads
``` **and post the results back here** (via the editor you are composing your replies in. Best to put the output in quote tags {located on the reply editor toolbar}).

We'll try to keep instructions as simple as possible but we do need to use the terminal to gather information at times to help you, if you don't use the graphical method explained in post #4.

---

### Post by Like67ninjas on 2010-10-15
when I put that in it says 

hon@hon-desktop:~$ ls -l ~/ | grep Downloads
dr-xr-xr-x  2 hon hon    4096 2010-09-12 19:44 Downloads
hon@hon-desktop:~$

---

### Post by endotherm on 2010-10-15
> **Like67ninjas said:**
> when I put that in it says 

hon@hon-desktop:~$ ls -l ~/ | grep Downloads
dr-xr-xr-x  2 hon hon    4096 2010-09-12 19:44 Downloads
hon@hon-desktop:~$

ok, it looks like you don't have write access to the directory, but you own it, so that simplifies matters. 
try this:
```

chmod -R u+w ~/Downloads

```

this will give you write permission on all files within downloads.
it will not help however if files within downloads are owned by root though, so paste back the output of:
```
ls -l ~/Downloads
```
you can delete the file names for your privacy if you wish, but leave the part of the line that looks like "dr-xr-xr-x  2 hon hon "

---

### Post by yetiman64 on 2010-10-15
Those permissions are wrong, needs to be like drwxr-xr-x to give you write permission,
in terminal use,

```
chmod 755 ~/Downloads
``` then use the command you just did **again** and compare the output to drwxr-xr-x (ownership is fine). If they match try out the torrent again.

Edit: endotherm got there, just noticed :smile:

---

### Post by Like67ninjas on 2010-10-16
> **yetiman64 said:**
> Those permissions are wrong, needs to be like drwxr-xr-x to give you write permission,
in terminal use,

```
chmod 755 ~/Downloads
``` then use the command you just did **again** and compare the output to drwxr-xr-x (ownership is fine). If they match try out the torrent again.

Edit: endotherm got there, just noticed :smile:


thanks guys its all fixed now, woulda been screwed without ya

---

### Post by yetiman64 on 2010-10-16
> **Like67ninjas said:**
> thanks guys its all fixed now, woulda been screwed without ya

You're welcome Like67ninjas, It's good to hear it's worked for you. Could you mark the thread as solved please? Link #5 in my sig has instructions on how to. Cheers.

---

