---
title: "Update Java version from v. 6.20 to 6.23"
date: 2010-12-14
forum: General Help
---

### Post by gdiloren on 2010-12-14
There is a new java update for security. I checked my java version here: [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)
and it said I have v. 6.20 installed even after unsuccessful trial to install their linux package following their vague instructions I think I followed well. What do I do?

---

### Post by lykeion on 2010-12-14
If you don't have any problems with Java in your browser I suggest you to leave it alone.

---

### Post by oldos2er on 2010-12-14
[http://sites.google.com/site/easylinuxtipsproject/java#TOC](http://sites.google.com/site/easylinuxtipsproject/java#TOC)

---

### Post by ratcheer on 2010-12-14
> **gdiloren said:**
> There is a new java update for security. I checked my java version here: [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)
and it said I have v. 6.20 installed even after unsuccessful trial to install their linux package following their vague instructions I think I followed well. What do I do?

What? I just downloaded and installed it, this morning, and got 6.22. Has it changed again, already?

Tim

---

### Post by gdiloren on 2010-12-15
> **oldos2er said:**
> [http://sites.google.com/site/easylinuxtipsproject/java#TOC](http://sites.google.com/site/easylinuxtipsproject/java#TOC)
I updated from version 6.22 to new 6.23 correcting where needed for version 23. Many thanks. It worked. Only sad it takes MOONS to get an automatic update from the repositories for Maverick and you have to go MANUAL to increase your security setups.
Thanks

---

### Post by oldos2er on 2010-12-15
You're welcome.

---

### Post by lykeion on 2010-12-15
Just to make things clear (quoted from the [release notes]("http://www.oracle.com/technetwork/java/javase/6u23releasenotes-191058.html")):
"Java SE 6u23 does not contain any additional fixes for security vulnerabilities to its previous release, Java SE 6u22. 
Users who have Java SE 6u22 have the latest security fixes and do not need to upgrade to this release to be current on security fixes."

---

### Post by gdiloren on 2010-12-16
> **lykeion said:**
> Just to make things clear (quoted from the [release notes]("http://www.oracle.com/technetwork/java/javase/6u23releasenotes-191058.html")):
"Java SE 6u23 does not contain any additional fixes for security vulnerabilities to its previous release, Java SE 6u22. 
Users who have Java SE 6u22 have the latest security fixes and do not need to upgrade to this release to be current on security fixes."
I disagree! Something is missing for Java and Security updates and Linux as it does not alert you about important updates. I had version 6u20 before checking it on the URL of the first thread and although 6u22 is available through Synaptic Manager the common Linux user is not aware of that change and still runs 6u20, so I am asking for somekind of automatic update for Java in the near future as we actually have with Windows with justcheck.exe. Anyway, your reply means that Linux still takes correctly in consideration this important aspect as Security but there is a GAP. Thanks;)

---

### Post by lykeion on 2010-12-16
I only quoted from Oracle's release notes for their v6u23 release, so I can't tell what you disagree with.

And why 6u20 is not automatically updated to 6u22 is because they are different versions of Java (open-source vs proprietary), 
even though the java.com test page doesn't tell you so.
6u20 -> [OpenJDK JRE](http://en.wikipedia.org/wiki/Openjdk) open-source
6u22 -> [Sun Java JRE](http://en.wikipedia.org/wiki/Java_SE) proprietary

---

