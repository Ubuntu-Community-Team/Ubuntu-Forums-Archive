---
title: "text file 3 million url into chunks of 5,000?"
date: 2010-12-16
forum: General Help
---

### Post by webcabbie on 2010-12-16
I have a text file with 3 million urls that I want split into chunks of 5,000. 

Anyone have idiot proof simple instructions to accomplish this in the command line?

---

### Post by Habeouscorpus on 2010-12-16
No fix, but... How in the name of all that is holy did you get 3 million urls?

But to do this, you'd have to use a highly specialized terminal based editor, like emacs or vi.

---

### Post by TiBaal89 on 2010-12-16
Check out the 'split' command... no joke.  :lol:

---

### Post by webcabbie on 2010-12-16
Ya I am trying to figure it out now and not having luck I`m trying 
split -l 5000 Desktop/Dupefree.txt and not getting a result? Any thoughts?

---

### Post by webcabbie on 2010-12-16
GRRRR... not having any luck PLEASE HELP!

---

### Post by TiBaal89 on 2010-12-16
What happens when you try to run split?

---

### Post by webcabbie on 2010-12-16
cat Desktop/urlfolder/* |split-l 5000 > Desktop/Dupefree.txt
split-l: command not found

so the file is in a folder on the desktop called urlfolderon my desktop and I want the resulting files to wind up on the desktop or in the urlfile.

Have I mentioned this is maybe my 3rd or 4th attempt at command line functions?

---

### Post by matt_symes on 2010-12-16
Hi

```
cat Desktop/urlfolder/* |split-l 5000 > Desktop/Dupefree.txt
```Add a space between split and -l and change to

```
split -l 5000 Desktop/Dupefree.txt
```

Look for a load of files called xaa, xab, xac etc

Kind regards

---

### Post by tgalati4 on 2010-12-16
The following is not specific:

split -l 5000 Desktop/Dupefree.txt

How about:

split -l 5000 ~/Desktop/Dupefree.txt

~/ is a placeholder for /home/webcabbie

---

### Post by TiBaal89 on 2010-12-16
> **webcabbie said:**
> cat Desktop/urlfolder/* |split-l 5000 > Desktop/Dupefree.txt

Ah, a few things going on there....

- No need for the 'cat' and the pipe...you should just run split itself. 
- There needs to be a space between the command (split) and the switch (-l).  
- split outputs to files, so there's nothing to redirect with '>'

My advice - use a smaller example to understand what you're doing.  Make a text file on your desktop called blahblah.txt and fill it with 10 lines of garbage.  'cd' to the desktop and run

```
split -l 2 blahblah.txt
```

5 files should appear on your desktop with funny names, each containing 2 lines of blahblah.

Also... with 3M files and 5K lines in each, you're going to get 600 files when you eventually run this full scale.  I recommend doing it someplace other than the desktop!

---

### Post by matt_symes on 2010-12-16
Hi

If you are in your home directory when you run the command

split -l 5000 Desktop/blah.txt

the split files will appear in your home directory and not on the desktop. I.e the directory you run the split command from.

Look for xaa, xab, xac

Kind regards

---

### Post by webcabbie on 2010-12-16
Ran this 

$ split -l 5000 ~/Desktop/Dupefree.txt

Processor jumped a bit than nothing. Nothing at all happened.

---

### Post by webcabbie on 2010-12-16
Yuppers..

found them in my home folder.. WOOPIE!

---

### Post by sgosnell on 2010-12-16
And I'll bet you found LOTS of them!

---

