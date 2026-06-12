---
title: "Problems with MATLAB and uigetfile"
date: 2006-03-08
forum: General Help
---

### Post by quaxo on 2006-03-08
Hi,

I'm using MATLAB R14 SP3 on ubuntu 5.10. Everything seems to work fine, except the ui* tools. When I try to select a file in the uigetfile-dialog for example, I get a "file does not exist" error. Furthermore I can't change directories in the dialog, it simply happens nothing when clicking on them.

By the way, I already fixed the well known problem with the oscheck.sh script, so the problem can't be at this place...

Does anyone has an idea what is going wrong here? 

Thanks a lot,

quaxo

---

### Post by adamkane on 2006-03-08
Post bug to Ubuntu Bugzilla
[https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by jrb114 on 2007-02-08
I had this problem many moons ago using breezy, but on an upgrade to dapper, it went away, so I assumed it was fixed.

However, my hard drive is now knackered, so on a reinstall, the same problem as above has recurred. So I assume it's a dependency issue of some sort. Any one got any ideas? My old machine still sort of works, so I can hunt through all the packages, but there're so many no it that I'd need some bright ideas to start with.

For reference, I'm using R14 SP1.

J

---

### Post by hoogland on 2007-03-01
adding UNSET LANG to my matlab startup script did the trick for me.

ALSO SEE: [http://www.mathworks.com/support/solutions/data/1-VD2UO.html](http://www.mathworks.com/support/solutions/data/1-VD2UO.html)

---

### Post by sam81 on 2007-04-01
Try
```
 setappdata(0,'UseNativeSystemDialogs',false)
```
I got the tip from the following URL:
[http://ntmm.org/~nt/matlab]("http://ntmm.org/~nt/matlab")

---

### Post by hoogland on 2007-04-16
Possibly your problem will be solved by typing this in a startup script for matlab.

unset LANG

---

