---
title: "how to get older versions of emacs ?"
date: 2005-02-01
forum: General Help
---

### Post by dusu on 2005-02-01
I've very recently installed the ubuntu distribution on my laptop which is quite old (900MHz). Before this I had an older version of emacs, namely emacs20. It ran much faster than emacs21 available with ubuntu, and I'm anyway not using the clickable icons of emacs21... so no need for the latest version.

I've tried to get emacs20 by doing some *apt-get install emacs20*, but I'm just told that  this package is missing, obsolete or available from somewhere else.

Does any one know how to get emacs20 ? thanks in advance

---

### Post by dusu on 2005-02-02
Hmmm,

I think I have not been clear enough in my post, and everyone wondered how the hell can emacs be slow ??? Sorry for the newbie mistake  :?
The point is that I'm using emacs together with auctex to directly compile some LaTeX from emacs. I also use emacs to remote-control gnuplot thanks to the gnuplot-mode available for emacs.
And for these two applications, things are really slower than they should be, and I think it is due to emacs...

In any case, I think my question also applies for any other software. Where can one get older versions ?

Any answer is welcome

---

### Post by mendicant on 2005-02-02
You can try getting the one from the Debian stable distribution.  There's no guarantee that it would work under Ubuntu, though: 
  [http://packages.debian.org/stable/editors/emacs20](http://packages.debian.org/stable/editors/emacs20)
Personally, I would first try to see if I couldn't get everything working nicely under emacs21, but you may have other priorities.

Older packages in general may be hard to find, unless you make them yourself.  Basically, you need to find somebody that maintains them for the distribution, or do it yourself.   You could also rebuild it from Debian sources or straight from emacs 20 sources.  In the latter case, you can keep track of it using checkinstall or stow.

---

### Post by dusu on 2005-02-02
Thanks a lot for the infos  :)
I'll try it !

---

