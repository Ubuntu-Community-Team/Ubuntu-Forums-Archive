---
title: "Installing PyLucene from Sarge repo"
date: 2006-05-31
forum: General Help
---

### Post by egghead3 on 2006-05-31
I'm trying to get pylucene, a version of the Java search engine lucene integrated with python via gcj, to work in ubuntu. There is a Debian package in the sarge repo, but my attempt to apt-get it from breezy is yielding some dependency issues.

```
greg@greg-ubuntu:~$ sudo apt-get install python2.4-pylucene
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python2.4-pylucene: Depends: libgcj5 (>= 3.4.1-3) but it is not installable
E: Broken packages

```

I'm not really sure where to go from here. A quick search on libgcj in synaptic shows that I have libgcj6, not libgcj5, which does not appear in the repos. A google search found that there are apparently some discrepencies in the versions of gcc used to compile python versus pylucene, stuff I don't really know much about. 

I'd really like to be able to use lucene with python; if anyone has any suggestions or has gotten this to work, let me know.

The pylucene website is [http://pylucene.osafoundation.org/]("http://pylucene.osafoundation.org/")

---

