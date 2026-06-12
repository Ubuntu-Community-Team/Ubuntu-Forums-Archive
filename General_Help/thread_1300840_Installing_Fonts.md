---
title: "Installing Fonts?"
date: 2009-10-25
forum: General Help
---

### Post by monroetransfer on 2009-10-25
My trouble has basically been outlined [here]("http://ubuntuforums.org/showthread.php?t=985924") two years ago, but for some reason nobody helped the man.

I've installed, from the internet, a font "Monaco_Linux.ttf" which is a very pretty font for monospaced editing. I'd like to use it in my emacs. Emacs accepts font strings like -*-courier-*-*-*-*-*-12-* (this isn't correct, just an example.)

One can view a list of fonts which x can see and select them by various traits and receive a generated string like the above using "xfontsel". When I run it, I cannot find monaco under the "fmly" tab where it should be. I found some emacs lisp that would print the list of fonts in this format which emacs could see, and it also cannot find monaco (I've C-s'd and grep'd til my fingers bleed.)

The strangest part is, I have no trouble opening an xterm with the -fa option set to "Monaco Linux", which isn't even a very exact name, and is certainly not in the style emacs accepts, and as well, I can and have set "Monaco" as the font which gnome-terminal uses by default. It found it no problem.

What gives? I've run the whole "mv <fontname.ttf> /usr/share/fonts/truetype/custom/ && sudo fc-cache -f -v" song and dance, and that is what originally made monaco visible to xterm and various gnome apps (for example I can use it in gimp, oowriter, etc...) but not emacs.

The only fonts I can get working in emacs are HIDEOUS. Please help!

(PS if at all possible I'd like not to have to use gnome or have it running, as my main wm is fluxbox. I've only gone into gnome because it's very easy to set and examine system fonts.)

---

### Post by kushal.kumaran on 2009-10-25
Have you tried the emacs-snapshot-gtk package?  That should make font configuration much easier.  Snippet from my .emacs:

```
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(default ((t (:inherit nil :stipple nil :background "LightYellow1" :foreground "black" :inverse-video nil :box nil :strike-through nil :overline nil :underline nil :slant normal :weight normal :height 122 :width normal :foundry "unknown" :family "DejaVu Sans Mono")))))

```

---

### Post by monroetransfer on 2009-10-30
Thanks. I am pretty sure it had more to do with my install of ubuntu which was very old, heavily modded, and not maintained very well. At any rate, I'm in a fresh linux install right now, and remembering your advice, I installed emacs-snapshot-gtk, and it's crazy how easy it was to get monaco working (or any font for that matter. I didn't even bother with those annoying x font strings.) Thank you thank you thank you!!!

---

