---
title: "Problem installing build-essential on 3 year old ubuntu desktop 8.04"
date: 2011-04-16
forum: General Help
---

### Post by Shwick2 on 2011-04-16
I want to start some C++ development on my 3 year old, un-updated 8.04 ubuntu desktop machine.  I tried,

sudo apt-get install build-essential

and got,

```

sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libc6-i386: Breaks: ia32-libs (< 20090804) but 2.2ubuntu11 is to be installed
              Breaks: lib32asound2 (< 1.0.20-3) but 1.0.15-3ubuntu4 is to be installed
E: Broken packages

```

I thought apt would automatically install the package dependencies.
I don't really want to update the entire installation as I have a lot of network services installed and running which I don't want to risk breaking.  
They aren't exposed to the internet and don't pose a security risk.

So is there any way to get apt to install the dependencies for build-essential?

---

### Post by Bucky Ball on 2011-04-16
8.04 LTS is no longer supported. You could try the backports but can't give you any advice on that.

10.04 LTS is the current supported long-term support release. ;)

---

### Post by Shwick2 on 2011-04-17
-tried, sudo apt-get ia32-libs, failed due to public key error
-updated public key from 2010
-did sudo apt-get update, worked :D
-did sudo apt-get install ia32-libs, worked
-did sudo apt-get install lib32asound2, worked
-did sudo apt-get install build-essential, worked

---

