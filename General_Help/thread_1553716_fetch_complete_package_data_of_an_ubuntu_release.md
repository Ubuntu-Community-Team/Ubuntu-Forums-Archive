---
title: "fetch complete package data of an ubuntu release"
date: 2010-08-15
forum: General Help
---

### Post by sureshsaragadam on 2010-08-15
how to fetch the complete list of packages of each ubuntu release, 

  - is there is any facility so that i can fetch the list online, 

  - can i download such a file containing the complete list of packages of a release

  - any particular format is associated with such a file, if any

In-fact i wanted the complete information of a release, 
including the list of all packages, 
their versions, 
file size,
release date,
all the components..

specific information will help me a lot

---

### Post by dagdeniz on 2010-08-15
I'm not sure if you can do it for every release. However, for your release, try: 

```
apt-cache dump | less
```

or the text editor/viewer of your choice instead of less, like: 

```
apt-cache dump | gedit
```

---

### Post by sureshsaragadam on 2010-08-16
It is working here for ubuntu 

apt-cache dump > pak-list

I stored this list to a file name 'pak-list'

to my surprise this file is of size 17MB,

I may need to work with many release DATA,
Is there is any such data officially available for each release.

Any SPDX kind of file available for download for each ubntu release.

What kind of format does Ubuntu uses to submit its release data?

---

