---
title: "More books like this?"
date: 2011-03-16
forum: General Help
---

### Post by alphaamanitin on 2011-03-16
Hey guys,

Does anyone know other good sources of general books like this one:

> **TeoBigusGeekus said:**
> Very good [book]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") on bash.

Flash on linux is a sad story, you're not the only one suffering.

Can't help you with the touch pad.



I put it on my nook and have been reading it.  It has been very helpful, and more than just linux.  Reading it I finally realised what the Windows "shortcuts" are.  I mean I knew what they were, but I didn't really *know* what they were, symbolic link files.  At least, I think that is correct.  Anyway, the book has bee good so far.  Does anyone know where I can get books like it covering things in Ubuntu and/or Linux in general?  By like it I mean, good, in digital format, and legally free.

Thanks,

AlphaA

---

### Post by ant2ne on 2011-03-16
> **alphaamanitin said:**
> Reading it I finally realised what the Windows "shortcuts" are.  I mean I knew what they were, but I didn't really *know* what they were, symbolic link files.  At least, I think that is correct.No windows short cuts are very different from linux symbolic links.

---

### Post by alphaamanitin on 2011-03-16
Really?  It sounded like what Windows would be doing in spirit.  Crap, now I am sad.  Oh well, now I know.  Better to be corrected than to continue with being wrong and not understanding.  Also, wouldn't it be simpler to do something like symbolic links?

AlphaA

---

### Post by ant2ne on 2011-03-17
A MS Shortcut is just a pointer to launch an application or other file. It just points. A unix link treats that file just like the original.

---

### Post by alphaamanitin on 2011-03-17
I thought that is what symbolic links basically are, a special file type that contains a reference to another file.  Not claiming it is right, but that is what wikipedia says a symbolic link is as well.  What do you mean by "Unix link"?  Anyway, I figured that Shortcuts were not strictly speaking symbolic links, but in spirit were of the same nature.  A file that references another file.

AlphaA

---

### Post by Grenage on 2011-03-17
There are different kinds of links, and I believe that these days, MS also has symlinks (Vista+)

---

### Post by Matt__ on 2011-03-17
there are a couple of bash pdfs available for free.(also in html or plain text)

_[Bash Beginners Guide]("http://www.tldp.org/LDP/Win+OpenSolaris+CentOS-Install/Win+OpenSolaris+CentOS-Install.pdf")_[U]

[Advanced Bash-Scripting Guide]("http://www.tldp.org/LDP/abs/abs-guide.pdf")[/U]

both taken from [Linux Documentation Project Guides]("http://www.tldp.org/guides.html") where you should find lots of usueful info.

or even [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

and this post [http://ubuntuforums.org/showthread.php?p=5005069#post5005069](http://ubuntuforums.org/showthread.php?p=5005069#post5005069)

---

### Post by ant2ne on 2011-03-17
> **alphaamanitin said:**
> I thought that is what symbolic links basically are, a special file type that contains a reference to another file.  Not claiming it is right, but that is what wikipedia says a symbolic link is as well.  What do you mean by "Unix link"?  Anyway, I figured that Shortcuts were not strictly speaking symbolic links, but in spirit were of the same nature.  A file that references another file.

AlphaA
create a file called test in /tmp then link it to your home then pipe data into the link and it shows up in tmp.
```

touch /tmp/test
ln -s /home/mylink /tmp/myfile
echo "data" > /home/mylink
cat /tmp/myfile
```
you can't do that with a MS shortcut. If you did create a shortcut and pipe something into it, it breaks your shortcut. At least in XP.

---

### Post by alphaamanitin on 2011-03-17
> **Matt__ said:**
> there are a couple of bash pdfs available for free.(also in html or plain text)

_[Bash Beginners Guide]("http://www.tldp.org/LDP/Win+OpenSolaris+CentOS-Install/Win+OpenSolaris+CentOS-Install.pdf")_[U]

[Advanced Bash-Scripting Guide]("http://www.tldp.org/LDP/abs/abs-guide.pdf")[/U]

both taken from [Linux Documentation Project Guides]("http://www.tldp.org/guides.html") where you should find lots of usueful info.

or even [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

and this post [http://ubuntuforums.org/showthread.php?p=5005069#post5005069](http://ubuntuforums.org/showthread.php?p=5005069#post5005069)

Great, just what I was looking for.  

@ant2ne-I read some about MS shortcuts and there are some key differences.  But at least my basic understanding of them was correct, thought in the end wrong.  

@Grenage-Yes from what I have just read, Vista and above use symbolic links, but there are some differences there as well I guess.

AlphaA

---

### Post by ant2ne on 2011-03-17
> **alphaamanitin said:**
> @ant2ne-I read some about MS shortcuts and there are some key differences.  But at least my basic understanding of them was correct, thought in the end wrong.   Yeah you are on the right track i guess.

---

