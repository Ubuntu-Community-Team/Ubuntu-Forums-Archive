---
title: "Please Help!"
date: 2011-01-23
forum: General Help
---

### Post by Zethioth on 2011-01-23
While trying to install Wine via Ubuntu Software Center my laptop batter died. I am now getting the "Previous installation has not been completed" error. I can't install anything!

I've tried:

```
sudo dpkg --configure -a
```

It gives me this:

```
dpkg: parse error, in file '/var/lib/dpkg/updates/0017' near line 0:
 newline in field name `#padding'
```

-------------------------------------------------------------------------------------------------------

I've also tried:

```
sudo apt-get install -f
```

but it gives me this:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' 
to correct the problem.
```

----------------------------------------------------------------------------------------------------------------------------------

How can I possible run that if it doesn't work? Someone please help me resolve this issue!

---

### Post by derklempner on 2011-01-23
Have you attempted to remove the package and then reinstall it?
```
sudo apt-get remove --purge wine
```

---

### Post by Zethioth on 2011-01-23
No, I am new to Ubuntu. I tried the command but still I get this:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

---

### Post by derklempner on 2011-01-23
Check to see if there are any files in **/var/lib/dpkg/updates**.  If there are files in that directory, delete them all then run:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install wine
```

---

### Post by Zethioth on 2011-01-23
That is odd. I cannot delete them no matter what I try. Aren't hey important system files?

---

### Post by derklempner on 2011-01-23
> **Zethioth said:**
> That is odd. I cannot delete them no matter what I try. Aren't hey important system files?
The reason you can't delete them is probably because you're using the file browser (Nautilus) to navigate into that directory and delete them there.

What you need to do is open a command prompt and do this:
```
cd /var/lib/dpkg/updates
sudo rm -rf ./*
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install wine
```

---

### Post by Zethioth on 2011-01-23
By command prompt, you mean Terminal correct?

---

### Post by derklempner on 2011-01-23
> **Zethioth said:**
> By command prompt, you mean Terminal correct?
Yes, terminal is just the program that replicates a command prompt in the GUI (i.e., GNOME or KDE).

---

### Post by Zethioth on 2011-01-23
Okay, cool. It is doing its magic as I type.

---

### Post by derklempner on 2011-01-23
Make sure you change the name of this thread to "[SOLVED]" if it fixes your problem.

---

### Post by Zethioth on 2011-01-23
[derklempner]("http://ubuntuforums.org/member.php?u=86164"), you are an amazing guy. Thank you for resolving this issue. Perhaps in the future they can make a much simpler solution for issues like this?

I hope to join in on Linux development but I am only 16 and haven't had a chance to work in a Computer science major. :(

---

### Post by derklempner on 2011-01-23
> **Zethioth said:**
> [derklempner]("http://ubuntuforums.org/member.php?u=86164"), you are an amazing guy. Thank you for resolving this issue. Perhaps in the future they can make a much simpler solution for issues like this?

I hope to join in on Linux development but I am only 16 and haven't had a chance to work in a Computer science major. :(
I'm glad I could help.  It's simply a matter of Googling the error message and finding the correct resolution.  Try to do a bit of research on your own before posting here, and you'll be surprised at how much new information you can find.

And don't forget this: [http://xkcd.com/627/](http://xkcd.com/627/)

---

### Post by Zethioth on 2011-01-23
Well, I did an hours worth of Googling. In my first post I wrote what I tried. I also had another thread that was dead. When you title your thread "Please Help!", you seem to get a lot more attention.

[http://ubuntuforums.org/showthread.php?t=1673690](http://ubuntuforums.org/showthread.php?t=1673690)

---

### Post by ubudog on 2011-01-23
> **derklempner said:**
> Make sure you change the name of this thread to "[SOLVED]" if it fixes your problem.

Thanks!  After all these years, I still hadn't found the solution.

---

### Post by derklempner on 2011-01-24
> **ubudog said:**
> Thanks!  After all these years, I still hadn't found the solution.
LOL, I hope that was sarcasm at its finest...

---

### Post by ubudog on 2011-01-24
> **derklempner said:**
> LOL, I hope that was sarcasm at its finest...

No, seriously.

:lolflag:

---

### Post by derklempner on 2011-01-24
> **ubudog said:**
> No, seriously.
Were you referring to the problem I helped him with, or the changing of the thread name to [SOLVED]?

---

### Post by Zethioth on 2011-01-24
I have no idea what he is talking about. I am extremely confused.

---

### Post by ubudog on 2011-01-24
> **derklempner said:**
> Were you referring to the problem I helped him with, or the changing of the thread name to [SOLVED]?

Dude, I'm just saying thanks, because your answer also helped me.  :)

---

