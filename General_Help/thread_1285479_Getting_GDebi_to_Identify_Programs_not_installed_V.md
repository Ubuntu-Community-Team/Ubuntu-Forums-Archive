---
title: "Getting GDebi to Identify Programs not installed VIA a Package"
date: 2009-10-07
forum: General Help
---

### Post by ZekeDragon on 2009-10-07
Forgive me if this has already been addressed and I simply couldn't find it on the forums, however, I've looked around and haven't had much luck.

A while ago, I had installed Java VIA the package manager, however I also develop with Java, and I'm used to working in NetBeans with Sun's JDK. This was rather counter-intuitive for the Package Manager since it would appear the package manager has a fierce loyalty toward Eclipse with OpenJDK and gcj for Java development. After trying in vain to get the packages to work happily with something other than OpenJDK (namely the SUN JDK), I uninstalled everything that had the word "Java" attached to it and started from scratch. This time I went ahead and simply got Sun's Java 6 from their website, and this installation was considerably less painful and more importantly I had access to the development environment and software of my preference.

Anyway, that isn't here nor there, what this post is about is getting my GDebi package manager to realize that I actually *have* a copy of the JRE, and if I install anything that requires the JRE, to not install some package as a dependency. This dependency is already fulfilled, and I'd rather it not want this all the time. Further, if I install anything that would require the JDK, I'd also like GDebi to automagically recognize that I also have the JDK, albeit it's not OpenJDK from the package manager. Is there **any** way for me to get GDebi to realize these things are there, and if so what config files will I have to modify. If not, is there a workaround or do I simply have to live with installing anything that would require the JRE from source?

Thank you for your attention and I apologize if this has already been resolved.

---

