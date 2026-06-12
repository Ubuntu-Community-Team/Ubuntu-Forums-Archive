---
title: "Eclipse PDT setup"
date: 2011-06-23
forum: General Help
---

### Post by lykkeligal on 2011-06-23
Using Eclipse PDT I try to set workspace as a folder in opt/lampp/htdocs but the error message says that .metadata file is read-only and I cannot set the folder. Where is .metadata in the htdocs folder and what does it do?

---

### Post by Azdour on 2011-06-24
Hi,

The .metadata is created by Eclipse when you set up a workspace. I have a feeling that 'opt/lampp/htdocs' has read-only permissions and Eclipse needs r/w to the .metadata directory.

---

