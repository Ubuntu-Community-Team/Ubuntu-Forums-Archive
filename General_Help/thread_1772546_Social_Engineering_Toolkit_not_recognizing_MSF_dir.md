---
title: "Social Engineering Toolkit not recognizing MSF directory"
date: 2011-05-31
forum: General Help
---

### Post by TheDr1ver on 2011-05-31
I realize this may be more of a post for backtrack-linux.org, but seeing as I recently switched from using Backtrack 4 R2 in favor of using a more customized (and driver-appropriate) Ubuntu 11.04 (Natty Narwhal), I felt it was better for me to post on the Ubuntu forums than over at backtrack-linux.

That said, I'm not sure if anyone here has experience with installing the Social Engineering Toolkit on Ubuntu and getting it to play nicely with Metasploit. I've used both SET and MSF for a while on Backtrack and am no stranger to how they operate. However, switching over to a different file structure on Ubuntu has caused some issues. Despite having modified the SET config file to point to the proper MSF directory:

```
/opt/framework-3.7.1/msf
```

When I load SET it tells me that it cannot find the MSF files.

I'm sure this is a simple problem and I'm just not seeing the solution (perhaps a different directory?), but I can't seem to find anything regarding this particular problem on these forums or the ones over at backtrack-linux.org. 

More details can be found as to exactly how I set up my current distro at [http://www.thedr1ver.com/2011/05/asus-1215n-ubuntu-natty-narwhal-with.html]("http://www.thedr1ver.com/2011/05/asus-1215n-ubuntu-natty-narwhal-with.html") -- but any assistance that could be offered would be greatly appreciated.

---

### Post by TheDr1ver on 2011-06-03
I figured out what was wrong thanks to the help of a commenter. The detailed solution can be found on my [blog]("http://www.thedr1ver.com/2011/05/asus-1215n-ubuntu-natty-narwhal-with.html").

The short version is this: 

To get SET to recognize your Metasploit directory, you must change the Metasploit directory to /opt/framework3/ and change the directory listed in SET to /opt/framework3/msf3

There were a few other unrelated errors I received once SET found MSF, but they don't pertain to this thread and are addressed on my blog.

---

