---
title: "Which of the emacs packages to install?"
date: 2009-12-11
forum: General Help
---

### Post by thebrotherofasis on 2009-12-11
Hello,

I'd like to install emacs to test it as a PHP editor. I have always used gedit or Eclipse for this task, but I have the feeling that Emacs is a more general-use editor and I'd like to test it.

So, when opening Ubuntu Software Center I find several packages when searching "Emacs", but I am not sure which is the one I sould Install

Emacs22 GTK+
Emacs22 X11
Devhelp
GNU Emacs 23
gnuclient

...

Have any of you used Emacs for PHP development?

Which package should I Install?

Thanks

---

### Post by ajacx on 2009-12-11
I use Emacs22 GTK+ on gnome, I haven't tried 23 yet. You might want to refer [www.emacswiki.org/emacs/PhpMode](www.emacswiki.org/emacs/PhpMode) and php-mode.sourceforge.net if you're planning to use it for php development.

---

### Post by llamabr on 2009-12-11
emacs will already come installed with your distibution.  it's already well suited to edit php files.  what do you want it to do that it's not already doing?

---

### Post by jpkotta on 2009-12-12
> **llamabr said:**
> emacs will already come installed with your distibution.
No, it's not.  You have to install a package.  I like emacs-snapshot (which is version 23 currently).  In Karmic there's a emacs23 package, but I guess I haven't felt the need to try it.  Anyway, I think 23 is a big improvement over 22, due to daemon mode, Xft fonts, and more.

> it's already well suited to edit php files.
I needed to get php-mode.el from elsewhere (php-mode on sourceforge).  There are two php-mode packages in the repos, neither of which I've tried.

Full disclosure: I barely know php, and have only done enough to fix a bug in a project at work.

---

### Post by thebrotherofasis on 2009-12-12
What would be the difference bewteen emacs snapshot and emacs22-gtk ?

---

### Post by thebrotherofasis on 2009-12-12
Ok, after a little bit of testing and playing around, and after installing different packages, I think the response to my question is really simple: 

```
sudo apt-get install emacs23 php-mode
```

apt-get configures the php-mode to work seamlessly with emacs.

Besides, I am beginning to learn emacs, and it's really cool!

---

### Post by jpkotta on 2009-12-13
> **thebrotherofasis said:**
> What would be the difference bewteen emacs snapshot and emacs22-gtk ?

emacs-snapshot is always a development snapshot of emacs, as opposed to emacs22 or emacs23, which are released versions of emacs.  The emacs devs typically do a good job of keeping the development code working so there  aren't any major bugs in the snapshots.  

FWIW, php-elisp is the one from [http://php-mode.sourceforge.net/](http://php-mode.sourceforge.net/), but it's really old for some reason.

---

### Post by thebrotherofasis on 2009-12-13
So, is php-mode from the repos the same as php-elisp?

Which one are you using?

---

### Post by jpkotta on 2009-12-14
From php-mode.el in php-mode package:
```

;;; php-mode.el --- major mode for editing PHP code

;; Copyright (C) 1999-2001 Turadg Aleahmad

;; Maintainer: Turadg Aleahmad <turadg at users.sourceforge.net>
;; Keywords: php languages oop
;; Created: 1999-05-17
;; Modified: 2002-01-22
;; X-URL:   http://php-mode.sf.net/

(defconst php-version "1.0.2"
  "PHP Mode version number.")

```

From php-mode.el in php-elisp:
```

;;; php-mode.el --- major mode for editing PHP code

;; Copyright (C) 1999-2004 Turadg Aleahmad

;; Maintainer: Turadg Aleahmad <turadg at users.sourceforge.net>
;; Keywords: php languages oop
;; Created: 1999-05-17
;; Modified: 2005-07-27
;; X-URL:   http://php-mode.sourceforge.net/

(defconst php-version "1.2.0"
  "PHP Mode version number.")

```

From php-mode at php-mode.sourceforge.net:
```

;;; php-mode.el --- major mode for editing PHP code

;; Copyright (C) 1999, 2000, 2001, 2003, 2004 Turadg Aleahmad
;;               2008 Aaron S. Hawley

;; Maintainer: Aaron S. Hawley <ashawley at users.sourceforge.net>
;; Author: Turadg Aleahmad, 1999-2004
;; Keywords: php languages oop
;; Created: 1999-05-17
;; Modified: 2008-11-04
;; X-URL:   http://php-mode.sourceforge.net/

(defconst php-mode-version-number "1.5.0"
  "PHP Mode version number.")

```

So they're all the same thing, just different versions of it.  I use 1.5.0 from sf, but like I said I don't do much php.  Which is best depends on whether if any of the versions gives you trouble.

---

### Post by thebrotherofasis on 2009-12-14
Interesting, way to find out differences between similar packages.

Thanks.

---

