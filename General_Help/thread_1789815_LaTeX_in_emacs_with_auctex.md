---
title: "LaTeX in emacs with auctex"
date: 2011-06-24
forum: General Help
---

### Post by snOOfy on 2011-06-24
I am new to ubuntu and currently trying to write LaTeX documents with emacs. I already installed emacs and auctex, but somehow I can't get it to parse a .tex document. This is the sample document I use:

[http://amath.colorado.edu/documentation/LaTeX/basics/example.html](http://amath.colorado.edu/documentation/LaTeX/basics/example.html)

When I use C-c C-p C-b the inline formula don't get parsed. Red error marks appear, the first error is:

gs -dOutputFile\=\(_region_.prv/tmp13105yRl/pr1-6.png\) -q -dSAFER -dNOPAUSE -DNOPLATFONTS -dPrinted -dTextAlphaBits\=4 -dGraphicsAlphaBits\=4 -sDEVICE\=png16m -r90.6379x90.4475
GS>{DELAYSAFER{.setsafe}if}stopped pop/.preview-BP currentpagedevice/BeginPage get dup null eq{pop{pop}bind}if def<</BeginPage{currentpagedevice/PageSize get dup 0 get 1 ne exch 1 get 1 ne or{.preview-BP 0 0 0 setrgbcolor clippath fill 0 1 0 setrgbcolor}{pop}ifelse}bind/PageSize[1 1]>>setpagedevice/preview-do{[count 3 roll save]3 1 roll dup length 0 eq{pop}{setpagedevice}{ifelse .runandhide}stopped{handleerror quit}if aload pop restore}bind def [(_region_.prv/tmp13105yRl/preview.ps)(r)file]aload exch dup 0 setfileposition 148416()/SubFileDecode filter cvx .runandhide aload pop dup dup 148416 setfileposition 121()/SubFileDecode filter cvx<<>>preview-do
Error: /typecheck in --setfileposition--
Operand stack:
   --nostringval--   (_region_.prv/tmp13105yRl/preview.ps)   (r)   (r)   (r)   148882   148882   148882   148758   148758   148758   148658   148658   148658   148537   148537   148537   148416
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   %loop_continue   --nostringval--   --nostringval--   false   1   %stopped_push   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1163/1684(ro)(G)--   --dict:0/20(G)--   --dict:79/200(L)--
Current allocation mode is local
Current file position is 31
GS<18>

What do I have to do to make it work?

---

### Post by Kobin on 2011-08-10
See here:
[http://ubuntuforums.org/showthread.php?t=1769817&highlight=auctex+preview]("http://ubuntuforums.org/showthread.php?t=1769817&highlight=auctex+preview")

Solved it for me

---

