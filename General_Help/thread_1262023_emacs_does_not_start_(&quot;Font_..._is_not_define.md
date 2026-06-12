---
title: "emacs does not start (&quot;Font ... is not defined&quot;)"
date: 2009-09-09
forum: General Help
---

### Post by shahor02 on 2009-09-09
Hello,
After the recent update (Ubuntu 9.04) I am having the following problem (GNU Emacs 22.2.1):
> emacs
Font `-Adobe-Courier-Medium-R-Normal--12-120-75-75-M-70-ISO8859-1' is not defined

After checking the web I've got the hint to use: 
emacs -fn '-Adobe-Courier-Medium-R-Normal--12-120-75-75-M-70-ISO8859-1'
This allows to open the emacs, but then, if I use Ediff, I get the message in the buffer:
x-create-frame-with-faces: Font `-Misc-Fixed-Medium-R-Normal--13-120-75-75-C-80-ISO8859-1' is not defined

Also, adding to .emacs  
(set-default-font "-adobe-courier-medium-r-normal--18-180-75-75-m-110-iso8859-1")
leads to:
> emacs 
Font `-Misc-Fixed-Medium-R-Normal--15-140-75-75-C-90-ISO8859-1' is not defined

This seems be some X related problem: if I run emacs from remote ssh session, it works w/o problems.

Reinstalling emacs did not help.
The update after which I've noticed the problem is:
 Commit Log for Wed Sep  2 15:06:08 2009

Upgraded the following packages:
app-install-data-partner (11.9.04.2) to 11.9.04.4
dnsmasq-base (2.47-3) to 2.47-3ubuntu0.1
libgl1-mesa-dev (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2
libgl1-mesa-dri (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2
libgl1-mesa-glx (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2
libglu1-mesa (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2
libglu1-mesa-dev (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2
libnss3-1d (3.12.3.1-0ubuntu0.9.04.1) to 3.12.3.1-0ubuntu0.9.04.2
mesa-common-dev (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2
mesa-utils (7.4-0ubuntu3.1) to 7.4-0ubuntu3.2
python-gobject (2.16.1-1ubuntu2) to 2.16.1-1ubuntu3

Any hints?

---

