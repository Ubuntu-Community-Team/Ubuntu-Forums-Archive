---
title: "What does the CLEAN command do?"
date: 2011-05-30
forum: General Help
---

### Post by Maheriano on 2011-05-30
I see sometimes when you're compiling something to run, you do a make, install and clean. What exactly does clean do?

---

### Post by linuxinstalledfromhdd on 2011-05-30
it removes the temp files that were needed to do the compiling.

I like the beck quote.  Go listen to fumes on youtube by beck if you like beck.. :)

---

### Post by dFlyer on 2011-05-30
> **Maheriano said:**
> I see sometimes when you're compiling something to run, you do a make, install and clean. What exactly does clean do?

It cleans the temp files involved with compiling.

---

### Post by Maheriano on 2011-05-30
> **linuxinstalledfromhdd said:**
> it removes the temp files that were needed to do the compiling.

I like the beck quote.  Go listen to fumes on youtube by beck if you like beck.. :)

haha ya, some guy posted that in another thread and I thought it was genius.

So it doesn't do anything to your project files then? Some genius put a CLEAN file in an ANT project I was working on and a script ran and deleted every file in my project that I had worked on. I just wanted to make sure I wasn't crazy and that CLEAN really is an acceptable thing to run (or should be) when compiling things. It was in Springsource (Eclipse) on a Windows machine, I should have known it wouldn't be the same.

---

