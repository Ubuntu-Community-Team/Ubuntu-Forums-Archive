---
title: "libstdc++.so.6 installed but not found"
date: 2010-03-09
forum: General Help
---

### Post by afrodeity on 2010-03-09
I downloading a programme last night which required libstdc++.so.5 and libstdc++.so.5.0.1 i.e Jaunty libraries, then copied the two files to /usr/lib/ thinking this would be fine. [Here is a [posting]("http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/") on the proper way to go about doing this, and [another]("http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000")]

My system immediately got upset and started complaining. Now I can't run anything. Apt-Get is broken, Aptitude can't run. It looks like a versioning crisis:

 
```

/usr/lib/libstdc++.so.6: version 'GLIBCXX_3.4.9' not found (required by apt-get)

 /usr/lib/libstdc++.so.6: version 'GXXABI_1.3' not found (required by apt-get)

 /usr/lib/libstdc++.so.6: version 'GLIBCXX_3.4.11' not found (required by apt-get)

 libstdc++.so.6: version 'GLIBCXX_3.4' not found (required by apt-get)

 libstdc++.so.6: version 'GLIBCXX_3.4.11' not found (required by /usr/lib/libapt-pkg-libc6.10-6.so.4.8)

 libstdc++.so.6: version 'CXXABI_1.3' not found (required by /usr/lib/libapt-pkg-libc6.10-6.so.4.8)

 libstdc++.so.6: version 'GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-pkg-libc6.10-6.so.4.8)

 libstdc++.so.6: version 'GLIBCXX_3.4' not found (required by /usr/lib/libapt-pkg-libc6.10-6.so.4.8)


```

If i do a locate for libstdc++.so.6 it appears where it was, /usr/lib/libstdc++.so.6

I've found two postings which very are similar but not the exact problem:

[http://ubuntuforums.org/showthread.php?t=808045](http://ubuntuforums.org/showthread.php?t=808045)

[http://ubuntuforums.org/showthread.php?t=1282957](http://ubuntuforums.org/showthread.php?t=1282957)

Need somebody to talk me through this crisis, because I don't understand what I've done wrong.

---

### Post by afrodeity on 2010-03-09
tried sudo updatedb but to no avail, I do not understand why this is happening, and what exactly is wrong with the database.

---

### Post by afrodeity on 2010-03-09
The only thing which seems to be working is dpkg but no man page.

---

### Post by afrodeity on 2010-03-09
Well, this is a clue: my system GCC version is 4.4.1

Installing [http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.4/libstdc++6_4.4.1-4ubuntu9_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.4/libstdc++6_4.4.1-4ubuntu9_i386.deb) did it for me, thanks for being there, I guess, just the idea that somebody else did it too.

---

### Post by afrodeity on 2010-03-09
Here the two links which helped the most:

[http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000)

[http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/#comment-145](http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/#comment-145)

---

### Post by hsmak_linux on 2010-03-10
Hi afrodeity,

You already had my reply at my blog, and thank you very much for seeking my help.

Just a quick explanation based on my guess about this problem:
It appears from the error msg you posted in the above that your libstdc++6 was corrupted by somehow!
> **afrodeity said:**
> Well, this is a clue: my system GCC version is 4.4.1

Installing [http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.4/libstdc++6_4.4.1-4ubuntu9_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.4/libstdc++6_4.4.1-4ubuntu9_i386.deb) did it for me, thanks for being there, I guess, just the idea that somebody else did it too.
So, Installing the libstdc++6 library again, as you did, must have solved the problem.


> **afrodeity said:**
> Here the two links which helped the most:

[http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000)

[http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/#comment-145](http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/#comment-145)
Thanks for linking to my blog.
It would always be my pleasure to help.

Good luck!

---

### Post by afrodeity on 2010-03-10
Thanks Husain,

The corruption occurred because I didn't install libstdc++.so.5 via a package manager. Result was some form of weirdness in the package manager database which effected the overall functioning system. Exactly why adding something to a folder should change anything at all is a good question. I don't know why this happens, unless the folder is hot i.e symbolically linked to a programme which doesn't have any tolerance for hacks like simply copying a file into the folder. Which begs another question - which folders in Ubuntu are hot, and how can we tell, and isn't there a better way of visualising the system?

Wish I knew more about how Ubuntu actually works.

---

### Post by hsmak_linux on 2010-03-10
> **afrodeity said:**
> ...Wish I knew more about how Ubuntu actually works.

Now you know about this ;)

---

