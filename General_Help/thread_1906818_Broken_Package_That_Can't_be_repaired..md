---
title: "Broken Package That Can't be repaired."
date: 2012-01-10
forum: General Help
---

### Post by Elie-M on 2012-01-10
```
elie-m@elie-m:~$ sudo apt-get purge plymouth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2.2-common : Depends: procps but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

Plymouth switched to fallback text mode and I wanted to purge it and reinstall, that's the error I get. I installed both packages responsible for the errors, both installed normally and the problem continued.

I did clean, autoclean, autoremove, update, upgrade, dist-upgrade, -f install, nothing solved it and it doesnt even give me there's an error.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

no broken packages in synaptic too.

it's driving me crazy bcz I dont like to have anything broken and not working in my system.. any ideas?

---

