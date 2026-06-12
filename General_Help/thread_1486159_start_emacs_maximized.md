---
title: "start emacs maximized"
date: 2010-05-17
forum: General Help
---

### Post by cytmtn on 2010-05-17
I was using the following code in my .emacs file to start emacs maximized:

> 
(defun toggle-fullscreen ()
  (interactive)
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
                 '(2 "_NET_WM_STATE_MAXIMIZED_VERT" 0))
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
                 '(2 "_NET_WM_STATE_MAXIMIZED_HORZ" 0))
)
(toggle-fullscreen)
After I upgraded to Lucid, it still works, but now the bottom of the window is cut off. Anybody have any ideas why this is, or how to fix it?

Reference for the original hack:

[http://ubuntuforums.org/showthread.php?t=782196](http://ubuntuforums.org/showthread.php?t=782196)

---

### Post by fbkarsdorp on 2010-05-19
Hi, don't know what the problem is, but I have a different method for full screen:

[FONT=Lucida Console](defun fullscreen (&optional f)
  (interactive)
  (set-frame-parameter f 'fullscreen
               (if (frame-parameter f 'fullscreen) nil 'fullboth)))
(global-set-key [f11] 'fullscreen)
(add-hook 'after-make-frame-functions 'fullscreen)[/FONT]

Bind it to whatever key you want. Hope it helps.

---

### Post by cytmtn on 2010-05-19
Thanks. That works pretty well. Anything to keep me from having to take my lazy hands off the keyboard :)

---

