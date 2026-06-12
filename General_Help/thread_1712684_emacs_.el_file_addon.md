---
title: "emacs .el file addon"
date: 2011-03-23
forum: General Help
---

### Post by C0NFU53D2 on 2011-03-23
I'm new to the emacs thingy. i just moved back to ubuntu.
i have found out how to have emacs load the .el file from the .emacs file but i cant seem to use the addon.

[http://blogs.unity3d.com/2010/01/15/emacs-mode-for-unity-javascript/](http://blogs.unity3d.com/2010/01/15/emacs-mode-for-unity-javascript/)

that is the addon i  am trying to use.

this is my .emacs file:

(add-to-list 'load-path "~/.emacs.d")
;; UnityJS mode for emacs
(autoload 'unityjs-mode "unityjs-mode" "Major mode for editing Unity Javascript code." t)
(require 'unityjs-mode)

P.S. i'm sorry if this question has been answered, i couldn't find it with Google or the search here.

---

### Post by howefield on 2011-03-23
Moved to *General Help*.

---

### Post by jpkotta on 2011-03-23
The autoload is completely useless with the require.  require loads the lisp immediately, autoload defers the load until unityjs-mode is invoked (making start up faster).  I would use the autoload but you would probably want the require, if only for the fact that there's a line in there that associates .js files with the mode.

[http://www.emacswiki.org/emacs/LoadingLispFiles](http://www.emacswiki.org/emacs/LoadingLispFiles)

---

