---
title: "Building from source and package manager dependencies"
date: 2010-12-22
forum: General Help
---

### Post by Hsiu on 2010-12-22
I couldn't find a better subcategory to put this in.

Please correct me if I'm wrong - if I build something from source, the package manager has no way of knowing and thus will falsely register and try to rectify unmet dependencies the next time I apt-get a package from the repository that depends on that which I built from source.

For example, I just built the latest version of Ruby from source I downloaded - an easy but nonetheless rewarding process. Now, however, if I were to try and apt-get install a package that required Ruby, apt would tell me I have an unmet dependency on Ruby and would offer to get the (less recent) Ruby package in the repository, correct?

If so, what can I do to rectify this?

Does the situation change any if I apt-get source the package source, instead of manually wget-ing a tarball or checking out from a remote repository?

Thank you!

---

### Post by 3Miro on 2010-12-22
This depends on how you build the package. You can compile a package and create a .deb which you can install in the regular repo-database. Then dependencies will be satisfied (i.e. apt will know about it).

I think the preferred way to get the "latest" software is via unofficial PPA.

---

