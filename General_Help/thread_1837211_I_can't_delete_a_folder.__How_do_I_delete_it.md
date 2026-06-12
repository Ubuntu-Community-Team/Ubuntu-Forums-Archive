---
title: "I can't delete a folder.  How do I delete it?"
date: 2011-09-01
forum: General Help
---

### Post by pretty_whistle on 2011-09-01
I can't delete a folder.

I tried this but it says no such file or directory:

> sudo rm -r 2011-08-31-19-imgsavedUbuntu

After the -r is the folder name btw.


How do I get the folder deleted?

---

### Post by tingxyu1996 on 2011-09-01
try:
sudo rm -rf <folder name>

---

### Post by nothingspecial on 2011-09-01
> **tingxyu1996 said:**
> try:
sudo rm -rf <folder name>

That's not going to work if bash says no such file or directory.

1. Linux is case sensetive
2. Have you spelled it correctly?
3. Are you in the directory that folder is in?

---

### Post by gandaran on 2011-09-01
> **pretty_whistle said:**
> I can't delete a folder.

I tried this but it says no such file or directory:



After the -r is the folder name btw.


How do I get the folder deleted?
you have to enter the path to the file in the command or you get the no such file or directory error

---

### Post by saltmarshlamb on 2011-09-01
Are you in the correct place to remove it?

While in the terminal do

```
ls 2011-08*
```

If it's not shown then you need to move to the right directory first - for example if it's in your home in a backup folder

```
cd ~/backup
```

then run the rm command

Or you can run a file browser as root as I said in the other thread

```
gksudo nautilus
```

If you still can't find it - update the dbase

```
sudo updatedb
locate 2011-08-31-19-imgsavedUbuntu
```

---

### Post by haqking on 2011-09-01
> **pretty_whistle said:**
> I can't delete a folder.

I tried this but it says no such file or directory:



After the -r is the folder name btw.


How do I get the folder deleted?

I am assuming this is pertaining to your earlier thread ?

[http://ubuntuforums.org/showthread.php?t=1837057](http://ubuntuforums.org/showthread.php?t=1837057)

try not to multipost, keep it altogether as it is same subject.

use tab completion to complete the filename.

or delete it from within nautilus

---

### Post by tingxyu1996 on 2011-09-01
> **nothingspecial said:**
> That's not going to work if bash says no such file or directory.

1. Linux is case sensetive
2. Have you spelled it correctly?
3. Are you in the directory that folder is in?

Sorry, I do wrong.. But... why last time I can use this command to delete an 'undelete-able folder'? Weird.. When I tried second time, it failed working. :(

---

### Post by nothingspecial on 2011-09-01
It depends what you tried to delete. Recently Ubuntu has included a guard against deleting something you shouldn't.

You should be very very careful with that command. A typo such as a space in the wrong place and bang, no more system.

---

### Post by pretty_whistle on 2011-09-01
> **tingxyu1996 said:**
> try:
sudo rm -rf <folder name>

I just tried that and in the terminal it appears to have worked but when I go look the folder's still there anyway.

---

### Post by bab1 on 2011-09-01
> **nothingspecial said:**
> ...Recently Ubuntu has included a guard against deleting something you shouldn't.
What is this ***guard*** that Ubuntu added?  Can your describe this feature a little more or point to a reference to read about this?

---

### Post by pretty_whistle on 2011-09-01
> **haqking said:**
> I am assuming this is pertaining to your earlier thread ?

[http://ubuntuforums.org/showthread.php?t=1837057](http://ubuntuforums.org/showthread.php?t=1837057)

try not to multipost, keep it altogether as it is same subject.

use tab completion to complete the filename.

or delete it from within nautilus
Yes it's connected to that other thread, sorry about that.

Delete it from within nautilus?  What's that?

---

### Post by nothingspecial on 2011-09-01
It only prevents you from removing everything.

A few years back some people thought it would be fun to help people on ubuntuforums by telling them to run a command that does that.

I've only read that that command no longer works. I'm not trying it and finding out I'm wrong.

The command in question is in the stickies. I don't think you are permitted to post it.

---

### Post by nothingspecial on 2011-09-01
> **pretty_whistle said:**
> Yes it's connected to that other thread, sorry about that.

Delete it from within nautilus?  What's that?

It's the file browser. But if you do that you won't learn what you are doing wrong.

Where is the folder?

---

### Post by haqking on 2011-09-01
> **nothingspecial said:**
> It's the file browser. But if you do that you won't learn what you are doing wrong.

Where is the folder?

that is true, just saying if he really needs it gone and doesnt get it solved.

But yes make sure you are in correct location in terminal and use tab completion to make sure you get the filename correct.

---

### Post by pretty_whistle on 2011-09-01
I deleted it finally using:

> gksudo nautilus

---

### Post by sanderd17 on 2011-09-01
> **haqking said:**
> 

as for the command we are not allowed to mention, no it doesnt work anymore ;-)

So even not with the -f option?

---

### Post by nothingspecial on 2011-09-01
> **sanderd17 said:**
> So even not with the -f option?

Don't think so. Again, I'm not trying it.

---

### Post by haqking on 2011-09-01
> **sanderd17 said:**
> So even not with the -f option?

well i tried it recently on a VM and no it did nothing unless i used sudo.

---

### Post by nothingspecial on 2011-09-01
> **haqking said:**
> well i tried it recently on a VM and no it did nothing unless i used sudo.

Well it wouldn't anyway.

I heard that it now doesn't work at all.

Let me boot my oneiric a minute and see.

---

### Post by sanderd17 on 2011-09-01
> **haqking said:**
> well i tried it recently on a VM and no it did nothing unless i used sudo.

Without sudo it won't work, that's natural.

I'm not gonna try it either. I'm now on Arch, and I don't think Arch would give such kind of protection against yourself.

---

### Post by haqking on 2011-09-01
[QUOTE=sanderd17;11209016]Without sudo it won't work, that's natural.

edited due to off topic and probably on the border of COC infringement ;)

---

### Post by nothingspecial on 2011-09-01
> **haqking said:**
> no the point was, it used to be able to be carried out without sudo.  Allowing it with sudo is correct as it assumes the admin knows what they are doing.

it still works with * etc but not /

anyways off topic ;-)

No it didn't used to work without sudo.

Anyway, in oneiric at least it doesn't work but it tells you how to overide it (which is good because I might want to).

No I wouldn't try it with Arch.

And yes, this has gone offtopic.

---

### Post by haqking on 2011-09-01
> **nothingspecial said:**
> No it didn't used to work without sudo.

Anyway, in oneiric at least it doesn't work but it tells you how to overide it (which is good because I might want to).

No I wouldn't try it with Arch.

And yes, this has gone offtopic.

we have crossed wires i think.

which is what my miscommunication meant, i was trying to avoid entering the commands ;-)

anyways i PM you

---

### Post by bab1 on 2011-09-01
> **nothingspecial said:**
> Well it wouldn't anyway.

I heard that it now doesn't work at all.

Let me boot my oneiric a minute and see.

The command works as it always has.  Sudo (or the lack thereof) is your friend here.  The tool is not the danger here; the users inexperience is.

Edit:> Anyway, in oneiric at least it doesn't work but it tells you how to overide it (which is good because I might want to).

This is new.  I shall have to look at that.

---

### Post by haqking on 2011-09-01
> **bab1 said:**
> The command works as it always has.  Sudo (or the lack thereof) is your friend here.  The tool is not the danger here; the users inexperience is.

ha still of topic though, i have been in PM with nothingspecial about this instead.

---

### Post by sisco311 on 2011-09-01
--preserve-root option has been the default since version 6.4 of GNU Core Utilities (2006).

See: [http://en.wikipedia.org/wiki/Rm_(Unix)#Protection_of_.2F](http://en.wikipedia.org/wiki/Rm_(Unix)#Protection_of_.2F)

@sanderd17
Arch uses GNU coreutils too. ;)

---

