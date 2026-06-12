---
title: "Skype keeps closing"
date: 2011-05-29
forum: General Help
---

### Post by mitk0o0o0 on 2011-05-29
Hello, for the past 3 days skype has been giving me problems for some reason

I start it, the sign in screen shows up and like 5 seconds later it closes, i check if the process is still running but it's not so it just shuts down.

I've tried uninstalling it from synaptic package manager, then installing it again and it's still doing me this.

Has anyone else dealt with this before?

---

### Post by mitk0o0o0 on 2011-05-29
bump

---

### Post by RichardCain on 2011-05-29
I've got exactly the same problem. uninstalled and re-installed; still the same.

update: I tried running it in a terminal, it just returned "Aborted" and went back to the prompt.

---

### Post by mitk0o0o0 on 2011-05-29
Skype epidemic these days :P

A friend's skype was causing the computer to freeze
Neighbour's skype as causing her computer to shutdown for some reason when making calls..

and in ubuntu this, wow.. :s

---

### Post by RichardCain on 2011-05-29
Just found this on another thread:

SIMPLE FIX:

Go to your home folder
Code:

cd ~/

Turn on hidden files and folders

Navigate to the folder ./Skype

Open it and delete the file shared.xml

You will have to reconfigure skype, but you will be able to use the service again.

Works for me.

---

### Post by mitk0o0o0 on 2011-05-29
> **RichardCain said:**
> Just found this on another thread:

SIMPLE FIX:

Go to your home folder
Code:

cd ~/

Turn on hidden files and folders

Navigate to the folder ./Skype

Open it and delete the file shared.xml

You will have to reconfigure skype, but you will be able to use the service again.

Works for me.Worked.

Thank you so much! :D

---

### Post by sostentado on 2011-06-11
i have the same problem too...
the older beta version of skype is 2.2.25-1 and the newest is 2.2.35-1, think you might want to download rather than deleting any files on skype folder.

---

### Post by richard.scott-ettrick on 2012-03-19
This only works once! You then need to do it again each time you start skype.
> **RichardCain said:**
> Just found this on another thread:

SIMPLE FIX:

Go to your home folder
Code:

cd ~/

Turn on hidden files and folders

Navigate to the folder ./Skype

Open it and delete the file shared.xml

You will have to reconfigure skype, but you will be able to use the service again.

Works for me.

---

### Post by RichardCain on 2012-03-19
That does seem strange.  A few questions for you:

How many times has this happened?

Did you do anything inbetween, such as restoring from a back-up?

Are you still using Lucid?

How did you install Skype, from a download or through the repository?
If it was from a download, what version are you running?

Anything to help a fellow Borderer ;-)

---

### Post by richard.scott-ettrick on 2012-04-14
I am using Ubuntu 11.10. Skype 2.2 Beta. I seem to remember downloding it from the repositry. Not even working when I remove the .xml file now.

---

### Post by RichardCain on 2012-04-14
It looks like some setting has got messed up somewhere along the line.  I can only suggest starting from scratch.

In a terminal, type:
```
sudo apt-get purge skype
```

Then, just to make doubly sure:
```
cd ~

sudo rm -R .Skype
```

Open Software Sources and, on the "Other Software" tab, make sure that the "Canonical Partners" boxes are both ticked.  Then just:
```
sudo apt-get update

sudo apt-get install skype
```

or you can go and re-install Skype from the Software Centre.

Let me know how you get on.

---

### Post by richard.scott-ettrick on 2012-04-15
Thankyou. It appears to be working at the moment. I will keep an eye on it and see if it keeps on behaving itself. Richard.

---

### Post by Ronan1971 on 2012-05-22
I used to have the same problem with previous versions but it totally disappeared since I upgraded to 12-04. Looks like they finally fixed the glitch (about time...).

---

