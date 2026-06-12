---
title: "How-To update latex packages?"
date: 2010-12-16
forum: General Help
---

### Post by WG- on 2010-12-16
Question how can I update latex packages is there any easy way to do it in linux, such as in windows (miktex for example).

I have installed all the TeX-live packages on the ubuntu software center. But I seem to have outdated older packages.

---

### Post by b.lo4443 on 2011-05-12
I see this is an older post.  I stumbled across it keyword searching for LaTeX discussions.  I'm a Linux newbie, was running LaTeX on Windows with MikTeX - but, I'm in the process of trying to leave Windows for Linux.

Anyway, I'm not a pro at Linux or LaTeX but I found helpful info on this topic here: [http://www.tug.org/texlive/debian.html](http://www.tug.org/texlive/debian.html)

Essentially, Ubuntu 10.04 is running TeX Live 2009 and they're not going to update it until TeX Live 2011 is released and then they have time to repackage for the Debian/Ubuntu distro.  As an alternative, you can manually load TeX Live, which gives you greater flexibility to update packages via CTAN repositories.  See the section "Vanilla TeX Live on Debian" on the same web page referenced above.

Hope this helps.

---

### Post by oldmankit on 2011-07-05
> **b.lo4443 said:**
> I see this is an older post.  I stumbled across it keyword searching for LaTeX discussions.  I'm a Linux newbie, was running LaTeX on Windows with MikTeX - but, I'm in the process of trying to leave Windows for Linux.

Anyway, I'm not a pro at Linux or LaTeX but I found helpful info on this topic here: [http://www.tug.org/texlive/debian.html](http://www.tug.org/texlive/debian.html)

Essentially, Ubuntu 10.04 is running TeX Live 2009 and they're not going to update it until TeX Live 2011 is released and then they have time to repackage for the Debian/Ubuntu distro.  As an alternative, you can manually load TeX Live, which gives you greater flexibility to update packages via CTAN repositories.  See the section "Vanilla TeX Live on Debian" on the same web page referenced above.

Hope this helps.
Thanks for those tips, made it very clear.

---

### Post by FreeTheBee on 2011-07-06
In case you want to use Kile it might be a bit more involved. When I switched to a manual install of texlive I had to mess with equivs, but that was quite a while ago. There is some info here, [kile-texlive-2008-equivs]("http://texblog.net/latex-archive/linux/kile-texlive-2008-equivs/").
The article is a bit old now, but perhaps it can still function as a guideline in case you run into trouble.

---

### Post by lisati on 2011-07-06
*Thread moved to **General Help**.*

---

### Post by catalin.hritcu on 2011-07-24
From the TeX Live webpage:[INDENT]*20jul11: public release made (also of MacTeX).*
[/INDENT]So if b.lo4443 is right then can we expect Tex Live 2011 coming soon to Ubuntu? Personally I'm a bit skeptical that this will be fast, they didn't even bother to support TeX Live 2010, so probably they don't care about 2011 either. This is sad, because the old packages that come with Ubuntu are *full of bugs*.

---

### Post by oldmankit on 2011-07-24
I will manually install tex live 2011 instead of waiting for Ubuntu, as soon as I find a good fast internet connection.  It looks really big - 1 or 2 GB!

---

