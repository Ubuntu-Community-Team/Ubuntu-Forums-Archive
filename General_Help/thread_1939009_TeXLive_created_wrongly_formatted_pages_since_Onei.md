---
title: "TeXLive created wrongly formatted pages since Oneiric"
date: 2012-03-10
forum: General Help
---

### Post by jombra on 2012-03-10
Hello,

I have a questions to all TeX/LaTeX users.
Since 1994 I am using TeX/LaTeX quite intensively. 
Since Oneiric (11.10, stable, Lubuntu, 64 bit) the generated
DVI file is not correct, as a DinA4 page (i.e. the pagesize given)
is not used as before on all used systems (many Unixes :). 
The space on the page is no longer sufficient, i.e. when the page is 
really filled with text, the last lines are on the next page. 
As I rely heavily on TeX, I just switched from Lubuntu 11.10 to
Debian Squeeze (6.0) and now to Wheezy (Testing; both 64 bit). 
As given by versioning info the TeX/LaTeX versions are all the same
(belonging to TeXLive 2009 ... still), but in Debian this bug is not
present but the layout is correct as before and on many platforms.
I just installed Xubuntu 12.04 Beta (64 bit) and updated everything
right now - and all documents are generated wrongly in Precise like
they were generated wrongly in Oneric. 
As all installations were done from scratch (no upgades) and TeXLive full
and many additional packages are installed I would not consider the
installation to be the reason for the problem. 
Unfortunately I could not find anything about that bug in the WWW - but
maybe  I am just using the wrong keywords. 
As all documents are affected - also really simple ones - I would expect 
this problem to be seen by all TeX/LaTeX users. 
Are there others here in the forum who have come across this problem?
Any ideas how such a bug can be effectively reported to Ubuntu (if it
hasn't been reported yet) - and how one may get more details?
I would appreciate any idea/help/info - especially as such a bug should
not be present in the comming stable LTS release of Ubuntu. 
Many thanks in advance! 

Best wishes, JMB

---

### Post by llamabr on 2012-03-10
It may help if you post a minimal example, along with the behavior you expect, and the behavior you see.

---

### Post by jombra on 2012-03-11
Hi,

well, I don't think it makes sense to provide a PDF created by TeX/LaTeX
on Ubuntu verses that on Debian.
I must admit that as the problem is so extreme that it is clearly visible
I did not analyse much - and had hoped to get further information from others.
As explained before every document of mine is generated wrongly.
I just tried with an Ubuntu and Debian PS-file of the same TeX/LaTeX source,
made evince scale at 85% and showed them one against the other in two windows.
The TeX/LaTeX output (placing of images, fonts etc.) is exactly the same,
but the size of the page size isn't.
I measered it on screen (cm) just to show the proportion:
  21.5x27.5 Ubuntu
  20.8x28.8 Debian
with Debian being the correct one (i.e. the page size of all TeX/LaTeX runs
the last ~20 year I am using TeX (under DOS, Ultrix, OS/2, Linux, cygwin ...).
And I generated TeX output as scientist under many different language settings
without any page size trouble - so I don't even think about any local
customization being in the way ... but I may be wrong.
The layout is fixed in my LaTeX source by:
    \textheight24.8cm
    \textwidth16.9cm
    \topmargin-1.1cm
    \oddsidemargin-0.6cm
    \evensidemargin-0.6cm}
(which is reasonable for Din A4 being about 20.9 cm x 29.7 cm).
So the rough proportions (height / width) are:
  1.42 Din A4
  1.38 Debian
  1.28 Ubuntu
So if anyone can transform TeX/LaTeX documents the same way he did before
Oneiric that person has not the problem I have - the difference is clearly
visible (and people using TeX/LaTeX tend to spot bad styling in sub-mm range;)).
So any questions about further specification makes it clear that the problem
is not present for the one rising the question.
Maybe I code in a special way - but the difference between Debian and Ubuntu
using the same version (TeXLive 2009, IMHO) is strange anyway.
But as Debian works for me (after a lot of configuration work - not related
with TeX), I am not in a hurry to use Ubuntu right now.
The only point to rise my question is - next to curiosity - to help fixing
a bug in the LTS version. It would habe been the candidate to recommend
for people not so deeply involved in Unix/Linux ... but I may consider
Debian Wheezy (Testing) for that purpose now ... making me the 1st spot
for quesions. I but can only recommend what I (at least sometimes) use.
But thanks anyway to give that hint - maybe I could clarify what I envisioned.

Best wishes,
JMB

---

### Post by jombra on 2012-10-22
Hello - just back in the Ubuntu game,


well, as I switched to Debian Testing/Wheezy I did not look at the problem
further. With Ubuntu 12.10 I wanted to check if the problem is solved - and
it ist not.
Actually, TeX/LaTeX is correct - the problem is the default paper size being
letter on the system ([font=courier]/etc/papersize[/font] was "letter" not "a4") and thus
```

  paperconf -n  => letter
  paperconf -s  => 612 792

```
As I found no command to change it I did it by hand:
```

  vi /etc/papersize   => a4
    paperconf -n  => a4
    paperconf -s  => 595.276 841.89

```
But I don`t know how to change TeX configuration for all the special
components (like: dvips/dvipdft/ps2pdfwr/dvipdfmx) and maybe other
parts of the system configuration depending on that.
```

texconfig paper a4
    ... just yields: "This command shouldn't be used on Debian.
                      Please use 'paperconf' instead."

```
But paperconf seems not to work for me - and
```

    tlmgr paper a4

```
is not present on the Ubuntu 12.10 system (full TeXLive being installed).

So I need a way to give the TeXLive package (and maybe other components)
the correct information and than it would be appropriate to file a bug,
as I think this is a bug of the Ubuntu installer - as one can just specify
(*giving my choice*):
  [center]language (English), Timezone (Berlin time),[/center]
  [center]and keyboard (German no deadkeys),[/center]
and I would not guess from that input that the user needs letter format,
would you? It would even be better to ask paper size seperately than to
misconfigure a system and hide its configuration (I am an experienced
Unix admin - maybe I should feel ashamed - but Ubuntu is not designed
for experts, right?).
Additionally, with these settings the paper configuration war OK before
Oneiric (that was the point to switch to Debian for me) and with similar
settings Squeeze/Stable was OK (which I migrated to Testing/Wheezy,
the hard way:) ).
***Can anyone help?***
 
The Internet is full of pieces of advice for changing paper size - but
nothing which really fits to Ubuntu (as far as I dug) ...
If anyone just wonders about the page size just look at:
```

  pdfinfo <documentname>.pdf
      -> Page size:      595 x 842 pts (A4)
           *** or ***
         Page size:      612 x 792 pts (letter)
  grep -i paper <documentname>.ps
      -> %%DocumentPaperSizes: Letter
         %%BeginPaperSize: Letter
           *** or ***
         %%DocumentPaperSizes: a4
         %%BeginPaperSize: a4

```
and if it is not what you want you're in the _configuration game_, too.

Any help in making my Ubuntu system fully aware of the [i]changed
paper size[/i] is highly welcome and that piece of information may be
appreciated by others too.
If I manage this myself I will update this thread, of cause.

Best wishes, JMB

---

### Post by Gerie Langeveld on 2012-10-22
Your locale settings is English, so you get the english settings for numbers, papersize, etc.
I found this page: [Locale]("https://help.ubuntu.com/community/Locale")
Your language setting (in system settings), LC_PAPER and /etc/papersize seem to be connected. And since you use English in Berlin, the "wrong" preference is chosen.
On my system the language in the system settings is Dutch, LC_PAPER is nl_NL.UTF-8 and /etc/papersize is a4.

---

### Post by jombra on 2012-10-24
Thanks for the hint to locale - actually it is [font=courier]LANG="en_US.UTF-8"[/font].
It is really strange that giving English to the language question results in US-English and letter format in recent Ubuntu version.
Before Oneiric, I never saw that kind of problem.
Additionally, if one does not correct this directly after basic installation, TeXLive is installed using letter format, and the normal commands to change the paper format are absolute useless (i.e. not working in Ubuntu/Xubuntu):
```

texconfig pdftex paper a4
texconfig dvipdfm paper a4
texconfig xdvi paper a4
texconfig dvips paper a4
texconfig paper a4  # should set default papersize for dvips, dvipdfm, pdftex and xdvi.
texconfig rehash  *or*  texhash  *or*  mktexlsr
paperconf -p a4

```
If someone knows how/if one can change this under *buntu a short description here would be welcome.
For those having such problems with an installation, one may define aliases or invoking commands with given paper format (here a4) as quick workaround:
```

dvips -t a4 ...
dvipdft -p a4 ...  # same for dvipdfm

```
As better "workaround" I just made a fresh installation, changed [font=courier]/etc/papersize[/font] to [font=courier]a4[/font] and installed package [font=courier]texlive-full[/font] and the other missing packages - and thus TeXLive uses consistently Din A4 paper format (learning the hard way).

From my point of view the installer is buggy (maybe on purpuse to present people as few questions as possible and neglecting quality; an impression I am getting from Unity, too - many bugs and as far as I have seen no additional customization compared to LTS, like focus-follow-mouse still missing instead of former promises by developers; and with 13.04 focussing on mobile devices it may even get worse).
Actually I am not very motivated - on the other side the Xubuntu people did a really great job - maybe I can stay on that distro (next to Debian).
Xubuntu is impressively faster on my machine (Intel 2700k, 16 GB memory, Intel chipset graphics) than Ubuntu (with same additional packages installed) and is after less configuration trouble better to use for **my** workflow.
I have trouble seeing the user base for Unity/Ubuntu after my current experience.
But maybe Xubuntu can regain some users - it seems to deserve 1st place on desktops right now (at least concerning the *buntu derivatives).
Maybe this is a good motivation to try filing a bug report against the installer.

---

