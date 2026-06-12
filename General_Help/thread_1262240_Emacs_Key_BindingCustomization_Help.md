---
title: "Emacs Key Binding/Customization Help"
date: 2009-09-09
forum: General Help
---

### Post by ngrieb on 2009-09-09
I was trying to create a key binding for Emacs using the right and left arrow keys. Emacs has no complaints about the key binding after the change to the .emacs file, but it doesn't seem to work. Here is what I have:

(global-set-key "\M-[right]" 'end-of-line)
(global-set-key "\M-[left]" 'beginning-of-line)
blah...

Also I have global-font-lock mode on, and I want bold text. Is this possible? I have had this: 

(set-face-attribute :weight 'bold )

in my .emacs file again without anything happening...

Any ideas? Thanks in advance.

---

### Post by Brandon Williams on 2009-09-09
Don't use the quotes or the backslash when you're using a symbolic name.
```
(global-set-key [M-right] 'end-of-line)
(global-set-key [M-left] 'beginning-of-line)
```

As for setting the default font to bold ... my first thought was to use the builtin customize function to change that setting. It was fairly easy to find the right setting to change (Faces -> Basic Faces -> Default Face).

---

### Post by ngrieb on 2009-09-10
Ok, thanks for the tip. Does the bold default face require any sudo permissions? Because I was trying to do this at work, and everyone is locked out of root by the admins., and I have never been able to get the font face to stay bold for more than one session through the gui.

---

### Post by Brandon Williams on 2009-09-10
It shouldn't require sudo permissions. If I make that change using customize, then the setting shows up inside the custom-set-faces block in my .emacs file.

---

### Post by jpkotta on 2009-09-10
> **ngrieb said:**
> Ok, thanks for the tip. Does the bold default face require any sudo permissions? Because I was trying to do this at work, and everyone is locked out of root by the admins., and I have never been able to get the font face to stay bold for more than one session through the gui.

M-x customize-face RET bold RET
Then choose "Save for future sessions" in the State menu.

---

### Post by jpkotta on 2009-09-10
> **Brandon Williams said:**
> Don't use the quotes or the backslash when you're using a symbolic name.
```
(global-set-key [M-right] 'end-of-line)
(global-set-key [M-left] 'beginning-of-line)
```

As for setting the default font to bold ... my first thought was to use the builtin customize function to change that setting. It was fairly easy to find the right setting to change (Faces -> Basic Faces -> Default Face).

If you do C-h k and then press what ever key, it will show you what the key is bound to and an "encoding" of the key.  99% of the time you can copy this encoding verbatim by using the kdb macro.

Example: 
I type C-h k **C-h k**, and the following pops up:
> **C-h k** runs the command describe-key, which is an interactive compiled
Lisp function in `help.el'.

It is bound to **C-h k**, <f1> k, <help> k, <menu-bar> <help-menu>
<describe> <describe-key-1>.

(describe-key &optional key untranslated up-event)

Display documentation of the function invoked by key.
key can be any kind of a key sequence; it can include keyboard events,
mouse events, and/or menu events.  When calling from a program,
pass key as a string or a vector.

If non-nil, untranslated is a vector of the corresponding untranslated events.
It can also be a number, in which case the untranslated events from
the last key sequence entered are used.
up-event is the up-event that was discarded by reading key, or nil.

If key is a menu item or a tool-bar button that is disabled, this command
temporarily enables it to allow getting help on disabled items and buttons.
Then I can rebind it with 
```
(global-set-key (kbd "**C-h k**") 'my-kbd-help-func)
```

Then there is local-set-key, define-key and keymaps, global-unset-key, etc., but you can read the manual for that.

---

### Post by ngrieb on 2009-09-14
Thanks for all the help and great tips. I have just one more question: when I load Emacs, I have (setq default-frame-alist '((height . blah)(width . blah))), but recently the frame redraw has not been happening or has been happening very very slowly. Is there something I can do to make the frame redisplay at it's new size (I tried (redraw-frame) with no luck). I also have no idea what settings changed to make the redraw so slow. Might have been a GNOME theme change or something odd like that, but I don't see how that could affect the Emacs frame. Thanks again.

---

### Post by jpkotta on 2009-09-16
Yes, it seems like Emacs likes to resize the frame about 5 times before getting comfortable.  I use the customize feature to set the default-frame-parameters, but it does exactly what you have.  If you specify a -geometry on the command line or with X resources, you can make it start with the correct geometry.

---

### Post by ngrieb on 2009-11-11
I'm not very good with elisp, but is there a way to make it so that I can use the delete key for C_w (cut) when a region is selected, and for delete when normally being used? I attempted to look for examples but just had to parse through lines and lines of atrocious elisp code, which to me looks like absolute garbage (...so unstructured sometimes).
Thanks Again.

---

### Post by jpkotta on 2009-11-11
It seems like delete-char already does what you want, which I discovered halfway through writing this.  It's bound to C-d.

Anyway, this probably does what you want.  You probably need transient-mark-mode enabled (default in Emacs 23).
```

(defun kill-region-or-delete-char (start stop)
  (interactive "r")
  (if (use-region-p)
      (kill-region start stop)
    (delete-char 1)))

(global-set-key (kbd "C-w") 'kill-region-or-delete-char)

```

You need Emacs 23 to get use-region-p.  Here is the definition, which works with Emacs 22.

```

(unless (fboundp 'region-active-p)
  ;; use-region-p is not built-in in emacs22 or earlier
  (defun region-active-p ()
    "Return t if Transient Mark mode is enabled and the mark is active.

  Most commands that act on the region if it is active and
  Transient Mark mode is enabled, and on the text near point
  otherwise, should use `use-region-p' instead.  That function
  checks the value of `use-empty-active-region' as well."
    (and transient-mark-mode mark-active))
  (defcustom use-empty-active-region nil
    "Whether \"region-aware\" commands should act on empty regions.
  If nil, region-aware commands treat empty regions as inactive.
  If non-nil, region-aware commands treat the region as active as
  long as the mark is active, even if the region is empty.

  Region-aware commands are those that act on the region if it is
  active and Transient Mark mode is enabled, and on the text near
  point otherwise."
    :type 'boolean
    :version "23.1"
    :group 'editing-basics)
  (defun use-region-p ()
    "Return t if the region is active and it is appropriate to act on it.
  This is used by commands that act specially on the region under
  Transient Mark mode.  It returns t if and only if Transient Mark
  mode is enabled, the mark is active, and the region is non-empty.
  If `use-empty-active-region' is non-nil, it returns t even if the
  region is empty.

  For some commands, it may be appropriate to disregard the value
  of `use-empty-active-region'; in that case, use `region-active-p'."
    (and (region-active-p)
         (or use-empty-active-region (> (region-end) (region-beginning)))))
  )
```

---

