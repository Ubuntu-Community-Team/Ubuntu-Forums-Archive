---
title: "Questions about purge"
date: 2012-05-24
forum: General Help
---

### Post by charleswb on 2012-05-24
What is difference between:[INDENT]apt-get **purge** brasero

[/INDENT]versus[INDENT]apt-get **remove -purge** brasero

[/INDENT]I used brasero for sake of example, but it could be any program being removed.

I have been using: apt-get **purge** brasero
It seemed to work.

I just read in a book that I should use: apt-get** remove -purge **brasero

Is there a difference in what they do? If so, what is the difference?

---

### Post by wilee-nilee on 2012-05-24
> **charleswb said:**
> What is difference between:[INDENT]apt-get **purge** brasero

[/INDENT]versus[INDENT]apt-get **remove -purge** brasero

[/INDENT]I used brasero for sake of example, but it could be any program being removed.

I have been using: apt-get **purge** brasero
It seemed to work.

I just read in a book that I should use: apt-get** remove -purge **brasero

Is there a difference in what they do? If so, what is the difference?

Purge removes everything including the brasero in .config , remove leaves the brasero in .config.

Running purge and remove together is incorrect it is one or the other.

---

### Post by eleftg on 2012-05-24
I don't think there is any difference. I always use

```
apt-get purge <packagename>
``` and it works as expected.

The only useful thing about --purge is when cleaning up packages:

```
apt-get autoremove --purge
```

---

### Post by charleswb on 2012-05-24
> **wilee-nilee said:**
> Purge removes everything including the brasero in .config , remove leaves the brasero in .config.

Running purge and remove together is incorrect it is one or the other.

My Ubuntu Unleashed book has this example of using purge:[INDENT]apt-get remove --purge firefox


[/INDENT]So they are showing to use them together. I'll test that on some piece of software I don't need. Just to see what happens.

---

### Post by wilee-nilee on 2012-05-24
> **charleswb said:**
> My Ubuntu Unleashed book has this example of using purge:[INDENT]apt-get remove -purge firefox
[/INDENT]So they are showing to use them together. Maybe I'll test that on some piece of software I don't need. Just to see what happens.

How old is the book I have never used them together, could this be a context issue?

---

### Post by charleswb on 2012-05-24
> **wilee-nilee said:**
> How old is the book I have never used them together, could this be a context issue?

Published in 2011 by SAMS. Book is Ubuntu Unleashed - Covering U10.04 and U11.04.

I am using U11.04.

I don't think it's a context issue.

---

### Post by wilee-nilee on 2012-05-24
> **charleswb said:**
> Published in 2011 by SAMS. Book is Ubuntu Unleashed - Covering U10.04 and U11.04.

I am using U11.04.

I don't think it's a context issue.

Seems to be just extra commands really, I run if I want just a removal.

```
sudo apt-get remove "package"
```I want it gone completely.

```
sudo apt-get purge "package"
```If purge is in there it will be all gone whether the remove is there or not I suspect.

Are you running in root rather then using sudo as well?

---

### Post by josephmills on 2012-05-24
```
man apt-get 
```


Usage: apt-get [options] command

so would that not be 
```
sudo apt-get --purge remove ex-wife-from-life
```

? just saying

---

### Post by eleftg on 2012-05-24
I agree with wilee-nilee

---

### Post by josephmills on 2012-05-24
```
man apt-get 
```


Usage: apt-get [options] command

so would that not be 
```
sudo apt-get --purge remove ex-wife-from-life
```

? just saying  (I know that purge is also a command )

---

### Post by wilee-nilee on 2012-05-24
> **josephmills said:**
> ```
man apt-get 
```Usage: apt-get [options] command

so would that not be 
```
sudo apt-get --purge remove ex-wife-from-life
```? just saying

:lolflag:

About the ex-wife, good idea with the man, to.

---

### Post by charleswb on 2012-05-29
> **josephmills said:**
> ```
man apt-get 
```
Usage: apt-get [options] command

so would that not be 
```
sudo apt-get --purge remove ex-wife-from-life
```? just saying  (I know that purge is also a command )

Tech support mixed with humor. I love it.

---

### Post by sgage on 2012-05-29
> **wilee-nilee said:**
> Purge removes everything including the brasero in .config , remove leaves the brasero in .config.

Running purge and remove together is incorrect it is one or the other.

However, purge does not remove userland .config entries - just system-wide config. If you want to remove ~/.config/brasero you need to that yourself manually.

---

