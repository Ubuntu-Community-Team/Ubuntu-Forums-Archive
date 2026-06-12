---
title: "brother printing issues"
date: 2010-03-06
forum: General Help
---

### Post by linuxcss on 2010-03-06
I have been trying to get 5250DN brother printer to print
envelopes correctly and Have tried installing the ppd
and a host of other things and still within openoffice 
on karmic nothing works correctly 

I have also installed the brother package specifically from
the repository via synaptic as well

any one have a solution

---

### Post by linuxcss on 2010-03-18
a hack around the envelope issue was to print to letter size and adjust  settings,
hard to believe such issues still exist ... 

NOTE  before any testing was done ran update-manager as of Mar 16,2010.

next  issue is this:

while trying to print this document


[http://www.thinkgeek.com/files/BC-9009-Manual.pdf](http://www.thinkgeek.com/files/BC-9009-Manual.pdf)

If  I print with adobe or xpdf documents to network printer hp 5m it is  done under 90secs,
however if I print to a brother network printer  5250dn with


driver:
Brother HL-5250DN Foomatic/Postscript  [en][recommended)  
or with
Brother HL-5250DN Foomatic/lj5gray  [en] 

its very slow ... 11 page pdf takes over 3.5 mins and that  pdf is not very complex
further if i use 
Brother HL-5250DN  BR-Script3 [en](recommended)
even prints slower ... 3mins 51 seconds,

anybody  have answers to these issues?

If i print using Foomatic/pxlmono  its 1:46 seconds,
if same file is printed from windows xp native  its  40 seconds,

so even the fastest mode used here is nearly 3 times  as slow as windows,
and worst case is nearly 6 times as slow in  windows

who has the reasons or fixes for this?

I also  changed the hp 5m above to foomatic/postscript and
the results were  even worst 6:40 or 10 times as slow as windows.

---

### Post by linuxcss on 2010-04-21
bttt

---

