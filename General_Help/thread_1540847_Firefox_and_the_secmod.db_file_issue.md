---
title: "Firefox and the secmod.db file issue"
date: 2010-07-28
forum: General Help
---

### Post by yopnono on 2010-07-28
What is happening with the FF on ubuntu 10.04 x86?

I go nuts over this issue, now and then I need to del the secmod.db file to make the FF start.

Well.. quite often so to speak, and really annoying.

Firefox 3.6.8 ubuntu
Have tried a new profile = same after a while.

---

### Post by lovinglinux on 2010-07-29
There are threads all over the web about this, but I couldn't find a solution yet. Let us know if someone gives a solution on your thread on mozillaZine.

Have you tried to download Firefox from Mozilla to see if the problem exists only in the repository version?

---

### Post by yopnono on 2010-07-29
> **lovinglinux said:**
> There are threads all over the web about this, but I couldn't find a solution yet. Let us know if someone gives a solution on your thread on mozillaZine.

Have you tried to download Firefox from Mozilla to see if the problem exists only in the repository version?

yes I have seen alot of threads on this, but not solution like you say.

Have install FF from Mozilla and a new profile, no add-ons.

So it's just to wait and see.

---

### Post by yopnono on 2010-07-30
Have not had any issues since I removed the FireFTP.

But it's still to early to say.

---

### Post by lovinglinux on 2010-07-30
> **yopnono said:**
> Have not had any issues since I removed the FireFTP.

But it's still to early to say.

Interesting. I have stopped using FireFTP months ago, but today I decided to give it another try.  Fortunately, there wasn't a version compatible with Firefox 4 available :)

---

### Post by yopnono on 2010-07-30
Nope. Spoke to soon :(

I will now use the official FF and see.

---

### Post by lovinglinux on 2010-08-07
I know is not a solution, but I have created a new Firefox extension that allows to delete secmod.db and compatibility.ini automatically when exiting Firefox, so you don't need to do it manually.

[http://profilecleaner-extension.blogspot.com](http://profilecleaner-extension.blogspot.com)

After installation, the extension will start without deleting the files by default and it will prompt for selecting the files you want to delete.

I have included compatibility.ini because that is causing the same issue here, with Firefox 3.6.8.

---

### Post by yopnono on 2010-08-07
Great work. I will try it:)

I have been using the Firefox from Mozilla and have not had any issues.. so far

---

### Post by lovinglinux on 2010-08-07
> **yopnono said:**
> Great work. I will try it:)

I have been using the Firefox from Mozilla and have not had any issues.. so far

I have no problems with 3.0.19, 3.5.9, 4.0b1, 4.0b2, 4.0b3 and 4.0b4pre, but 3.6.8 fails every time, unless I delete the compatibility.ini or start with a clean profile. Go figure.

---

