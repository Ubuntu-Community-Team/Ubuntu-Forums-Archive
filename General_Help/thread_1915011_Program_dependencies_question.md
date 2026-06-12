---
title: "Program dependencies question"
date: 2012-01-25
forum: General Help
---

### Post by EgoGratis on 2012-01-25
I was always wondering about one thing and i decided to ask. When something is installed it lists needed dependencies that will be installed too. Is there simple way to list all dependencies that are not needed for the program to run?

Example: to run web browser you don't need office application, music and video player and a lot of libraries is there a way to list what is not needed? Thanks.

---

### Post by Mark Phelps on 2012-01-25
> **EgoGratis said:**
> Is there simple way to list all dependencies that are not needed for the program to run?

Not really.

Think about what you're asking ... there are literally tens of THOUSANDS of deb packages, and each of them comes in different versions -- and that's before you start to count ALL the PPA'a which have their own unique packages.

To list ALL packages NOT needed, you would first require a list of ALL packages -- which is really not feasible or practical.

---

### Post by EgoGratis on 2012-01-26
I was thinking only about installed packages. I did find solution apt-cache and it shows dependencies for not installed packages to.

Thanks!

---

### Post by jamesisin on 2012-02-03
Take a look in the man-page for apt-get, specifically at autoremove and autoclean.  You might find those useful.

---

