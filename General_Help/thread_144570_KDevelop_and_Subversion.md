---
title: "KDevelop and Subversion"
date: 2006-03-14
forum: General Help
---

### Post by Arevos on 2006-03-14
I have Kubuntu Breezy with KDE 3.5, and I was wondering if anyone else had issues with KDevelop and Subversion. KDevelop is supposed to integrate with Subversion quite well, but this doesn't seem to be the case with Kubuntu.

When I try to "Sync with Repository", it throws up this unusual error:

[INDENT]The process for the svn+[http://fakeserver_this_is_normal_behavior](http://fakeserver_this_is_normal_behavior) protocol died unexpectedly.[/INDENT]

And when I try to to add a file, it throws up this:

[INDENT]The process for the svn+[http://blah](http://blah) protocol died unexpectedly.[/INDENT]

I can access Subversion find through the console, of course, and even Konqueror works smoothly with "svn://".

However, something appears to be wrong with the "svn+http://" protocol. It simply fails to connect to the process from svnserve. And KDevelop seems to default to svn+http even when I tell it to use svn.

Has anyone else had any similar issues? Is this problem fixed in Dapper?

---

### Post by RyanB on 2006-04-20
I have just run into this issue myself.  Did you ever get a resolution to the problem?

Thanks,

Ryan

---

