---
title: "Evince dvi problem"
date: 2011-01-19
forum: General Help
---

### Post by cardogar on 2011-01-19
Hi friends!

I'm getting mad trying to find out why my document viewer is not able to open dvi files.

The thing is pretty weird because evince didn't show any problem opening dvi files until few days ago... and suddenly evince doesn't render dvi documents any more. I tried to open a dvi file, it failed and since then I cannot open any.

The problem is not due to the dvi files because I can open the files easily with xgdvi for instance, and evince is able to open pdf, ps and eps files...

I have installed tetex, texlive and ghostscript in my Ubuntu 10.04.1 with gnome.

Any help is more than welcome because the problem is pretty annoying. I'm used to create my documents with latex and evince was the perfect tool to visualize the intermediate dvi files.

If I run evince in a terminal I get this:

sudo evince test.dvi

** (evince:5708): WARNING **: Failed to connect to the session bus: /bin/dbus-launch terminated abnormally without any error message

** (evince:5708): WARNING **: Error connection to DBus: /bin/dbus-launch terminated abnormally without any error message


** (evince:5708): WARNING **: Error connecting to D-Bus: /bin/dbus-launch terminated abnormally without any error message
page: Error: could not load font `cmbxti10'
page: Error: could not load font `cmbxti10'

** (evince:5708): WARNING **: Setting attribute metadata::evince::sidebar_visibility not supported

otherwise I get a windows error like this:

Unable to open the document
DVI document has incorrect format

Thanks a lot in advance for any help you can provide me!

Cheers.

---

### Post by Lulofs on 2011-06-30
My dvi files from texmaker and latexila both crash evince.
There is only a screen flash.

As this is my second day of linux, it took me hours to find this problem.

I tried xdvik and it works. So i guess this is the work-around.

It looks like there is only the two of us that care about this problem.
With a few more hours of learning/searching, perhaps I can find the bug report page...
Ed

---

### Post by cardogar on 2011-07-01
I couldn't solve it finally and I tried several gnome viewers with poor results... however, I'm now satisfied with my current viewer. Try Okular from kde, it's not perfect but adequate for latex use.

Cheers.

---

### Post by frisket on 2011-07-02
> **cardogar said:**
> Try Okular from kde, it's not perfect but adequate for latex use.
Only barely. I ditched it within a few minutes and went back to kdvi and kpdf which are fantastic. On recent versions of Ubuntu they need some additional libraries, but it's worth the effort. Unfortunately the gnomes at KDE decided to halt them and develop Okular instead, and the result is that Okular is still very raw and cumbersome: I do wish the KDE developers would try to learn from past developments instead of reinventing wheels badly.

---

### Post by hawthornso23 on 2011-07-02
These days I don't need to view dvi files. I either run pdflatex to get pdf files directly, or use latex followed by dvipdfm to generate pdf files if I want to include diagrams.

However I've just checked and evince does work for me with dvi files just fine. 

I'm not sure what problem you are having. From the error message you posted it sounds like some sort of exotic font issue.

---

### Post by r_conky on 2011-10-25
I dont know if you are still facing the problem, but you have to install evince-dvi to view dvi file in ubuntu.

---

### Post by marco1991 on 2012-03-16
I have a different problem: every time I launch Evince to open a dvi file, it gives me a segmentation fault error. I tried reinstalling it, I tried Okular but Ubuntu does not let me install it  because it says some packages to install are not safe. What can I do?

---

### Post by Helen McCall on 2012-03-18
> **cardogar said:**
> Hi friends!

I'm getting mad trying to find out why my document viewer is not able to open dvi files.

........

If I run evince in a terminal I get this:

sudo evince test.dvi

** (evince:5708): WARNING **: Failed to connect to the session bus: /bin/dbus-launch terminated abnormally without any error message

** (evince:5708): WARNING **: Error connection to DBus: /bin/dbus-launch terminated abnormally without any error message


** (evince:5708): WARNING **: Error connecting to D-Bus: /bin/dbus-launch terminated abnormally without any error message
page: Error: could not load font `cmbxti10'
page: Error: could not load font `cmbxti10'

** (evince:5708): WARNING **: Setting attribute metadata::evince::sidebar_visibility not supported

Cheers.


Why are you using sudo to launch evince? If you do that you will get all the wrong paths and so that might be causing your problems.

I am using Ubuntu 11.10 and can open dvi files with both evince and okular without any problems.

---

