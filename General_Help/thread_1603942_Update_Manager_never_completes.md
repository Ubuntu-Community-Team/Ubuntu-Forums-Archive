---
title: "Update Manager never completes"
date: 2010-10-23
forum: General Help
---

### Post by XEtedBear on 2010-10-23
I'm running Update Manager on a newly installed 10.10. It tells me thjere are 54 important security updates. I have chosen the option to install them. I get a window 'Applying Changes' with the message 'waiitng for apt-get to exit'. I've been waitng a week. Does it normally take this long, or it it perhaps a 6 month oparation synchronised to each Ubuntu update?

---

### Post by alexandari on 2010-10-23
in the terminal

```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

### Post by XEtedBear on 2010-10-23
> **alexandari said:**
> in the terminal

```
sudo aptitude update
```
```
sudo aptitude upgrade
```

"sudo: aptitude: command not found"

---

### Post by ivanovnegro on 2010-10-23
> **XEtedBear said:**
> I'm running Update Manager on a newly installed 10.10. It tells me thjere are 54 important security updates. I have chosen the option to install them. I get a window 'Applying Changes' with the message 'waiitng for apt-get to exit'. I've been waitng a week. Does it normally take this long, or it it perhaps a 6 month oparation synchronised to each Ubuntu update?

No it doese not take as long normally.
Seems that something is wrong with apt-get. Have you got any error message in the terminal?
Be sure to not use Synaptic or other package manager at the same time.
Ah, [here]("http://ubuntuforums.org/showthread.php?p=10001123") I found this. Maybe it helps.
Let me know if you solved your problem.

---

### Post by rnealg on 2010-10-23
Same here. It's very annoying not knowing if it's loading updates or it's just sitting there doing nothing!

---

### Post by XEtedBear on 2010-10-23
> **ivanovnegro said:**
> No it doese not take as long normally.
Seems that something is wrong with apt-get. Have you got any error message in the terminal?
Be sure to not use Synaptic or other package manager at the same time.
Ah, [here]("http://ubuntuforums.org/showthread.php?p=10001123") I found this. Maybe it helps.
Let me know if you solved your problem.

It describes the same problem that I am having (cannot get a lock on some file or other totally outside my understanding) 
but doesn't prescribe a solution.

---

### Post by ivanovnegro on 2010-10-23
> **XEtedBear said:**
> It describes the same problem that I am having (cannot get a lock on some file or other totally outside my understanding) 
but doesn't prescribe a solution.

Ok, try this in the terminal and then update again.
```
dpkg-reconfigure apt
```
Maybe it helps.

---

### Post by Sef on 2010-10-23
> Quote:
Originally Posted by alexandari  
in the terminal

Code:
sudo aptitude update
Code:
sudo aptitude upgrade
"sudo: aptitude: command not found"

Instead use these commands:

```
sudo apt-get update && sudo apt-get upgrade
```

Aptitude was removed from 10.10.  That is why you were getting that message.

---

### Post by XEtedBear on 2010-10-23
> **ivanovnegro said:**
> Ok, try this in the terminal and then update again.
```
dpkg-reconfigure apt
```
Maybe it helps.

Result: No changes (i.e. keys not changed)

But after a restart, updating seems to be working as one would expect (not complete yet, as over 100 MB to process)

Thanks for guidance.

---

### Post by ivanovnegro on 2010-10-23
> **Sef said:**
> Instead use these commands:

```
sudo apt-get update && sudo apt-get upgrade
```

Aptitude was removed from 10.10.  That is why you were getting that message.

Oh, yes thats right, aptitude was removed I forgot that, Im on Arch, I used the old commands and on Mint there is aptitude.

> **XEtedBear said:**
> Result: No changes (i.e. keys not changed)

But after a restart, updating seems to be working as one would expect (not complete yet, as over 100 MB to process)

Thanks for guidance.

Great that it worked after a restart, that would be my next suggestion, a restart normally can solve many things.

---

