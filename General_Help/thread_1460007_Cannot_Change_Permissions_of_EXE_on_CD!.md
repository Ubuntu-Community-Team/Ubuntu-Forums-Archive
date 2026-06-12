---
title: "Cannot Change Permissions of EXE on CD?!"
date: 2010-04-22
forum: General Help
---

### Post by Stewie2kill on 2010-04-22
I've been trying to install a few windows applications I own through wine right lately from a disc but ever since 10.04 (I'm on beta 2) it's been giving me fits and tantrums. 

The set ups are .exe's and being a little bit familiar with ubuntu I went to change the permissions only to be greeted with the error 'Sorry, could not change the permissions of "setup.exe": Error setting permissions: Read-only file system'.

Now I realize that it's imperative to keep security in Ubuntu a top priority and I appreciate it whole heartedly, but this is extremely annoying. What it seems this is telling me is, "Hey, change the permissions - oh wait, you can't ...sorry"

Maybe there's something I'm missing here. If you've got any ideas please let me hear them. I love Ubuntu and do not want to have to use Windows anymore than I have to, but this is making it quite difficult for me. I'm not afraid of terminal either or generally screwing up my system.

I should also mention I'm using a wubi install right now. If that affects anything let me know. I didn't marke the thread wubi because I think it's more of a Ubuntu issue than an issue with wubi (which I have been nothing short of the utmost of happy with).

EDIT: I'm experimenting with copying the contents of the cd into a folder and changing the permissions. This doesn't work in windows, but this is linux, so it may be a feasible strategy.

---

### Post by 3rdalbum on 2010-04-22
What do you want to change the permissions for? They don't need to have execute permission, just run them in wine like so:

```
wine <drag the executable file in the terminal>
```

---

### Post by Stewie2kill on 2010-04-22
Community never fails. That did the trick. I didn't think to drag the file into the terminal to set the file path.

I also copied the contents of the cd onto my harddrive and set the permissions there as well which also seems to have worked but in the future I'll be using your method instead.

Thanks.

---

### Post by Portmanteaufu on 2010-04-22
> **Stewie2kill said:**
> 
The set ups are .exe's and being a little bit familiar with ubuntu I went to change the permissions only to be greeted with the error 'Sorry, could not change the permissions of "setup.exe": Error setting permissions: Read-only file system'.

Now I realize that it's imperative to keep security in Ubuntu a top priority and I appreciate it whole heartedly, but this is extremely annoying. What it seems this is telling me is, "Hey, change the permissions - oh wait, you can't ...sorry"


For clarity's sake, I just wanted to mention that the error you were seeing wasn't put there for security reasons. You were trying to change the permissions on a file that was burned into a CD. Once a write-once CD has been written, you can't change anything on it -- you can't add files, delete files, or change file permissions.

That's why you were allowed to change the permissions once you had made copies of the files on your hard drive -- your hard drive isn't read-only, so the system was able to make changes to the file.

Hope that helps!

---

### Post by Stewie2kill on 2010-04-24
I suppose the confusion comes from me not understanding why changing the permissions for a file have to actually change the file itself. 

Perhaps this is one of the many differences in Linux that makes it more secure than other OS choices out there. Or maybe I'm a complete moron and it works this way under all OS's. While I've been using Ubuntu for a year, I am still technically a new user.

Thanks again for the feedback. I do want to say again that the solution provided by 3rdalbum did indeed work marvelously and I can indeed say that I have already utilized it to install several older games and a few applications I need to make the switch.

---

### Post by 3rdalbum on 2010-04-24
I'm glad I could help :-)

---

### Post by royan on 2010-04-24
First I want to say thanks, I had the same problem and this worked for me.

But I'm puzzled, why does this work? I tried to right-click the file and open with wine but that complained about permissions. What is the difference when running it from the console??? It still executes the program right?!

---

### Post by zerzu on 2011-02-07
Could someone please answer this question, I know this is a very old thread but I would really like to know the answer, I am just getting into linux.

---

### Post by Habitual on 2011-02-07
CDROM stands for Compact Disc **Read Only** Memory

-1 and OMG ):P

---

