---
title: "help needed with disk space"
date: 2012-04-24
forum: General Help
---

### Post by fra11 on 2012-04-24
Dear all
I need to ask you a very stupid question which is however driving me crazy.
I'm running out of space on my home directory but although I delete stuff the used space doesn't change. I thought I had to empty the trash bin, however that is empty aswell...
How can that be possible?
Thanks a lot:confused:

---

### Post by newbie-user on 2012-04-24
Check the hidden directories. You might have stuff in there you don't need. In the file browser, open your home folder and press ctrl+h to make the hidden files visible. If you're doing this in a terminal, then ls -a will show all hidden files. Be careful doing this, though, there are some config files that you probably need in those hidden files.

---

### Post by fra11 on 2012-04-24
Thank you very much for your suggestions. However the hidden items look like configuration files to me, not places where massive amounts of data could ended up being... :/

---

### Post by papibe on 2012-04-24
Hi fra11.

Try running 'Disk Usage Analyzer'. Press the button 'Scan Home'. That should should show you how big your directories are, and browse to find big files and directories.

I hope that helps. Tell us how it goes.
Regards

---

### Post by strask on 2012-04-24
What version of ubuntu are you using? 

In my Ubuntu 11.10 install I have a very useful program called "Disk Usage Analyzer" that you could find by just typing "disk" in the dash search box. It helps with exactly the problem you are having.

Edit: Ninja'd! :)

---

### Post by newbie-user on 2012-04-24
Is your home directory in its own partition on the hard drive? How much space do you have left and how much did you start with?

---

### Post by codemaniac on 2012-04-24
Check dish usage of your home directory .On a terminal
```
du -sh ~
```

---

### Post by fra11 on 2012-04-24
Hi!
I tried 

```

du -sh ~

```

and got 22GB. Is that the disk used or the one left?

The version is 2.6.32-5-amd64


I'm on remote on my home directory now so I have to do everything by terminal. If I run 

```

df

```

I get 92% of use

but when I started deleting stuff (which means more than half of the stuff I had there) I had a use of 97%. How is it possible?

Thanks

---

### Post by fra11 on 2012-04-24
Btw I don't have the disk command :/ and my home directory I guess is on an external disk. Actually it is my work computer I'm talking about and I have a home directory stored on some server at which my computer is connected.

---

### Post by strask on 2012-04-24
> **fra11 said:**
> Hi!
I tried 

```

du -sh ~

```and got 22GB. Is that the disk used or the one left?
The du command lists _**D**_isk _**U**_sed, so that is the amount of space your home directory is taking up.

> I get 92% of use

but when I started deleting stuff (which means more than half of the stuff I had there) I had a use of 97%. How is it possible?
That would be possible if you have some program still running that is actively writing to disk, it could be filling it up faster than you are deleting things.

---

### Post by strask on 2012-04-24
> **fra11 said:**
> Btw I don't have the disk command :/ and my home directory I guess is on an external disk. Actually it is my work computer I'm talking about and I have a home directory stored on some server at which my computer is connected.

Oh! If your home directory is on a server, it is likely that the server also holds the home directories for many other users too. And often all on the same partition. So maybe the space is being used up by someone else's home directory and not your own, but you would have no way of knowing that.

I would call your system administrator or help desk and see if they can help.

---

### Post by fra11 on 2012-04-24
I do have some simulations running but the 92% has been still since the beginning of those.
However I should have something like 100 GB of free space so how is it possible that it is 92% occupied if the Disk Used is 22 GB? I'm really confused...sorry

---

### Post by fra11 on 2012-04-24
> **strask said:**
> Oh! If your home directory is on a server, it is likely that the server also holds the home directories for many other users too. And often all on the same partition. So maybe the space is being used up by someone else's home directory and not your own, but you would have no way of knowing that.

I would call your system administrator or help desk and see if they can help.

Ahahah that is exactly why I'm here asking this questions!Essentially because my help desk hasn't been helpful at all!
Actually when I resented them my space problem they replied that I should ask to my group colleagues to give me more space...
However I have these simulations running and I would like not to lose them due to lack of space. Any idea how to prevent that at least until next morning when I can come back as angry as ever to the "help" desk people?
Thank you and sorry for bothering so much

---

### Post by strask on 2012-04-24
Here is one possible scenario; I'm using made-up numbers. 

Let's say the server at your work has 5TB of disk space for user directories. There are 100 users, so that would mean 50GB for each user if you divided it up fairly. But not everyone needs that much disk space, and some people need more. So they put a limit of 100GB on each user, and assume that not everyone will use that much.

So now enough people are using more than 50GB that the disk is getting pretty full.... it's using up 92% of the 5TB, that's all users combined. That's the number you see in 'df' even though you are only using 22% of your 100GB. 

Make sense?

---

### Post by fra11 on 2012-04-24
It might be. We are all struggling for some space there. But then it is not my fault!Why should my poor simulations dye????
However, that doesn't solve the problem... :/

---

### Post by strask on 2012-04-24
How low is the space, actually? You haven't said. Do 'df -h' and see what it says for free space.

How much space does your simulation need?

Is there anything you (or another user with the same home directory disk) can move to other storage for now?

---

### Post by fra11 on 2012-04-24
Using the df -h command it came out that the size of my home directory is actually 8.1T  of which I have used 7.0T and consequently I have 662G free left which corresponds to a  92% of the disk used.
However if I run du in my home directory I get only 22G used. Where is the rest? This comes back to my first idea that when deleting files they were actually being stored in some kind of trash folder that I need to empty, however I cannot find it.

I don't really know how much space my simulations will require, but I guess a lot...
Now I have only the necessary stuff in my home directory, so I cannot move anything and I'll see my colleagues on the morrow only...

---

### Post by strask on 2012-04-24
> **fra11 said:**
> Using the df -h command it came out that the size of my home directory is actually 8.1T  of which I have used 7.0T and consequently I have 662G free left which corresponds to a  92% of the disk used.
Ok, so the actual disk on the server has 662GB available. You said earlier that you are supposed to have 100GB of space assigned to you, I think. So if you are using 22GB,  you should have 78GB left for your simulations to use.

> However if I run du in my home directory I get only 22G used. Where is the rest?

The rest of the used 7TB of disk is being used by other users, not you. There is nothing you can do about that, and you shouldn't worry about it.

---

### Post by fra11 on 2012-04-24
Thank you very much for help end support. :)

---

