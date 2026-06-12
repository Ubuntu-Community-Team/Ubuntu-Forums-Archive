---
title: "ibm_lotus_notes_fixpack-8.5.2.i586.deb : invalid character in revision number."
date: 2011-05-04
forum: General Help
---

### Post by pivert on 2011-05-04
Impossible to install the Lotus Notes 8.5.2 FP2

```

root@westvleteren:~# dpkg -i ibm_lotus_notes_fixpack-8.5.2.i586.deb
dpkg: error processing ibm_lotus_notes_fixpack-8.5.2.i586.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 2 package 'ibm-lotus-notes-fixpack':
 error in Version string '8.5.2-20110323.0837_FP2': invalid character in revision number
Errors were encountered while processing:
 ibm_lotus_notes_fixpack-8.5.2.i586.deb
root@westvleteren:~# 

```

---

### Post by lodopidolo on 2011-05-19
Solution:

[http://www-10.lotus.com/ldd/nd85forum.nsf/c6054cf2ea498b338525733900559bd1/4864ef72b45dd6108525785b000c7662?OpenDocument]("http://www-10.lotus.com/ldd/nd85forum.nsf/c6054cf2ea498b338525733900559bd1/4864ef72b45dd6108525785b000c7662?OpenDocument")

```

Solution: So, open the .deb with archive manager and extract it to a directory “ibm_lotus_notes_fixpack-8.5.1.i586&#8243;.  In this directory, navigate into the DEBIAN folder and edit all files, replacing 8.5.1-20100726.1445_FP4 with 8.5.1-20100726.1445FP4 (edit out the _).  Then navigate to /opt/ibm/lotus/notes/ in the same directory and rename the directory there in the same way.

Then in the parent directory build a new .deb:

dpkg-deb –-build ibm_lotus_notes_fixpack-8.5.1.i586/

Then install the new .deb 

```

---

