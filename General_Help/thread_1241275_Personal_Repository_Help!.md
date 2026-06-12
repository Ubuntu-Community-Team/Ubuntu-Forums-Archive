---
title: "Personal Repository Help!"
date: 2009-08-15
forum: General Help
---

### Post by jaxxstorm on 2009-08-15
Ok, I've added some debs to a repository, and I'm having a problem.

I upload the debs via scp - I've made a Packages.gz using dpkg-scanpackages and the directory on the webserver is ~/htdocs/alpha/jaunty

When I do ```
sudo apt-get update
``` it hits with no problem. However, when I try install the test package (slim 1.3.1 in this case) I get this error message

```

Err http://packages.icebuntu.com jaunty/ slim 1.3.1-0moonos1
  404 Not Found
Failed to fetch http://packages.icebuntu.com/alpha/./slim_1.3.1-0moonos1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I don't understand where this ```
/./
``` has come from. Any ideas?

Can anyone help :(

---

### Post by jaxxstorm on 2009-08-15
bump

---

### Post by jaxxstorm on 2009-08-16
?

---

