---
title: "Installed mtink but..."
date: 2010-10-17
forum: General Help
---

### Post by Extreedoc on 2010-10-17
Ok, I've installed mtink and associated files to keep an eye on my Epson printer but it seems that mtink does not have enough right for accessing the device files. I have to be a member of the "lp group". I assume this is the lpadmin group? How do I proceed?

---

### Post by Extreedoc on 2010-10-18
Sorry to have to bump but...Anybody know anything about mtink at all?

---

### Post by Mark Phelps on 2010-10-18
Open a terminal and enter "sudo useradd -G lp <username>"  where <username> is your Ubuntu username.

---

### Post by Extreedoc on 2010-10-19
Thanks Mark.

---

### Post by Extreedoc on 2010-10-19
Carried out the instructions, now I get: "bash: syntax error near unexpected token 'newline'"

---

### Post by Mark Phelps on 2010-10-19
That's odd ...

OK, let's say your username is Bob Smith, then the command would be "sudo useradd -G lp bob"

IF that still does not work, let me know as I'll check my home machine tonight where I have mtink installed and confirm the details of the command.

---

### Post by Extreedoc on 2010-10-19
I entered it properly, my user name that is, I tried it several times and got the same.
Very grateful for your help Mark.
John.

---

### Post by Mark Phelps on 2010-10-19
Sorry to hear it didn't work.  I'll have to check my home machine tonight and post back later.

---

### Post by Extreedoc on 2010-10-20
I've figured out what I was doing wrong, I think, it was a syntactical error on my part. Now I get: "useradd: user user exists".
I think this might be because my user name is "user" (added by the person who installed Ubuntu on my machine). Could this be causing a problem/confusion? If I change my user name to something else... What do you think?

---

### Post by Extreedoc on 2010-10-20
Thank you Mark, I have managed to solve the problem with the help of another member: todak. Although I have to use sudo to access mtink it is a lot better than having to boot into Windows. I will mark this thread solved.
John.

---

### Post by Mark Phelps on 2010-10-21
Yeah, I know that works ... but it is a pain.

I was able to find my own implementation -- which I know works.

Given that your username is "user", do the following:

```
sudo adduser user lp
```

Then do:
```

cat /etc/group | grep lp:
```

You should get something like:
```

lp:x:7:user
```

Sorry for the confusion, but I couldn't find my reference and relied on one that obviously, was not correct.

---

### Post by Extreedoc on 2010-10-21
I entered the first line of code just fine, was asked for my password which I entered and was told that I had been added to the lp group.
On trying to enter the second line of code I find that I cannot enter the vertical bar or "Or" symbol, it just leaves a blank space there. I know it works ordinarily as I checked it in "Writer" So I carried on 'as if' it had shown the symbol but then I get a page of code with "Cannot find file" in it.
Although I am now a member of the lp group, mtink still does not work unless I borrow root powers. How do I get that vertical bar to show up on screen?
John.

---

### Post by Mark Phelps on 2010-10-21
Getting added to the lp group SHOULD be sufficient -- at least, that's what has worked for me all these years.

As to the "|" symbol, I don't know what to tell you.  It shows up OK for me.

---

### Post by Extreedoc on 2010-10-22
Ok, thanks Mark, I appreciate your efforts, I will keep trying but if I have no more success I will still be able to use it in SUDO which is a vast improvement over what I had to do before.
John.

---

### Post by Mark Phelps on 2010-10-22
It's a long shot ... but I've run out of other ideas ...

In my case, I added mtink to the Accessories menu.  In the dialogue where you enter the command, I just put "mtink".

When I first started using this years ago, I now remember that I had similar problems to your.  So, I experimented with the menu item command entry by using "sudo <pathame>/mtink" and "gkduso <pathname>/mtink".

It's been so long now, I don't remember which one worked.  And currently, I don't use sudo at all for it.  But you could try these as a last resort and see if either one lets you launch it without having to enter the password.

---

### Post by Extreedoc on 2010-10-23
Thanks, you have given me a few things to go at and I will keep trying.
John

---

