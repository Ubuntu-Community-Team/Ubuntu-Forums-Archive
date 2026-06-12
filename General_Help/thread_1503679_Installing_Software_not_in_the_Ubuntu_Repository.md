---
title: "Installing Software not in the Ubuntu Repository"
date: 2010-06-07
forum: General Help
---

### Post by COKEDUDE on 2010-06-07
What is the recommended method for Installing Software not in the Ubuntu Repository? I currently want dos2unix. I discovered from wiki that that dos2unix is supposed to be in the "tofrodos package". So then I checked the ubuntu repository. 
[http://en.wikipedia.org/wiki/Unix2dos](http://en.wikipedia.org/wiki/Unix2dos)
[http://packages.ubuntu.com/lucid/tofrodos](http://packages.ubuntu.com/lucid/tofrodos)

Then I did the usual "sudo apt-get install tofrodos". After I did this I discovered that for some unknown reason ubuntu removed dos2unix from the tofrodos package. How would you recommend that I get dos2unix now? Is there a way to use "sudo apt-get install tofrodos" with a repository name to use a different repository? I saw it was in the debian repository and I know ubuntu is based on debian. Could I use something like "sudo apt-get install tofrodos debian". Should I just go directly to the author's website and download it there?

---

### Post by dino99 on 2010-06-07
from your second link:

***  Tofrodos comprises one program, "fromdos" alias "todos", which converts text files to and from these formats. [COLOR="Red"]Use "fromdos" to convert DOS text files to the Unix format[/COLOR], [COLOR="Blue"]and "todos" to convert Unix text files to the DOS format[/COLOR]. ****

so where is the problem ? renaming fonction ?

---

### Post by dcstar on 2010-06-07
> **COKEDUDE said:**
> What is the recommended method for Installing Software not in the Ubuntu Repository? I currently want dos2unix. I discovered from wiki that that dos2unix is supposed to be in the "tofrodos package". So then I checked the ubuntu repository. 
[http://en.wikipedia.org/wiki/Unix2dos](http://en.wikipedia.org/wiki/Unix2dos)
[http://packages.ubuntu.com/lucid/tofrodos](http://packages.ubuntu.com/lucid/tofrodos)

Then I did the usual "sudo apt-get install tofrodos". After I did this I discovered that for some unknown reason ubuntu removed dos2unix from the tofrodos package. How would you recommend that I get dos2unix now? Is there a way to use "sudo apt-get install tofrodos" with a repository name to use a different repository? I saw it was in the debian repository and I know ubuntu is based on debian. Could I use something like "sudo apt-get install tofrodos debian". Should I just go directly to the author's website and download it there?

Read the man page, there are two functions in the package that do the job, they are just called something else.

---

### Post by COKEDUDE on 2010-06-07
The problem is I want dos2unix. dos2unix can do stuff the other program can't do. So how would I use the debian repository?

---

### Post by COKEDUDE on 2010-06-07
I'm pretty sure that I should be able to install deb files. I found them in the debian repository. Could someone please tell me how to install them? 

[http://packages.debian.org/squeeze/dos2unix](http://packages.debian.org/squeeze/dos2unix)
[http://packages.debian.org/squeeze/i386/dos2unix/download](http://packages.debian.org/squeeze/i386/dos2unix/download)

---

### Post by SlidingHorn on 2010-06-07
> **COKEDUDE said:**
> I'm pretty sure that I should be able to install deb files. I found them in the debian repository. Could someone please tell me how to install them? 

[http://packages.debian.org/squeeze/dos2unix](http://packages.debian.org/squeeze/dos2unix)
[http://packages.debian.org/squeeze/i386/dos2unix/download](http://packages.debian.org/squeeze/i386/dos2unix/download)

.deb files can simply be double-clicked...a package installer will open asking if you want to install.  Click yes (or whatever is the "affirmative") and you're golden

---

### Post by COKEDUDE on 2010-06-08
> **SlidingHorn said:**
> .deb files can simply be double-clicked...a package installer will open asking if you want to install.  Click yes (or whatever is the "affirmative") and you're golden

Wow that was quite easy. Looks like I was overthinking it a bit.

---

