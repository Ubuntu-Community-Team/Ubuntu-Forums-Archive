---
title: "xdvi not showing menu"
date: 2010-11-27
forum: General Help
---

### Post by cholericfun on 2010-11-27
Hi
i am writing in Latex and tend to view my document in xdvik out of the vim editor.
for some strange reason i suddenly dont have a menubar or scrollbar in xdvi anymore. i looked at the manpage which mentioned +expertmode 16
but this doesnt work somehow. 
in .xdvirc the expertmode is swiched off as well, but it doesnt make a difference if i change it there either. Anyone any ideas?
i tried reinstalling, which didnt work. I am able to get normal behaviour back from the commandline via the -q option. however i'd rather just have things back to normal

---

### Post by cholericfun on 2010-11-27
Well, sort of solved:
i access the xdvi view of my currently edited .tex file from within vim directly by pressing ctrl-k with the following lines in vimrc (i found this on the web but forgot where and am too lazy to search, anyhow credit for this very practical thing goes elsewhere!)
(^K and ^M are generated as follows:
^K:  ctrl-k twice
^M:  ctrl-k, M

in my vimrc
:map ^K :w!^M:!clear; echo Making Postscript % ...; latex %; xdvi -q -expertmode 4%<.dvi&^M^M

i just added the xdvi options -q -expertmode 4

although i'm confused that without it doesnt work anymore,
this is really just a quickfix

---

### Post by mpiter on 2011-07-14
I guess that you solved your problem after all this time, but in doubt I reply.

Did you add the line [COLOR="SeaGreen"]xdvi.expertMode:	31[/COLOR] to your [COLOR="Blue"]~/.xdvirc[/COLOR] file?

---

### Post by cholericfun on 2012-05-04
Stange, i thought i had email notifications on,
so it took ages to even find this answer,

anyhow: your suggestion works like a charm, the edit is in vimrc though, no in xdvirc

thanks a lot

---

### Post by mpiter on 2012-05-08
Welcome.  It is fun that sometimes we find an old unanswered request.  We hesitate before answering because the request is so old.  We do it, and finally, it helps :-)

---

### Post by codingman on 2012-05-08
If you're question has been answered, please set it as solved ;)

---

### Post by cholericfun on 2012-05-15
yes, like
[http://imgs.xkcd.com/comics/wisdom_of_the_ancients.png]("http://imgs.xkcd.com/comics/wisdom_of_the_ancients.png")

but with a happy-end

---

