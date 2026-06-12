---
title: "emacs editor problems"
date: 2011-01-04
forum: General Help
---

### Post by pgscannell on 2011-01-04
This is my first time using emacs.  I've been able to do some customization to make my editing experience more familiar for myself.
 
I do have a problem that I can't seem to solve.  When I start eht program, I not only have a buffer containing the file I wish to edit, but there is always a buffer named ***GNU Emacs* % **and also one named ***scratch***
 
Where are they coming from?  Ad more importantly, how do I tell emacs not to open them every time I invoke the program.  The one entitled *scratch* isn't a big deal because you don't see that one.  The other one is an annoyance that I would like to eliminate.
 
Thanks in advance,
Paul Scannell

---

### Post by psusi on 2011-01-04
They are both default buffers.  Just ignore them.

---

### Post by KJ KJ KJ on 2011-01-04
The *scratch* buffer is there as a place to test out snippets of Lisp. I don't know what the other one is because I use XEmacs (a holy war topic to be avoided).

Out-of-the-box, XEmacs starts in *scratch* only.  

Anyway, to solve your problem with Emacs:

[http://groups.google.com/group/gnu.emacs.help/browse_frm/thread/bf2fae706a7424f0/75a09396b8a8fba6?tvc=1#75a09396b8a8fba6](http://groups.google.com/group/gnu.emacs.help/browse_frm/thread/bf2fae706a7424f0/75a09396b8a8fba6?tvc=1#75a09396b8a8fba6)
[U]
[/U] 
Solution in 2nd post.

---

### Post by mdwy62 on 2011-03-09
I am a longtime user of xemacs, but for some time now, I have had a problem that is beginning to wear on me. I cannot get the filladapt-mode option to work by default. 

When xemacs starts up, I have to go to Options>Advanced>Emacs>Editing>Fill>FillAdapt>FillAdapt

This last brings up the configuration screen. I click on Done and it goes away. Only after this process can I invoke M-x filladapt-mode in a buffer. It is good for a given session, but if I have to restart xemacs, I have to go through this again.

Does anyone know how to enable this option without clicking through all these menus?

Thanks.

---

### Post by jpkotta on 2011-03-10
> **mdwy62 said:**
> I am a longtime user of xemacs, but for some time now, I have had a problem that is beginning to wear on me. I cannot get the filladapt-mode option to work by default. 

When xemacs starts up, I have to go to Options>Advanced>Emacs>Editing>Fill>FillAdapt>FillAdapt

This last brings up the configuration screen. I click on Done and it goes away. Only after this process can I invoke M-x filladapt-mode in a buffer. It is good for a given session, but if I have to restart xemacs, I have to go through this again.

Does anyone know how to enable this option without clicking through all these menus?

Thanks.

Disclaimer: I use GNU Emacs.

Many emacs libraries are autoloaded.  You just start using them and Emacs loads the lisp file if it hasn't been loaded already.  filladapt replaces some built-in functionality, which is why it's not autoloaded.  You need to explicitly load the lisp code before using it.
```
(require 'filladapt) ;; load the library if necessary
(setq-default filladapt-mode 1) ;; enable by default
```

Personally, I only want filladapt turned on in certain modes.  I also try to make my init.el portable to machines that don't have all of the packages I may want (plain require throws an error if it can't find a library).
```
(require 'filladapt nil 'noerror) ;; no error if it can't be found
(defun jpk/programming-mode-hook ()
  (when (featurep 'filladapt)
    (filladapt-mode 1)))

(add-hook 'c-mode-common-hook 'jpk/programming-mode-hook)
(add-hook 'python-mode-hook 'jpk/programming-mode-hook)
```

A lot of this stuff is described in the source for filladapt.  Just do M-x find-library RET filladapt RET.

---

### Post by mdwy62 on 2011-03-19
Worked like a charm. Many thanks!:D

---

