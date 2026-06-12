---
title: "Animation Program for Linux?"
date: 2006-05-29
forum: General Help
---

### Post by Gracye on 2006-05-29
Not sure where to post this but I need an animation program like Animation Shop or Image Ready.  I really don't want to have to keep switching back and forth between my Linux and Windows partitions.  I want to get rid of Windows all together.

I can't figure out how to use Wine so I can't run programs through that.  I can get them installed but can't figure out how to run them after *sigh*

I thought GIMP had an animation part to it, but I can't seem to find it.

---

### Post by centered effect on 2006-05-29
You have to install gimp-gap from apt

---

### Post by Sef on 2006-05-29
> You have to install gimp-gap from apt

To install gimp-gap:
 
Open the Konsole (Kmenu > System > Konsole)

kdesu apt-get update

kdesu aptitude install gimp-gap


For more information on installing programs, [click here.]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Gracye on 2006-06-01
I'm on Ubuntu, so would I do sudo instead of kdesu?

---

