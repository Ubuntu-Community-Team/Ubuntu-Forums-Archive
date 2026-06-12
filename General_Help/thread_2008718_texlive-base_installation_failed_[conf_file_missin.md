---
title: "texlive-base installation failed [conf file missing?]"
date: 2012-06-23
forum: General Help
---

### Post by phoeagon on 2012-06-23
hi!
today the texlive package on my ubuntu 11.04 has broken due to a harddisk fail. as a result i lost my configuration files.
at first whatever package related to tex/latex/texlive failed.
then, i managed to get tex-common installed fine by manually extracting default configuration file from the deb package. anyway tex-common is fine but texlive-base, texlive-binaries won't install on top of it.

i get this:------------------[INDENT]mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Building format(s) --refresh.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.DAJV0pUP
Please include this file if you report a bug.
[/INDENT]-----------------------------

the log file is below:===========[INDENT]tcfmgr: config file `tcfmgr.map' (usually in $TEXMFMAIN/texconfig) not found.
fmtutil: config file `fmtutil.cnf' not found.
[/INDENT]==========================

manually executing "kpsewhich fmtutil.cnf" doesn't yield anything. so i guess it can't find the file. then i tried:[INDENT]> kpsewhich --show-path=cnf
/usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c

>ll /usr/share/texmf/web2c
drwxr-xr-x 2 root root 4096 2012-06-23 17:19 ./
drwxr-xr-x 6 root root 4096 2012-06-23 17:07 ../
-rw-r--r-- 1 root root 1692 2012-06-23 17:19 fmtutil.cnf
......[some lines ommited]..
lrwxrwxrwx 1 root root   20 2012-06-23 17:02 texmf.cnf -> /etc/texmf/texmf.cnf

[/INDENT]and similar results for tcfmgr.map.
so now the shell tells me that the files exist, [and not a broken symbolic link], but kpsewhich doesn't find anything.

any idea?

-----------------
ubuntu 11.04, probably trying to install texlive 2009.

---

