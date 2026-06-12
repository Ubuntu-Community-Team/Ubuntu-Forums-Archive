---
title: "Apt-Get Question"
date: 2010-02-16
forum: General Help
---

### Post by dennismonsewicz on 2010-02-16
On my Ubuntu box at home I have available more items to install via apt-get than a server I have in the cloud...

Home Ubuntu Box Version:
9.10

Cloud Ubuntu Box:
8.04.2

I have done the apt-get update and still cannot find the particular package I am looking for

I am trying to install the libdmtx library

Any suggestions?

---

### Post by snowpine on 2010-02-16
packages.ubuntu.com is a great resource:

[http://packages.ubuntu.com/search?keywords=libdmtx&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=libdmtx&searchon=names&suite=karmic&section=all)

---

### Post by mcduck on 2010-02-16
I tried a search on that in packages.ubuntu.com, and it seems to only be avalable in 9.04 and later. Of course you could try cheking the Backports-repository, I found some messages asking for the package to be backported to older Ubuntu versions. Or, if that fails, you could either try installing the package made for 9.04, it might work just fine if there's no depndency problems...

---

### Post by dennismonsewicz on 2010-02-17
Thanks for the suggestions! I got it working! I was able to download the packages from the debian website and everything working like a charm!

---

