---
title: "emacs : intalling a new mode"
date: 2012-03-18
forum: General Help
---

### Post by silmaa on 2012-03-18
Hi,

I'm beginning with emacs, and I'd like to add a new mode : [hightlight indentation mode]("https://github.com/antonj/Highlight-Indentation-for-Emacs"). So I downloaded the lisp file, added it in ~/.emacs.d, and modified my .emacs.d as follow :
```
(menu-bar-mode -1)
(tool-bar-mode -1)
(scroll-bar-mode -1)
(setq ring-bell-function 'ignore)
(add-to-list 'load-path "~/.emacs.d/")
(autoload 'highlight-indentation-mode "highlight-indentation.el")
```

But when I try M-x hightlight-indentation or M-x highlight-indentation-mode, emacs tells me that this command does not exists...

What should I do ?

Thanks ):P

---

### Post by brainwash on 2012-03-18
You should try to include the elisp file via require:

```
(add-to-list 'load-path "~/.emacs.d")
(require 'highlight-indentation)
```

---

### Post by silmaa on 2012-03-20
Hi,

Thank you for your answer :)
But emacs tells me that my .emacs is wrong, with require...

```
Warning (initialization) : an error occurred while loading `home/bbti/.emacs` :
Symbol's value as variable is void: <!DOCTYPE

[...]
```
With --debug-init :```
Debugger entered--Lisp error: (void-variable <!DOCTYPE)
  eval-buffer(#<buffer  *load*<2>> nil "/home/bbti/.emacs.d/highlight-indentation.el" nil t)  ; Reading at buffer position 13
_  load-with-code-conversion_("/home/bbti/.emacs.d/highlight-indentation.el" "/home/bbti/.emacs.d/highlight-indentation.el" nil t)
  require(highlight-indentation)
  eval-buffer(#<buffer  *load*> nil "/home/bbti/.emacs" nil t)  ; Reading at buffer position 165
  _load-with-code-conversion_("/home/bbti/.emacs" "/home/bbti/.emacs" t t)
  load("~/.emacs" t t)
#[something unreadable]
[init-file-user system-type user-init-file-1 user-init-file otherfile source ms-dos "~" "/_emacs" windows-nt directory-files nil "^\\.emacs\\(\\.elc?\\)?$" "~/.emacs" "^_emacs\\(\\.elc?\\)?$" "~/_emacs" "/.emacs" t load expand-file-name "init" file-name-as-directory "/.emacs.d" file-name-extension "elc" file-name-sans-extension ".el" file-exists-p file-newer-than-file-p message "Warning: %s is newer than %s" sit-for 1 "default" alt inhibit-default-init inhibit-startup-screen] 7]()
  command-line()
  normal-top-level()
```

... not very explicit

---

### Post by brainwash on 2012-03-21
I'm running GNU Emacs 23.3.1. After downloading the highlight-indentation.el (version 0.6.0) and adding it to .emacs I can load it via M-x highlight-indentation-mode.

Not an expert myself, but maybe there is some codepage issue causing the error. :confused:

Can you attach your .emacs file and some details about your emacs setup please?

---

