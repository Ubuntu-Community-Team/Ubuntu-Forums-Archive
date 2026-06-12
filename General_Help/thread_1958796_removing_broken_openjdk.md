---
title: "removing broken openjdk"
date: 2012-04-14
forum: General Help
---

### Post by AVStudio on 2012-04-14
update-alternatives: error: /var/lib/dpkg/alternatives/java corrupt: line not terminated while trying to read status
dpkg: error processing openjdk-6-jre-headless (--purge):
 subprocess installed pre-removal script returned error exit status 2
Removing openjdk-7-jre-headless ...
update-alternatives: error: /var/lib/dpkg/alternatives/java corrupt: line not terminated while trying to read status
dpkg: error processing openjdk-7-jre-headless (--purge):
 subprocess installed pre-removal script returned error exit status 2
Errors were encountered while processing:
 openjdk-6-jre-headless
 openjdk-7-jre-headless
E: Sub-process /usr/bin/dpkg returned an error code (1)


thats my output if i try do anything with those last two packages.  i've been using precise (12.04) since alpha and updates rolled fine till this started.  I just want Java gone I don't use it.  Right now all packages relating to java are gone except these two packages no amount of solving the dependences and purging gets rid of these.  I tried update-java-alternatives but no success.

---

