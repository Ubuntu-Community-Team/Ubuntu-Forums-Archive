---
title: "Pull dependencies of modules by refernecing parent in maven java project??"
date: 2010-11-09
forum: General Help
---

### Post by rainInSpain on 2010-11-09
I have a maven-java project (say Project A) with a parent defining modules in its pom.
I also have an external project (say Project B) that requires dependencies of two of the modules from Project A. For now, i have defined the dependency to pull each module individually. 
When i replace these two with a dependency on the parent pom, it errors out on build. Is there some modification i need to make to my parent pom of Project A to make this work?
Is it even possible???

---

