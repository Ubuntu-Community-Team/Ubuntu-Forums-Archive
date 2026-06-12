---
title: "force version help please"
date: 2011-05-12
forum: General Help
---

### Post by maddbaron on 2011-05-12
problem: added software from a ppa i use to get up to date programs, during the update empathy was deleted. 

i went back and deleted the new software causing the conflict but empathy still won't install. 

I see there are two versions,  3.1.1.1 and the ubuntu 11.04 2.3.4 i think... i want to install the natty version but whenever I try force version it gives me an error... 

Is the solution removing the ppa? or is there a work around like downgrading back to the original software?

any help would be appreciated, thanks in advance?

---

### Post by lithopsian on 2011-05-12
It would help to see the errors you are getting?  Do you know which version you had before that was working?  Which PPA?  Is version 3.1.1.1 coming from that PPA or another PPA?

---

### Post by maddbaron on 2011-05-12
> **lithopsian said:**
> It would help to see the errors you are getting?  Do you know which version you had before that was working?  Which PPA?  Is version 3.1.1.1 coming from that PPA or another PPA?

The default version was 2.34, I wanted to go to 3.1.1.1...here is the output from terminal
```
$ sudo apt-get install empathy
[sudo] password for wordsmith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 empathy : Depends: libchamplain-0.10-0 (>= 0.9.0) but it is not installable
           Depends: libchamplain-gtk-0.10-0 (>= 0.9.0) but it is not installable
           Depends: libgck0 (>= 2.91.1) but it is not installable
           Depends: libgcr-3-0 (>= 2.91.4) but it is not installable
           Depends: libgnome-control-center1 (>= 1:2.91.2) but it is not installable
           Recommends: nautilus-sendto-empathy but it is not going to be installed
           Recommends: freedesktop-sound-theme but it is not installable
E: Broken packages

```

I am not exactly sure how it got like this, I removed the programs that caused the original removal...this is confusing

---

