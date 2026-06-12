---
title: "removing texlive"
date: 2009-11-17
forum: General Help
---

### Post by mistikkia on 2009-11-17
Hello eveyone, 

I was trying to install texlive when I remained without current, hence the installation was brutally stopped. After I've got power back on I tried to install it again, purge it, remove it etc .. nothing work, i've even done : sudo dpkg --configure -a, which outputs this: 

Setting up lacheck (1.26-11.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing lacheck (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up tex-common (1.20) ...
dpkg: error processing tex-common (--configure):
 fgets gave an empty string from `/var/lib/dpkg/info/tex-common.triggers'
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on tex-common (>= 1.1; however:
  [....]
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lacheck
 tex-common
 prosper
 texlive-base
 texlive-generic-recommended
 texlive-doc-base
 texlive-fonts-recommended
 texlive-base-bin
 texlive-base-bin-doc
 texlive-latex-recommended
 texlive-pstricks
 texlive-latex-base
 texlive-fonts-recommended-doc
 latex-beamer
 texlive-latex-base-doc
 texlive-common
 texlive-extra-utils
 lmodern
 dvipdfmx
 latex-xcolor
 pgf





all the others end with :
sudo apt-get remove texlive
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package texlive is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
21 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tex-common (1.20) ...
dpkg: error processing tex-common (--configure):
 fgets gave an empty string from `/var/lib/dpkg/info/tex-common.triggers'
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.; however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
[...]
 texlive-latex-base-doc depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-common
 texlive-base-bin
 dvipdfmx
 lacheck
 texlive-doc-base
 texlive-base
 texlive-latex-base
 texlive-latex-recommended
 latex-xcolor
 pgf
 latex-beamer
 lmodern
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-base-bin-doc
 texlive-extra-utils
 texlive-fonts-recommended
 texlive-fonts-recommended-doc
 texlive-latex-base-doc
**********E: Sub-process /usr/bin/dpkg returned an error code (1)****


what can I do to have a functional texlive package ... any hints appreaciated.



best,
mistikkia

---

### Post by ohzopants on 2009-11-17
Try running apt-get check.  It's worth a try.

---

### Post by bhishan on 2009-11-17
Can't it be removed from Synaptic?

---

### Post by zika on 2009-11-17
Did You try **sudo aptitude install -f** ... and then regular actions ...?

---

### Post by mistikkia on 2009-11-17
tried sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done


tried Synaptic both the remove and remove  actions and in the reinstall one ... nothing ... these are some of the errors: 

E: dvipdfmx: subprocess installed post-removal script returned error exit status 2
E: latex-beamer: subprocess installed post-removal script returned error exit status 2
E: pgf: subprocess installed post-removal script returned error exit status 2
E: latex-xcolor: subprocess installed post-removal script returned error exit status 2
E: prosper: subprocess installed post-removal script returned error exit status 2

E: tex-common: fgets gave an empty string from `/var/lib/dpkg/info/tex-common.triggers'
E: texlive-common: dependency problems - leaving unconfigured
E: texlive-base-bin: dependency problems - leaving unconfigured
E: dvipdfmx: dependency problems - leaving unconfigured
E: lacheck: subprocess installed post-installation script returned error exit status 2
E: texlive-doc-base: dependency problems - leaving unconfigured
E: texlive-base: dependency problems - leaving unconfigured
E: texlive-latex-base: dependency problems - leaving unconfigured
E: texlive-latex-recommended: dependency problems - leaving unconfigured
E: latex-xcolor: dependency problems - leaving unconfigured
E: pgf: dependency problems - leaving unconfigured
E: latex-beamer: dependency problems - leaving unconfigured
E: lmodern: dependency problems - leaving unconfigured
E: texlive-generic-recommended: dependency problems - leaving unconfigured
E: texlive-pstricks: dependency problems - leaving unconfigured
E: prosper: dependency problems - leaving unconfigured
E: texlive-base-bin-doc: dependency problems - leaving unconfigured
E: texlive-extra-utils: dependency problems - leaving unconfigured
E: texlive-fonts-recommended: dependency problems - leaving unconfigured
E: texlive-fonts-recommended-doc: dependency problems - leaving unconfigured
E: texlive-latex-base-doc: dependency problems - leaving unconfigured



tried sudo aptitude install -f texlive

oc-base ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing texlive-doc-base (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Removing texlive-common ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing texlive-common (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 dvipdfmx
 latex-beamer
 pgf
 latex-xcolor
 prosper
 texlive-pstricks
 texlive-latex-recommended
 texlive-latex-base
 texlive-generic-recommended
 texlive-fonts-recommended
 texlive-extra-utils
 texlive-base
 texlive-base-bin
 texlive-base-bin-doc
 texlive-fonts-recommended-doc
 texlive-doc-base
 texlive-common
E: Sub-process /usr/bin/dpkg returned an error code (1)



still... nothing works :( but thanks for the hints

---

### Post by mistikkia on 2009-11-17
i notice that if i do sudo apt-get upgrade it gives me as error the texlive packages ... and i tried to remove them but i did not manage .... 

how can they be removed?

sudo apt-get purge dvipdfmx
..... and it does not want to remove it :

dpkg: error processing texlive-common (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 dvipdfmx
 latex-beamer
 pgf
 latex-xcolor
 prosper
 texlive-pstricks
 texlive-latex-recommended
 texlive-latex-base
 texlive-generic-recommended
 texlive-fonts-recommended
 texlive-extra-utils
 texlive-base
 texlive-base-bin
 texlive-base-bin-doc
 texlive-fonts-recommended-doc
 texlive-doc-base
 texlive-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


i found here a potential solution (he had exactly the same problem as i did .. a power cut that messed everything up) but i cannot apply it.... because mine are not files, but packages (i think) :

" The power cut caused the corruption of some files, causing problems with dpkg, particularly `/var/lib/dpkg/info/openoffice.org-impress.list'. For some reason, dpkg (or apt-get) can't work if some `.list' files are corrupted; I hope such behavior will get corrected. Why not just ignore a bad file and continue on?
 To clear the cache, and other things, `sudo apt-get clean' is good to do. `apt-get update' and `apt-get upgrade' will ferret out the offending file (for me it was `/var/lib/dpkg/info/openoffice.org-impress.list').  So, delete that file and then `apt-get upgrade' again.  Then it should work.
 Purge openoffice.org-impress (it may be another package for others) and Install it again, perhaps the `.list' file will be restored.
"

---

### Post by mistikkia on 2009-11-17
quite odd..

in synaptic i have texlive-latex-base-doc in the "not install (residual config)" category ... but i can't do anything about it ...

also all the other texlive packages have remained marked for removal even after reopening synaptic ...


hm .. now i went into /var/lib/dpkg/info and  deleted the packages belonging to the offending packages ... obviously that was not a good idea ...

texlive depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-base-bin-doc (2007.dfsg.2-7ubuntu1) ...
&#65533;{&#65533;XWz~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Z&#65533;: not foundB
/usr/sbin/update-updmap: 1: e&#65533;&#65533;@}&#65533;m: not found
/usr/sbin/update-updmap: 1: &#65533;k: not found
/usr/sbin/update-updmap: 1: cannot open &#65533;&#65533;=O&#65533;&#65533;&#65533;&#65533;M&#65533;j&#65533;&#65533;&#65533;2J&#65533;&#65533;&#65533;&#65533;1I[&#65533;&#65533;#S&#65533;&#65533;I&#65533;&#65533;&#65533;?~G&#65533;&#958;&#65533;&#65533;&#65533;2&#1775;&#65533;&#65533;iV&#65533;&#65533;8z3W&#65533;&#65533;
                    %w&#65533;&#300;n&#65533;
                            &#65533;: No such file
/usr/sbin/update-updmap: 1: &#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;: not found
/usr/sbin/update-updmap: 1: &#65533;: not found
/usr/sbin/update-updmap: 1: &#65533;tt&#65533;&#65533;&#65533;.Y: not found
/usr/sbin/update-updmap: 2: Syntax error: ")" unexpected
dpkg: error processing texlive-base-bin-doc (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-fonts-recommended-doc (2007.dfsg.2-4ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
&#65533;{&#65533;XWz~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Z&#65533;: not found              /usr/sbin/update-updmap: 1: 6&#65533;B
[........]
/usr/sbin/update-updmap: 1: &#65533;tt&#65533;&#65533;&#65533;.Y: not found
/usr/sbin/update-updmap: 2: Syntax error: ")" unexpected
dpkg: error processing texlive-pstricks-doc (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 tipa depends on texlive-base-bin; however:
  Package texlive-base-bin is not configured yet.
dpkg: error processing tipa (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 texlive-base-bin
 dvipdfmx
 texlive-doc-base
 texlive-base
 texlive-latex-base
 texlive-latex-recommended
 latex-xcolor
 pgf
 latex-beamer
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-fonts-recommended
 texlive
 texlive-base-bin-doc
 texlive-extra-utils
 texlive-fonts-recommended-doc
 texlive-latex-base-doc
 texlive-latex-recommended-doc
 texlive-pstricks-doc
 tipa
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zika on 2009-11-18
> **mistikkia said:**
> tried sudo aptitude install -f texliveI meant just **sudo aptitude install -f **(without package name).

---

### Post by zika on 2009-11-18
> **mistikkia said:**
> tried sudo aptitude install -f texliveI meant just **sudo aptitude install -f **(without package name). Also try **sudo aptitude full-upgrade** ...
(Desperate times requires desperate measures ...)

---

### Post by Wolf-Ekkehard on 2009-12-29
Not sure whether you got this resolved mistikka - so just in case...

I too had a problem installing LaTeX, but there was no power failure, simply a broken package texlive-latex-base in the repo.I too could not get apt-get install -f to fix it, so I finally used
**sudo apt-get purge texlive-latex-base**
which solved at least the issue of cleaning up the database and getting rid of the package.  Did not solve the real problem of getting a good LaTeX install though, which is still open!

Has anybody successfully installed texlive-latex-base under 9.10 Karmic Koala?  If so, I'd like to get a hint as to what was done to make it happen, as I am getting increasingly frustrated with that thing...

---

### Post by Chronon on 2009-12-29
Wolf,

I have it installed on both 32-bit and 64-bit versions of 9.10.  I merely installed the packages using a GUI package manager in both cases.

---

### Post by Wolf-Ekkehard on 2009-12-29
Darn - how come I am the lucky one :-(   My 
sudo apt-get install texlive-latex-base 
returns with 
E: Sub-process /usr/bin/dpkg returned an error code (1)
(after a lot of other text, of course).  And I bet the dandy GUI does the same apt-get thing under the covers.

Did you check the return code and everything went fine? Because I ended up with a partial install of the package, and some basic stuff even works.

---

### Post by Chronon on 2009-12-29
Yes, it does use the same apt system under the covers.  I didn't notice any errors in the GUI (everything completed normally).  I also recently finished my dissertation using TexLive in Karmic.  I don't recall any special measures being necessary for installation on either system (32-bit system was an upgrade from Jaunty -- 64-bit system is a fresh install).

I understand this probably isn't very helpful to you.  I don't have a good idea for what would cause problems for one setup and not in another.

---

### Post by Wolf-Ekkehard on 2009-12-30
Thanks Chronon, I fixed it...

Looking in /tmp/fmtutil.xxxxxxxx I found out that the file "ushyph.tex" was missing and this caused all the trouble.  Tried to "find" it, and the file was really nowhere to be found on my machine.  Got it from [http://www.ctan.org/tex-archive/language/hyphenation/ushyph/]("http://www.ctan.org/tex-archive/language/hyphenation/ushyph/") and stuck it into my /usr/share/texmf-texlive/tex/generic/hyphen/.  After that, a
**sudo apt-get install -f**
fixed the broken package and everything is working fine now.

Since ushyph.tex was needed and wasn't in the package I downloaded, I reported this as a bug too.  But the above should be a work-around for those few that run into the same problem as I did.

The machine is a pretty prestine Dell laptop - just wiped Windows off of it and freshly installed Karmic Koala from scratch.  Why you got off the hook without the file is still a mystery to me...  Are you in the US (as this is apparently a country-specific hyphenation file)?

---

### Post by Ayers on 2010-03-16
dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 texlive-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
me@elijah-laptop:~$ 


I keep getting this error no matter what I try to install.
Thanks for the help:o

---

### Post by Chronon on 2010-03-16
Is that all the information you have?  Can you look for a similar file to what Wolf-Ekkehard mentioned (i.e. /tmp/fmtutil.xxxxxxxx)?  It seems some people have some issues when it comes to building formats.  (At least Wolf-Ekkehard and [one other person](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg647693.html) on the Debian support list.  In the latter case it was due to a spurious fmtutil.cnf file that was overriding the default.)

I suspect this will also provide a clue as to what is causing problems for you.

---

### Post by desired on 2010-04-18
i've got this error after install winefish. it said that latex was not installed yet in system.
i ignored anyway. but when i tried to install other package (any package) i got error-message below,

```
E: tex-common: subprocess installed post-installation script returned error exit status 1
E: texlive-binaries: dependency problems - leaving unconfigured
```

i solved this by complete-removing those two package(tex-common, texlive-binaries) and then install them back.

;-)

---

### Post by Wolf-Ekkehard on 2010-05-07
Unfortunately, the saga continues...

While upgrading to Lucid, when it came to upgrading/re-installing LaTeX, I got
```

...
dpkg: error processing texlive-binaries (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dvipng:
 dvipng depends on texlive-base-bin; however:
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
dpkg: error processing dvipng (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                  Errors were encountered while processing:
 texlive-binaries
 dvipng
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This time, manually installing ushyph.tex alone did not do the trick.  The fix is now a little more involved, so I post the entire sequence of commands
```

sudo wget -q -P /usr/share/texmf-texlive/tex/generic/hyphen \
        http://ctan.org/language/hyphenation/ushyph/ushyph.tex
sudo wget -q -P /usr/share/texmf-texlive/tex/generic/hyphen \
        http://ctan.org/language/hyphenation/frhyph.tex
sudo wget -q -P /usr/share/texmf-texlive/tex/generic/hyphen \
        http://ctan.org/language/hyphenation/dehyph/dehypht.tex
sudo wget -q -P /usr/share/texmf-texlive/tex/generic/hyphen \
        http://ctan.org/language/hyphenation/dehyph/dehyphn.tex
sudo apt-get install -f

```

This worked for me; and no, I have no idea why this package cannot install without all these hyphenation files from weird languages ;) and on top of that doesn't know how to get them itself.

---

