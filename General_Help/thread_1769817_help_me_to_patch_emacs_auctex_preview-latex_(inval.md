---
title: "help me to patch emacs auctex preview-latex (invalidfileaccess)"
date: 2011-05-28
forum: General Help
---

### Post by gmoutso on 2011-05-28
I'd like to use emacs auctex and its preview-latex feature. However I get an error

```

gs -dOutputFile\=\(_region_.prv/tmp3086MfS/pr1-3.png\) -q -dSAFER -dNOPAUSE -DNOPLATFONTS -dPrinted -dTextAlphaBits\=4 -dGraphicsAlphaBits\=4 -sDEVICE\=png16m -r94.1897x94.1727
GS>{DELAYSAFER{.setsafe}if}stopped pop/.preview-BP currentpagedevice/BeginPage get dup null eq{pop{pop}bind}if def<</BeginPage{currentpagedevice/PageSize get dup 0 get 1 ne exch 1 get 1 ne or{.preview-BP gsave 0.933608 0.890639 0.738293 setrgbcolor clippath fill grestore }{pop}ifelse}bind/PageSize[1 1]>>setpagedevice/preview-do{[count 3 roll save]3 1 roll dup length 0 eq{pop}{setpagedevice}{ifelse .runandhide}stopped{handleerror quit}if aload pop restore}bind def [(_region_.prv/tmp3086MfS/preview.ps)(r)file]aload exch dup 0 setfileposition 54521()/SubFileDecode filter cvx .runandhide aload pop dup dup 55385 setfileposition 216()/SubFileDecode filter cvx<<>>preview-do
Error: /typecheck in --setfileposition--
Operand stack:
   --nostringval--   (_region_.prv/tmp3086MfS/preview.ps)   (r)   (r)   (r)   55601   55601   55601   55385
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   %loop_continue   --nostringval--   --nostringval--   false   1   %stopped_push   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1163/1684(ro)(G)--   --dict:0/20(G)--   --dict:79/200(L)--
Current allocation mode is local
Current file position is 30
GS<9>

```

the invalidfileaccess error is some incompatibility between texlive 2009 and gs 9. There is a patch to solve it here
[http://lists.gnu.org/archive/html/bug-auctex/2010-10/msg00017.html](http://lists.gnu.org/archive/html/bug-auctex/2010-10/msg00017.html)

But I am not sure how to patch it. Can someone help me please?

I did the patch -p0 < file.diff and the I run ./configure in the same directory
/usr/share/emacs/site-lisp/auctex/preview
I got an error
```

configure: WARNING: Conflicting previous installation in `/usr/share/emacs/23.2/site-lisp/auctex/' found!
Conflicting previous startup file `/usr/share/emacs/23.2/site-lisp/preview-latex.el' found!

```

Anyway, I am not sure what I am doing above. Any help appreciated.

---

### Post by gmoutso on 2011-05-28
I was trying to solve the preview-latex problem in emacs. Anyway, I solved this by removing auctex and reinstalling a newer version from [http://theotp1.physik.uni-ulm.de/~ste/comp/emacs/auctex/snapshots/ftp/auctex-current.tar.gz](http://theotp1.physik.uni-ulm.de/~ste/comp/emacs/auctex/snapshots/ftp/auctex-current.tar.gz)
[http://www.latex-community.org/forum/viewtopic.php?f=25&p=50323#p48391](http://www.latex-community.org/forum/viewtopic.php?f=25&p=50323#p48391)

[https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/543266](https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/543266)

---

