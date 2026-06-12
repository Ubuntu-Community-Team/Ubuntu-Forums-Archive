---
title: "File ownership/permission problems in xubuntu 11.10"
date: 2011-10-24
forum: General Help
---

### Post by bothide on 2011-10-24
File ownership/permission problems in the /usr tree on xubuntu 11.10.

Since yesteday, the GUI for the synaptic package manager does not work for ordinary users, only for root.
Yesterday, I had some issues after inadvertently changing of the users/group osnership and persmissions in the usr tree.  But I still think there be one or two files that have wrong ownershoip and/or permssion. As an ordinay user, I can do 'sudo synaptic' end everything seems to run fine (perhaps a bit slower than before the mishap?).

Is there a manifest/master file with a listing of all the files and their attributesi in the 11.10 original distro?  Or, better still, is there a command (like in UNIX) where you can scan the whole directory tree to detect unwanted changes/muistakes?

I would be delighted to receive a prompt reply.

Thanks a lot,

Bo
[email]bt@irfu.se[/email]

---

### Post by gsmanners on 2011-10-24
> **bothide said:**
> Since yesteday, the GUI for the synaptic package manager does not work for ordinary users, only for root.

Okay, so that's working as designed, then. If it was working for anyone other than root, then that was a security issue and needed to be stopped.

> Yesterday, I had some issues after inadvertently changing of the users/group osnership and persmissions in the usr tree.  But I still think there be one or two files that have wrong ownershoip and/or permssion. As an ordinay user, I can do 'sudo synaptic' end everything seems to run fine (perhaps a bit slower than before the mishap?).

How exactly did you "inadvertently" change ownership of those files? If you did that from a terminal, it would be a simple matter of tracking it down from the ~/.bash_history file and undoing whatever you did there.

---

### Post by bothide on 2011-10-24
Strange.  It has worked in all versions of ubuntu that I have run so far.  It is only when you actually install or remove something that you are asked for the password...

I was meaning to make a recursive change of owner to bin:bin in a subdirectory of the /usr tree but for various reasons the command kicked in on /usr itself and /usr contains an awful lot of files...  The history file is of no use here (it just shows me what I happened to do and I already knew that). Now, if I only could have access to a "ls -lR" of /usr, I would be much helped.

Thanks in advance.

---

### Post by gsmanners on 2011-10-24
I'm not a mind reader, so any time you want to post specifics would be great.

```
cat ~/.bash_history
```

Would help me help you. Mind you, I don't need the whole thing. Just the part where things went awry.

---

### Post by bothide on 2011-10-25
As I said, I inadvertently did a recursive change of ownership on /usr,  that is,  I erroneously did 'chown -R bin:bin /usr' whereas I was meaning to do 'chown -R bin:bin: /usr/xxx/yyy/zzz' (where 'xxx' etc stand for actual subdirectory names). How I did it is perhaps not the important thing.  What I am looking for is a way of finding out what the ownership for the files and subdirectories in /usr are supposed to be in 11.10 for correct functionality and behaviour.  Surely, there must be a command in ubuntu where I can check and rectify things like this. or am I wrong?

PS. I run zsh, not bash, but that's a little beside the point.

---

### Post by gsmanners on 2011-10-25
Right. Most of the files are owned by root in that folder. The problem is that in the time we've been discussing this, I could have backup and reinstalled my own system about 8 times. If you have the means to do this, I would highly recommend it, as "fixing" all the irregular ownerships would take a very long time.

---

### Post by bothide on 2011-10-25
Look, I had just installed 11.10, fixing a few things before I was about to make the first backup when this happened!  The 11.10 has not been around for very long, you know.  There is no need to be abrasive, since I am asking a legitimate question, regardless if I my fingers would have slipped the other night or not...

Honestly, how difficult could it be to make a list of the files in a given release as a part of the release?  The commercial-grade unices that I work with since 20 years always include such lists.  Partly as a service, partly as a security means, allowing the sysadmin to compare the system files against such a list to check whether the system files have been tampered with - advertently or inadvertently.  Had I known that ubuntu does not come with such a list, I would of course have generated one myself first thing after I had installed it. Now I am simply asking for some help.  Pehaps somebody out there would be so kind to make such a list for
me?  Somtheing like
cd /
ls -lR /usr > filename
and then mail the file filename to [email]bt@irfu.se[/email].  Shouldn't take more than a few minutes.  It would have saved me many, many hours of work...

---

### Post by Sorinux on 2011-10-25
Hello!
Because I could not find nothing related to my problem I will post in this thread. It is related to Xubuntu but not sure what is the problem!
The situation is strange. I was upset with Unity and Gnome 3 and I started testing different distros. I was keeping a save of the files that I usually have on my Desktop (I use them often) and after the new installation, I was just cut/paste  the files to the desktop.
A few days ago I installed Lubuntu and because I did not like it, I decided to try also Xubuntu. After the installation, I went to my external HDD and I cut the files I wanted and paste them to the new desktop. 
The strange thing is that after the transfer was finished I did not noticed if the files are in the correct position. I gave to command that I use to take ownership on the new system and when I tried to go to the new location to see the files.... SURPRISE!!! In my Desktop and Pictures folder was nothing. I tried to search everywhere in /home, also I looked in all the root partition, but there is no trace of my files!
Strange thing is that if I open the partition manager, I see that actually the partition has the space used by exactly the same size that this files had.
My question is how did this happened? What did I do wrong? Somebody else had this kind of problem?
Any suggestion is welcomed!

---

### Post by gsmanners on 2011-10-25
Hi, Sorinux. I'll give you the same advice:

Backup your files. Make sure your files are securely copied to a device somewhere that you trust.

Reinstall your system.

The above will only take about an hour (two if you include all the little things you have to do afterward).

---

### Post by Sorinux on 2011-10-25
> **gsmanners said:**
> Hi, Sorinux. I'll give you the same advice:

Backup your files. Make sure your files are securely copied to a device somewhere that you trust.

Reinstall your system.

The above will only take about an hour (two if you include all the little things you have to do afterward).

Come on man, is not helping your comment. I just said that I had backup. From using the backup things went crazy. How to see again the files? Because according to the space used, they are still there.
I will install again the system, I just hope some genius will come to give me some idea before I do that, because I am really lost with this one! I still have hope to recover some of the files!!!
I must admit that after this happened to me, I will probably stop using the CUT command.

---

