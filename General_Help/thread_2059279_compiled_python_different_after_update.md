---
title: "compiled python different after update"
date: 2012-09-17
forum: General Help
---

### Post by FrancisBacon on 2012-09-17
I have a few 12.04 (x86_64) boxes, which have the exact same install on them. Last week I updated gimp, python-scientific, and python-netcdf on all of these machines, and now the compiled python files (.pyc) are different on some.

By different I mean the contents of the files are different. The size is 
the same, but each file has a different checksum.

For example:
/usr/lib/python2.7/dist-packages/Scientific/NumberDict.pyc 
has the MD5 sum of: 4b6cbb2789bbab3e51a5fff8f0e901c9 on 98.9% of my machines but different on the other 1.1% (each md5 sum is different on each machine).

What's going on?

Is this a bug that I should report?

Sure, I could just copy the .pyc files from the good boxes to the bad boxes, but that's not a good solution. I want to understand what's going on so I know what to do if it happens again.

Also the differences didn't show up until a day or so after the update. Is there a behind the scenes compiling going on?

Thanks.

---

