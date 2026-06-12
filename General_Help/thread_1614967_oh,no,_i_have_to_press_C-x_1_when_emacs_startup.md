---
title: "oh,no, i have to press C-x 1 when emacs startup"
date: 2010-11-06
forum: General Help
---

### Post by niejieqiang on 2010-11-06
hi,there.i intend to integrate with speedbar in the emacs frame.
but the it seems didn't work correctly follow my mind, i have to press C-x 1 to solve the mistake when emacs startup!!! 

screenshot for emacs starup:
[IMG]http://pic.yupoo.com/niejieqiang/ABrjTcUx/14RM3f.png[/IMG]

and after i  press C-x 1
[IMG]http://pic.yupoo.com/niejieqiang/ABrjRF3w/4Q3zU.png[/IMG]

 what should i write in .emacs? and  i had wrote these lines to ~/.emacs:

;speedbar intergration
(require 'tramp)
(defconst my-junk-buffer-name "Junk")
(setq junk-buffer (get-buffer-create my-junk-buffer-name)
      )
(require 'speedbar)
(defconst my-speedbar-buffer-name "SPEEDBAR")
(setq speedbar-buffer (get-buffer-create my-speedbar-buffer-name)
      speedbar-frame (selected-frame)
      dframe-attached-frame (selected-frame)
      speedbar-select-frame-method 'attached
      speedbar-verbosity-level 0
      speedbar-last-selected-file nil)
(setq right-window (split-window-horizontally 30))
(setq left-window (frame-first-window))
;(walk-windows (lambda (w) (setq left-window w)) "nominibuffer" t)
(set-buffer speedbar-buffer)
(speedbar-mode)
(speedbar-reconfigure-keymaps)
(speedbar-update-contents)
(speedbar-set-timer 1)
(set-window-buffer left-window "SPEEDBAR")
(set-window-dedicated-p left-window t)
(toggle-read-only) ; HACK, REQUIRED for Tramp to work ????
(select-window right-window)
(defun select-right-window () (select-window right-window))
;(defun reset-window-config () (interactive)
; (walk-windows (lambda (w) (when (not (or (eq w left-window) (eq w right-window))) (delete-window w))) "nominibuffer" t)
; )p
(defun reset-window-config () (interactive)
  (delete-other-windows)
  (setq right-window (split-window-horizontally 30))
  (setq left-window (frame-first-window))
  (set-window-buffer left-window speedbar-buffer)
  (set-window-dedicated-p left-window t)
  (select-window right-window)
  (set-window-dedicated-p right-window nil)
  (when (eq speedbar-buffer (window-buffer right-window)) (set-window-buffer right-window (next-buffer)))
  (set-window-dedicated-p right-window nil)
  )
(global-set-key "\C-x1" 'reset-window-config)

---

### Post by niejieqiang on 2010-11-06
i mean what should i do to integrate speedbar correctly and don't need press C-x 1 everytime.


&#20013;&#22269;&#28246;&#21335;&#33391;&#27665;&#39640;&#21628;&#19968;&#22768;&#65306;

&#20808;&#35874;&#35874;&#20102;:)

---

### Post by ronacc on 2010-11-06
try adjusting the value ```
(setq right-window (split-window-horizontally 30))
``` ( 2 places ) to 10 and see what happens , I think that is the value in columns not pixels .

---

### Post by niejieqiang on 2010-11-06
many thanks &#65292;i had try this approach before &#65292;and it says :
   error: Window width 9 too small (after splitting)

it works without error when i adjust to 10,  but when i press  C-x 1 , the left column display very small 
screenshot when startup:

[IMG]http://pic.yupoo.com/niejieqiang/ABwWQYDk/bMqts.png[/IMG]

after i press C-x 1,  
[IMG]http://pic.yupoo.com/niejieqiang/ABwWRUrK/8dK1v.png[/IMG]

it seems the problem not be solved.

---

### Post by cariboo on 2010-11-06
I know the folks here like to be helpful, but what has this got to do with Natty Testing and Discussion?

---

### Post by niejieqiang on 2010-11-07
i'm sorry

---

