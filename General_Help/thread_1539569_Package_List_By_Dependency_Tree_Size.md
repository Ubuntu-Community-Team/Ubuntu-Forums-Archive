---
title: "Package List By Dependency Tree Size"
date: 2010-07-26
forum: General Help
---

### Post by Finog on 2010-07-26
When you use aptitude to install a package there's generally a listing of how much space it and its dependencies will take up after installing. When removing packages, unnecessary dependencies are calculated.

What I would like to do is to list all my packages ordered by the combined size of the dependencies. In this way, fairly small programs (kstar, for instance) would show up somewhere near the top because of their immediate dependencies (kstars-data, for instance) and indirect dependencies (the entire KDE library).

In the KStars example, the program takes ~3,700k, the data 20.1MB, and the KDE library dependencies with this about 266MB. If I had to choose one program to remove based on size alone, this is the sort of program I could pick, if I could identify it. (Nothing against KStars.)

---

