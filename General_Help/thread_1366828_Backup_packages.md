---
title: "Backup packages?"
date: 2009-12-28
forum: General Help
---

### Post by qkzoo on 2009-12-28
Hello, I'm a noob.  I have what is probably a really stupid question, but, as the old idiom goes... So, here's my situation: I live in the sticks, and have really slow internet, therefore, any decent size downloads I obtain, I like to backup so I don't have to download it again.  So my question is, if I used the "Ubuntu Software Center" to install stuff, like "Ubuntu restricted extras", are those downloaded packages somewhere on my system still so I can backup and reinstall them, if necessary?  This could also save me time when I convert our other PC over to Ubuntu.

By the way, any known issues I should be aware of before installing Ubuntu on a Dell desktop?

Thanks in advance,

Q

---

### Post by x33a on 2009-12-28
the packages are stored here:

/var/cache/apt/archives

also, this might be of interest to you:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by qkzoo on 2009-12-31
> **x33a said:**
> the packages are stored here:

/var/cache/apt/archives

also, this might be of interest to you:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

This was perfect, thank you!  For other newbies, you can install this really easily, just type "sudo apt-get install aptoncd" from terminal, piece of cake and piece of mind! \\:D/

---

