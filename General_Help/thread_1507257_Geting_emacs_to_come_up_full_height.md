---
title: "Geting emacs to come up full height?"
date: 2010-06-11
forum: General Help
---

### Post by jhefferon on 2010-06-11
I have a new 10.4 installation.  I am using the default Gnome setup.

I use emacs a lot, and I like to have as much screen space as possible.   So I edited the options to reset the fonts to be 10pt instead of the default and to drop the toolbar.  

Then I tried to get emacs to come up full height.   I tried a number of things, like .Xresoutces, but the most relevant one is that I changed the panel launcher properties to add the -fh option. 
  /usr/bin/emacs23 -fh %F
Now emacs is full height all right, but the editing window is the same size, and the extra height comes from the minibuffer at the bottom of the screen.  It is 5 or 6 lines tall.

I'm a bit stumped.  Anyone know where this behavior is set?

Thanks,
Jim

---

### Post by jpkotta on 2010-06-12
It sounds like a bug.  Does it happen with ```
emacs -q -fh
```

I usually use emacs-snapshot (23.1.50.1).  "emacs-snapshot -fh" and "emacs-snapshot -q -fh" both work well, but without -q the scrollbar is not drawn until I move the mouse over it.  

I tried with emacs23 (23.1.1) and it didn't mess up the minibuffer, but without -q it puts a bunch of extra space between the scrollbar and (window manager) window border.  So there's something that I'm setting that makes -fh mess up in emacs23.

---

### Post by jhefferon on 2010-06-16
> **jpkotta said:**
> It sounds like a bug.  Does it happen with ```
emacs -q -fh
```

I usually use emacs-snapshot (23.1.50.1).  "emacs-snapshot -fh" and "emacs-snapshot -q -fh" both work well, but without -q the scrollbar is not drawn until I move the mouse over it.  

I tried with emacs23 (23.1.1) and it didn't mess up the minibuffer, but without -q it puts a bunch of extra space between the scrollbar and (window manager) window border.  So there's something that I'm setting that makes -fh mess up in emacs23.

The -q -fh invocation does make it come up the right size, but of course without the customizations.  Commenting out everything in the .emacs file also makes it come out the right size.

Leaving anything at all in the .emacs uncommented causes the error.  Starting with -init-debug (or is it -debug-init?) gets no rise out of the debugger, so I don't see that there are bad invisible chars in the .emacs file, or some such nonsense.

I guess it is not me (or you).  I guess it is a genuine bug.  Thank you for your help.

Regards,
Jim
Jim

---

### Post by jhefferon on 2010-07-22
In case someone finds this, I fixed it finally.  In .emacs I put

(defun toggle-fullscreen ()
  (interactive)
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
	    		 '(2 "_NET_WM_STATE_MAXIMIZED_VERT" 0))
;;  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
;;	    		 '(2 "_NET_WM_STATE_MAXIMIZED_HORZ" 0))
)
(toggle-fullscreen)

and I call it with "/usr/bin/emacs23 -fh %F" in the "Properties" part of the panel dohickey.

I'm not sure who posted this solution, or where, but thanks.

 Jim

---

### Post by BongoBen on 2010-08-11
The "defun toggle-fullscreen" method works great for me while using a separate emacs window, but I like to use the command line "emacs -nw" option a lot, and using the fullscreen hack I get:

error: X windows are not in use or not initialized

Anyone know how to make emacs check that I'm using the X windows version before using that function on startup?

---

