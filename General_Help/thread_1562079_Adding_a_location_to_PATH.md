---
title: "Adding a location to PATH"
date: 2010-08-27
forum: General Help
---

### Post by fterh on 2010-08-27
From Android.com's Quick Start guide,

> Select a starter package from the table at the top of this page and download it to your development computer. To install the SDK, simply unpack the starter package to a safe location and then add the location to your PATH.

How do I add a location to PATH?

---

### Post by lmarmisa on 2010-08-27
Edit the file **.bash_profile** located in your $HOME directory and add a new line similar to this:

> 
PATH=$PATH:/pathtothenewlocation


---

