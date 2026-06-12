---
title: "Problem installing Android SDK"
date: 2012-01-08
forum: General Help
---

### Post by delogren on 2012-01-08
With a new Android smart phone hot I my hands, I started trying to set up a development environment in Ubuntu.  Java and Eclipse installed fine but when I tried to install the Android SDK in Eclipse all I got was a message that one of the files couldn't be found....

Has anyone here hit the same wall?  Or can anyone aim me at a tutorial that worked for them??

--del

---

### Post by delogren on 2012-01-08
Here's the error message I get:

Cannot complete the install because one or more required items could not be found.
  Software being installed: Android Development Tools 16.0.1.v201112150204-238534 (com.android.ide.eclipse.adt.feature.group 16.0.1.v201112150204-238534)
  Missing requirement: Android Development Tools 16.0.1.v201112150204-238534 (com.android.ide.eclipse.adt.feature.group 16.0.1.v201112150204-238534) requires 'org.eclipse.wst.sse.core 0.0.0' but it could not be found.

---

### Post by antiplex on 2012-01-13
hi,

i found a solution for this here: [http://stackoverflow.com/questions/4249695/adt-requires-org-eclipse-wst-sse-core-0-0-0-but-it-could-not-be-found](http://stackoverflow.com/questions/4249695/adt-requires-org-eclipse-wst-sse-core-0-0-0-but-it-could-not-be-found)

in brief: an eclipse update site needs to be defined so dependencies like 'org.eclipse.wst.sse.core 0.0.0' can be resolved, if you run indigo (3.7 or 3.7.1) you would use 'http://download.eclipse.org/releases/indigo'

regards,
anti

---

### Post by bluexrider on 2012-01-13
This may help [http://community.linuxmint.com/tutorial/view/603](http://community.linuxmint.com/tutorial/view/603)

---

