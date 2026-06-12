---
title: "Zim &amp; LaTeX"
date: 2011-08-31
forum: General Help
---

### Post by floydian_slip on 2011-08-31
Hi,

I just installed the wiki-style notes program Zim and would like to use the Equations plugin, which has latex and dvipng as dependencies. Unfortunately Zim fails to recognize those dependencies, even though I've got them both installed, and the commands are available when I'm in terminal.

I think it may have to do with the fact that I got TeX Live directly from the website, instead of from the Ubuntu repositories. I installed it into my /home/brian directory and then added the relevant PATH, MANPATH, and INFOPATH stuff to my .bashrc file, so that the LaTeX man pages, commands, etc. are available.

So I have no idea why Zim won't recognize latex and dvipng as being available. Any help would be greatly appreciated!

Brian

---

### Post by floydian_slip on 2011-09-05
Still wondering about this. Any ideas? Maybe this will help...

```

brian@brian-PC:~$ latex --version ; dvipng --version
pdfTeX 3.1415926-2.3-1.40.12 (TeX Live 2011)
kpathsea version 6.0.1
Copyright 2011 Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
There is NO warranty.  Redistribution of this software is
covered by the terms of both the pdfTeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the pdfTeX source.
Primary author of pdfTeX: Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
Compiled with libpng 1.5.2; using libpng 1.5.2
Compiled with zlib 1.2.5; using zlib 1.2.5
Compiled with xpdf version 3.02pl5

This is dvipng 1.14 Copyright 2002-2010 Jan-Ake Larsson
dvipng 1.14
kpathsea version 6.0.1
Compiled with Freetype 2.4.4
Using libft 2.4.4
Using t1lib 5.1.2
Copyright (C) 2002-2010 Jan-Ake Larsson.
There is NO warranty.  You may redistribute this software
under the terms of the GNU Lesser General Public License
version 3, see the COPYING file in the dvipng distribution
or <http://www.gnu.org/licenses/>.
brian@brian-PC:~$ 

```

And here's a photo of what Zim tells me:

[IMG]http://i.imgur.com/pNSTI.png[/IMG]

Thanks.

Brian

---

### Post by floydian_slip on 2011-09-07
UPDATE: I've fixed it. I just did the following in terminal:

```

source .bashrc

```

I had already done that immediately after updating my .bashrc file for the PATH, MANPATH, INFOPATH stuff for LaTeX, but for some reason it's working now that I've done the command again.

Maybe it had to do with restarting my computer before doing the command, or doing the command while Zim was closed, etc.

---

### Post by floydian_slip on 2011-09-10
UPDATE 2: Sorry to belabor the issue, but it turns out that it had nothing to do with re-executing the source command above. In fact, the reason it works is because I have opened Zim through terminal!

Originally, I was opening Zim with Alt+F2 and then running "zim". By doing so, Zim says I have failed latex & dvipng dependencies. However, if I open Zim by typing "zim" in terminal, then the dependencies are OK and I can choose the equations plugin.

I have no idea why there would be such a difference between opening Zim with xfrun4 (Alt+F2) vs. terminal...

---

### Post by philrasch on 2012-10-27
Hi Brian,

Once you open xfrun4 type $SHELL.

There is a chance that xfrun4, or python, or zim is starting up another shell. Be careful of environment variable inheritance between shells. depending on how you start things you may inherit the path one way, and not inherit it another, which can make things particularly confusing.

---

