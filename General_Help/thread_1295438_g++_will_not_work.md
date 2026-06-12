---
title: "g++ will not work"
date: 2009-10-19
forum: General Help
---

### Post by Koitsu on 2009-10-19
Hello there!
I am entirely new to Linux but about a week ago I was forced to write some smaller programmes using KDE (?).
Because I soon found that Windows is everything but fit to continue this at home I took this nice Ubuntu 5.10 Version and installed it on my laptop computer.
Everything was fine and I even think I understood that in order to install further components you use Synaptic.
So there I searched for "g++" and installed what was found.
I type in "g+ --help" in the terminal and everything is just peachy.
I type in "g++ Prog1.cpp -o Prog1 and I get like a million error messages.
Since I just copied the text of the programme  I wrote earlier (and which, of course, previously worked) I do not even have an idea where to look for my mistake.
I would be really happy to be illuminated :)

---

### Post by -Zeus- on 2009-10-19
I would highly recommend going with a newer version, 5.10 is 4 years old.  The latest release is about to be 9.10, you can get the beta at [http://ubuntu.com](http://ubuntu.com) or just wait about a week until it comes out.  Also, if you go to [http://shipit.ubuntu.com](http://shipit.ubuntu.com), they can mail you a CD, though it may take a while.

As for the problem, have you installed the package 'build-essential'?

---

### Post by hyperAura on 2009-10-19
so what u did is remove essential packages for g++ using synaptic.. since the g++ command is working that means that there is something wrong with the compiler if ur program is normally working..

---

### Post by Niko Johnson on 2009-10-19
try this ```
 sudo apt-get install g++ 
``` Thats how i installed g++ and it worked just fine

---

### Post by Giblet5 on 2009-10-19
> **Koitsu said:**
> Hello there!
I am entirely new to Linux but about a week ago I was forced to write some smaller programmes using KDE (?).
Because I soon found that Windows is everything but fit to continue this at home I took this nice Ubuntu 5.10 Version and installed it on my laptop computer.
Everything was fine and I even think I understood that in order to install further components you use Synaptic.
So there I searched for "g++" and installed what was found.
I type in "g+ --help" in the terminal and everything is just peachy.
I type in "g++ Prog1.cpp -o Prog1 and I get like a million error messages.
Since I just copied the text of the programme  I wrote earlier (and which, of course, previously worked) I do not even have an idea where to look for my mistake.
I would be really happy to be illuminated :)


You can easily get a million errors by forgetting just one header file.

C++ is picky. That's a good thing.

Post your output and the list of headers you're including in the code.

Or, post the code and I'll fix it for you.

---

### Post by QIII on 2009-10-19
If I remember by KDevelop days correctly, you get a design-time warning about missing headers...  Maybe not.

But I'm with Giblet5.  There is little anyone can do to help without knowing what at least a few of the million errors are.

---

### Post by Koitsu on 2009-10-19
> **-Zeus- said:**
> I would highly recommend going with a newer version, 5.10 is 4 years old. The latest release is about to be 9.10, you can get the beta at [http://ubuntu.com](http://ubuntu.com) or just wait about a week until it comes out.  Also, if you go to [http://shipit.ubuntu.com](http://shipit.ubuntu.com), they can mail you a CD, though it may take a while.

As for the problem, have you installed the package 'build-essential'?


Yes, I admit my library is a bit outdated, but I was glad to find something besides Windows at all when I looked through my CDs. I'll have to read the change log though.

Installing "buil-essential" really helped. I do not know what it is that I just installed but now everything seems to be the way it is supposed to be.

Since it seems to work just fine for the moment I guess I have to thank all of you for the swift support and go back to my files then.

---

### Post by -Zeus- on 2009-10-19
> **Koitsu said:**
> Yes, I admit my library is a bit outdated, but I was glad to find something besides Windows at all when I looked through my CDs. I'll have to read the change log though.

Installing "buil-essential" really helped. I do not know what it is that I just installed but now everything seems to be the way it is supposed to be.

Since it seems to work just fine for the moment I guess I have to thank all of you for the swift support and go back to my files then.
Nailed it! :P

If you could, please edit your original post and mark it as "solved" (you need to go to the advanced editor.)

---

