---
title: "Certain files ignored in disk utilization reports"
date: 2010-06-02
forum: General Help
---

### Post by latev on 2010-06-02
I'm currently scratching my head over the following situation:

I have an external 300GB Verbatim hard drive. /little guy, powered through USB/. I decided to backup my Win7 x64 installation on it, however for some strange reason it doesn't work under x64 OSs.
So I hooked it up to my Lin server, formatted it as ReiserFS and mounted it and made it available to Windows under Samba.

So far so good.

I let Windows do it's backup overnight since the transfer rates I was getting were embarrassingly low /800kb-900kb/

This morning I woke up to observe 2 very strange things:
1) Windows complained that the backup did not complete successfully because "the network share became unavailable". I was able to access it fine though

2) Several files were created on the verbatim HDD, including 1 huge >30GB file, totalling ~37 GB
Commands such as df -h under Linux however reported only less than 8gb of utilized disk space. Further investigation revealed that the huge 30+gb file for some reason gets completely ignored by df and du commands
What is the file size limit of ReiserFS under Debian stable?

Any comments, suggestions appreciated

Thanks,
TL

---

