---
title: "Question about version 6.10"
date: 2009-08-26
forum: General Help
---

### Post by KunoNoOni on 2009-08-26
I have 6.10 installed and really haven't need to anything more. Recently I needed to install some packages and have come to find out that I can't download anything using apt-get.


So my question is what do I do now? I need to install the python-dev package.

Appreciate your time!

-KunoNoOni

---

### Post by snowpine on 2009-08-26
Hi KunoNoOni, each Ubuntu release (except for LTS like 8.04) is supported for 18 months. So, support for 6.10 (released October 2006) ended in April 2008, over a year ago. This means there will be no more updates (including important security patches) and the repositories are closed. I highly recommend a fresh install of the current release, 9.04 (which will be supported through Oct. 2010).

If you really want to keep using 6.10 (*highly unrecommended*) what you need to do is edit your /etc/apt/sources.list file and change all of the URLs to "old-releases." For example, change: 

```
deb http://us.archive.ubuntu.com/ubuntu edgy main restricted
```

to:

```
deb http://old-releases.ubuntu.com/ubuntu edgy main restricted
```

But again, I strongly recommend bringing your system up to date.

---

### Post by michy99 on 2009-08-26
Since 6.10 is no longer supported, the repositories have been moved. If you really don't want to upgrade to a current version, you need to edit /etc/apt/sources.list to use the repositories at [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com).

EDIT: While I typing this, snowpine already said the same thing. I would add the versions of software in the old repositories will be at least three years old.

---

### Post by KunoNoOni on 2009-08-26
Thanks for the replies! :)

I will have to look into what I would need to do to update. From what I was told in the past I would need to do a fresh install. But I have a lot of files that I would need to backup before I did this. right now I'm not ready to do this. Need to sit down and actually see which files I need to save. 

Again thanks for the help :)


-KunoNoOni

---

### Post by snowpine on 2009-08-26
What I would recommend, if you have enough space on the hard drive, is to set up a dual boot between 6.10 and 9.04. You could then copy the files and settings over at your leisure, or fall back on 6.10 temporarily if you needed to. Just a suggestions...

---

