---
title: "creating a local repository"
date: 2009-08-14
forum: General Help
---

### Post by burmanabhay88 on 2009-08-14
I read a tutorial about creating a local repository.

However when I try the fourth step: dpkg-packages
it says ```
bash: dpkg-packages: command not found
```
i tried installing dpkg-packages
it said ```
E: Couldn't find package dpkg-packages
```
I even tried dpkg -packages. but it just didn't work.
Am i missing something, or is there another tutorial for this. Ne1.


THE TUTUORIAL..........................................
Steps for creating local repository:
Step1: Create two directory structures as /Local_Repository/dists/hardy/main/binary-i386
and /Local_Repository/pool/main (You may heve any other replace ment for /Local_Repository
such as /my_sync_updates/my_repository).
Step2: Store all your debian packages in /Local_Repository/pool/main.
Step3: Now open the terminal type cd /Local_Repository
Step4: Type dpkg-packages pool/main /dev/null > Packages (/dev/null represents a
override file which contains information
about how the package fi ts into the distribution).
Step5: Type cp Packages /Local_Reposi tory/dists/hardy/main/binary-i386.
Type gzip Packages.
Type mv Packages.gz /Local_Repository/dists/hardy/main/binary-i386.
Step6: Go to System > Administration > Sof tware Sources click on Third-Party Sof tware
tab click on Add in APT line type the following deb file:///Local_Repository hardy main.
Step7: Go to System > Administration > Update Manager click Check and click Install
Updates and sit back for a while to finish up everything.

---

### Post by P4man on 2009-08-14
you're following a tutorial for hardy, and I guess you're running jaunty?

---

### Post by burmanabhay88 on 2009-08-14
I changed hardy to jaunty wherever required. Still doesn't work.

Can some1 tell me a tutorial for jaunty????

---

### Post by P4man on 2009-08-14
Can you tell us what you want to achieve?
If you have different computers running ubuntu and want to avoid downloading every app and update on each, Id suggest using apt-cache**r** (its what I use).

(edit typo: apt-cacher)

---

