---
title: "URGENT! recovery of files"
date: 2012-02-16
forum: General Help
---

### Post by louisgonick on 2012-02-16
I was working on a video project which took me hours, I accidentally overwrote it. Now its completely gone! I NEED HELP TO GET IT BACK!

---

### Post by winh8r on 2012-02-16
try testdisk/photorec


```
sudo apt-get install testdisk
```


step by step guide is here:


[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

remember to run it from another partition or from live cd.

hope this helps

---

### Post by wolfen69 on 2012-02-16
**extundelete** and **magicrescue** are two tools I know of.

---

### Post by louisgonick on 2012-02-16
> **winh8r said:**
> try testdisk/photorec


```
sudo apt-get install testdisk
```


step by step guide is here:


[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

remember to run it from another partition or from live cd.

hope this helps

> **wolfen69 said:**
> **extundelete** and **magicrescue** are two tools I know of.

How will this exactly work? any tutorials? what I lost was just a file which was replaced by another one for accident

---

### Post by louisgonick on 2012-02-16
Please somebody help me!! that project is due tomorrow and I have to start from scratch! I'm panicking!

---

### Post by winh8r on 2012-02-16
What program were you working with and what format was the video in?

---

### Post by louisgonick on 2012-02-16
> **winh8r said:**
> What program were you working with and what format was the video in?

I was working in Openshot. It was in .osp format

---

### Post by miasmablk on 2012-02-16
photorec is a really good and simple to use file recovery program. also i would avoid writing too much to the hdd, if you want to ensure recovery of lost/ deleted files.

start with finding out which partition your linux distribution is installed to 

sudo sfdisk -l

[http://debianhelp.wordpress.com/2011/07/05/how-to-use-photorec-for-data-recovery-in-ubuntu-linux/](http://debianhelp.wordpress.com/2011/07/05/how-to-use-photorec-for-data-recovery-in-ubuntu-linux/)

---

### Post by winh8r on 2012-02-16
Ok , give me 10 mins, will post back after I check if it will work for you.

---

### Post by louisgonick on 2012-02-16
> **winh8r said:**
> Ok , give me 10 mins, will post back after I check if it will work for you.

If you are able to help me you would have saved my life

---

### Post by winh8r on 2012-02-16
Post retracted to prevent confusion.

Only partial commands given.


SEE POST #13 below.

---

### Post by aasdfasdfg on 2012-02-16
> **louisgonick said:**
> How will this exactly work? any tutorials? what I lost was just a file which was replaced by another one for accident

I have had success with [extundelete]("http://extundelete.sourceforge.net/") before. In my case, I accidentally deleted my entire home directory - no files were overwritten and I was able to do a full recovery.

However, I am unfamiliar with the case you have where you wrote over a file with another file. Just asking a stupid question here, but have you already verified that the program you were using does not do autosaves? Sometimes you might be able to find autosaves of the file by looking either in the same directory as the file with ls -al to see hidden files as well, or also in the /tmp directory.

Hope you succeed!

---

### Post by winh8r on 2012-02-16
Okay, I have located the info that I had stored in a .txt file on an external hdd.

There is a reference to using this:

```
sudo apt-get install e2undel
```

Here is the .txt file:







I hope that this is of some help to you, if it is not successful then I would suggest using photorec, that way you might at least get something useable back.

---

### Post by louisgonick on 2012-02-16
Thanks to everybody who offered help,

for some very strange reason the solution was restarting my machine. The file was back intact. It must be some weird ubuntu glitch. 

The last hour and a half were the most horryfying hours of my life, this was a project that I have been working on for weeks, and having to start doing it from scratch the night before its due was going to be almost an impossible task. Thankfully the odds were on my side. 

Thanks for your time.

---

### Post by winh8r on 2012-02-16
Glad you got it back! I was dreading this method not working and you having your hopes dashed.

Might be worth while to take a copy of that .txt file I uploaded and keep it in a safe place, just in case. Or use it to run an experiment to see if it will work if you need it in future.

Oh well, panic over.

Best mark this as solved!

---

### Post by speed32219 on 2012-02-16
Backup, Backup, Backup is the lesson learned.

---

