---
title: "zeitgeist-fts using lots of memory"
date: 2012-05-30
forum: General Help
---

### Post by Finalfantasykid on 2012-05-30
zeitgeist-fts is using over 100MB of memory, not long after doing a search for files in the dash(it only does this for file searches, not application, or music lenses).

Any idea as to why this is?

---

### Post by Finalfantasykid on 2012-05-31
*bump*

Any ideas anyone?

---

### Post by raja.genupula on 2012-05-31
sounds like a BUG report it to Launchpad .

---

### Post by Finalfantasykid on 2012-05-31
I think it might be related to this bug [https://bugs.launchpad.net/zeitgeist-extensions/+bug/757727](https://bugs.launchpad.net/zeitgeist-extensions/+bug/757727)

Problem is, it was reported like a year ago.  I'll post in it though, maybe it will get more attention that way.

---

### Post by raja.genupula on 2012-05-31
yeah i have seen that . more people effected with this .

---

### Post by dtstanton on 2012-07-25
I had the same problem - zeitgeist eating up to 80% of my memory, (Ubuntu 12.04 LTS). Tried to uninstall it, but it came back like a bad penny - even though it was supposedly not installed so I could uninstall it again.
 
My solution was to take ownership of /usr/bin/zeitgeist* and make it *not* executable. I figure if it can't Execute, it won't be in my processes eating my RAM.
 
I used
 
sudo chown [username] /usr/bin/zeitgeist* 
 
and opened the Properties of the files, under Permissions un-checked the Executable box.
 
Could have probably just used 

sudo chmod a-x /usr/bin/zeitgeist*   (IF that's the correct syntax)

but I wasn't convinced it would stay gone unless I was the owner. I have only been away from Windows since Precise came out, and I was trying to cover all bases.
 
So far, no problems. I do expect to get an error here or there when a program tries to run it, but everything seems to be working ok. Hope this helps someone else.
 
  -Dale
 
 
(Update:  This solution worked for me. After performing the fix I mentioned, I have not had one instance of zeitgeist reloading, nor have I had problems with programs eating my RAM. I have seen no adverse effects or error messages, and I am using my computers just like I always did before the fix.)

---

### Post by HughJarse on 2013-04-21
I have this problem immediately after logging in. Using 1.1 gb mem, unineruptible process.
Can anyone tell me what this process is doing?

EDIT:
I killed this process and now I can use my computer again :)
The problem still needs fixing of course.

---

### Post by GameX2 on 2013-04-21
Same problem.  It's using 300MB of RAM, and it's still rising..

---

### Post by mark1977 on 2013-05-03
Same problem, it's currently using 633MB of RAM. I'm on 12.04.

---

### Post by Dermit_Zamponi on 2013-08-19
Same problem. Ubuntu 13.04, Linux 3.8.0-27-generic

---

