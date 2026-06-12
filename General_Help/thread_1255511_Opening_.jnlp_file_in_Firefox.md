---
title: "Opening .jnlp file in Firefox"
date: 2009-09-01
forum: General Help
---

### Post by boondocks on 2009-09-01
I am trying to help my cousin setup his Ubuntu system.  He is trying to access his online college course.  The basic Java package was already installed.  Please look at the attached screenshot.  The "ClassLive.jnlp" needs an application.  What should we do?  Is there a specific package that needs to be installed?

---

### Post by jonobr on 2009-09-01
Hello


I think this may be an old issue related to Java version.

The java versions prior to 1.4 did not know what to do with this type of file,
I think 1.5 does,

You can find your version using 
```
java -version
```

According to [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/119175") the final post indicates an issue with 1.6 also

---

