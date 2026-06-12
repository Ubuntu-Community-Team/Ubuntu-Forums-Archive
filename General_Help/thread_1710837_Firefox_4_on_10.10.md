---
title: "Firefox 4 on 10.10"
date: 2011-03-20
forum: General Help
---

### Post by JP121 on 2011-03-20
Hello,

I downloaded Firefox 4 from the mozilla website and got it all set up.  Once the final release happens, how will I need to update it?  Also, is it worth my time to find a PPA with firefox4 and delete the setup I have right now once a trusted stable PPA appears?


Thanks.

---

### Post by lithopsian on 2011-03-20
You downloaded RC1 (or RC2)?  I am told that it will automatically update itself to 4.0 when that is released.  Keep an eye on it though, because I don't believe that 100%.  Of course, if the release candidate syands up to testing over the next week or so then it will be the final version except for the version number string :)

I don't bother hunting for Firefox PPAs but then I need the flexibility to install the exact version I want, when I want.

---

### Post by JP121 on 2011-03-20
Thanks for your response!  I feel better now knowing I am not going to be the only one not searching for  PPA.  According to the release notes I have RC2.:)

---

### Post by sports fan Matt on 2011-03-20
I used this guide this morning.  [http://ubuntuforums.org/showthread.php?t=1708905](http://ubuntuforums.org/showthread.php?t=1708905) "How To: Install Mozilla Firefox 4 RC 1 (64bit/32bit) "

---

### Post by Frogs Hair on 2011-03-20
If you choose the ppa you will have Firefox 4 , but it will always be called Minefield and you will have to deal with the daily builds.

---

### Post by JP121 on 2011-03-20
I think I am going to stick with what I got now.  The only issue is that I guess 3.6 and 4.0 can't coexist, because now whenever I try to launch 3.6, 4.0 launches, which is fine by me.

EDIT:

I tested it again but without 4.0 open, I think that is the problem.  Firefox can't have them both open at the same time.  Also whenever I open 3.6, the next time I run 4.0 I get the first launch page again, kind of interesting behavior.

---

### Post by pickarooney on 2011-03-21
Is there any way I can get firefox 4 and have it called firefox 4 like on every other OS?

I don't get this minefield/nakatori nonsense.

---

### Post by khelben1979 on 2011-03-22
> **pickarooney said:**
> Is there any way I can get firefox 4 and have it called firefox 4 like on every other OS?

I don't get this minefield/nakatori nonsense.

Why bother when you know it's Firefox 4? Otherwise I guess you could get a Firefox 4 skin or something just so you get reminded of what version you're using. 
:lolflag:

---

### Post by pqwoerituytrueiwoq on 2011-03-22
> **Frogs Hair said:**
> If you choose the ppa you will have Firefox 4 , but it will always be called Minefield and you will have to deal with the daily builds.
there is a ppa listed (link to) on  [http://ubuntuforums.org/showthread.php?t=1708905](http://ubuntuforums.org/showthread.php?t=1708905) that has it named firefox 

firefox 3.6 and 4 can coexist using the script on that thread
(you may want to use separate firefox profiles for each version)
use firefox -P to make it 
to specify what profile the desktop file open firefox with
firefox -P ff3-6
firefox -P ff4
firefox -P default
firefox -P $name_of_Profile

---

