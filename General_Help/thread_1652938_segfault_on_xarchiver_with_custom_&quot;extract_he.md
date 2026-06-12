---
title: "segfault on xarchiver with custom &quot;extract here&quot; command in nautilus with extentions"
date: 2010-12-25
forum: General Help
---

### Post by fireandspike on 2010-12-25
Hi

If you right click on an archive there is an "extract here" option provided by file roller that extracts the contents of the archive to the current directory.

I would like this facility to be provided by xarchiver instead because I want to specify a non default tmp directory for extracting files. xarchiver supports this but archivemanager/file roller does not.

I am using nautilus extentions to add a custom command to the context menu when you right click on an archive. I have got the command to appear but running it produces a segmentation fault in xarchiver. 

In Nautilus Actions Configuration Tool command tab I have xarchiver for the path and  -x %d %f for the parameters. -x being to extract option %d being current directory and %f being current file.

xarchiver -x %d %f

Here is the segfault that running this command produces from the syslog.

 1871.217615] xarchiver[2439]: segfault at 1c ip 08057254 sp bf9e3b70 error 4 in xarchiver[8048000+3c000]

if I just fire up a terminal and type 
xarchiver -x /mydirectory myarchive.zip

it extracts fine without any errors. 

So why is it screwing up when called from nautilus with command>

xarchiver -x %d %f  

command ref> [xarchiver.sourceforge.net/doc/ch03s02.html]("http://xarchiver.sourceforge.net/doc/ch03s02.html")

---

