---
title: "bin folder problems"
date: 2012-01-09
forum: General Help
---

### Post by masterrob213 on 2012-01-09
im trying to put unrar in the bin folder so it will run but every time i try to i get a thing that says that im not the owner. why?

---

### Post by Stovey on 2012-01-09
Hi Master Rob!  I am just a rookie at this, but I'll take a stab anyhow.  Someone more knowledgeable can feel fee to correct me or provide a better explanation.

There are numerous bin folders on your system (perhaps half a dozen?).  Some of those are "owned" by the root user or superuser.  I am guessing the bin folder you are using is owned by "root" - not you.

Create a bin folder in your home folder ie /home/name/bin or ~/bin.  Then logout and log back in.  Your system will the recognize your new bin folder as a place for executables (because ~/bin is defined as a PATH in your .bashrc, but does not exist.  You have to add it.)

---

### Post by masterrob213 on 2012-01-09
yay thank you so much ^_^ but im a little confused. how did it see that as a root file like the bin file?

---

### Post by m_duck on 2012-01-09
There is an unrar package in the repositories that would probably be a  'better' way of isntalling it, so it will receive updates. It would also mean  that its binary would be in the system PATH (likely /usr/bin) so that  it would always be recognised, regardless of user. Then again, this may  not apply to your situation.
> **masterrob213 said:**
> yay thank you so much ^_^ but im a little confused. how did it see that as a root file like the bin file?
I'm not sure I understand this question. The PATH variable is a list of locations which BASH will look through when you run a command, to save you from having to type the full path. By the looks of things, the "bin" directory in a users home directory is already in the PATH in Ubuntu, ergo by putting your binary in there, Ubuntu then recognises it.

You can see what is included in your current PATH by running the following in a terminal:```
echo $PATH
```

---

