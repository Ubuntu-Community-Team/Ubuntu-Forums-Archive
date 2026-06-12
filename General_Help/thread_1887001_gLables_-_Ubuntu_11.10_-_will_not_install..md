---
title: "gLables - Ubuntu 11.10 - will not install."
date: 2011-11-26
forum: General Help
---

### Post by M!SF!TS on 2011-11-26
I am trying to install gLabels on Ubuntu 11.10 but am having a issue.
I google searched and searched here but have been unable to find a solution.

If someone could help I would be very thankful :)
-------------------------------------------------------------------

When trying to install by Terminal I get this:

```
~$ sudo apt-get install glabels
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 glabels : Depends: libebook1.2-10 but it is not installable
E: Unable to correct problems, you have held broken packages.
```

And when I try to install it with Ubuntu Software Center
I get a error that pops up and say's this:

------------------------------------------------------------------------------
**Package dependencies cannot be resolved**
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

>Details
The following packages have unmet dependencies:

glabels: Depends: libebook1.2-10 but it is not going to be installed
------------------------------------------------------------------------------


If someone knows how to correct this. I would be a very happy human if you would tell :)

---

### Post by BC59 on 2011-11-26
Did you do a

```
sudo dpkg --configure -a
sudo apt-get -f install
```

to ensure all necessary packages are completely installed and configured?

Check through Synaptic if you have broken packages.

Then from Synaptic check the package libebook1.2-10 and try to see it's dependencies and if it's installable. If not means that this package will cause problems to your current installation.

---

### Post by M!SF!TS on 2011-11-26
BC59, Thanks for the info. I will try that in about 5 minutes after I get my morning coffee LOL! I wrote that ^ last night as I went to sleep.

I will post back my results or if I have anymore questions.
I totally appreciate your response Thank you! now lets give it a go!

---

### Post by dFlyer on 2011-11-26
I have gLabel installed here and working correctly. I installed it from the archive. Have you tried updating your system with all the current updates and security fixes for 11.10? Are you running a mixed distro install of ubuntu? What build of gLabels are you trying to install? I have 2.2.8-2build2 installed.

---

### Post by M!SF!TS on 2011-11-26
Well first thing was first I took a look at synaptic.
libebook1.2-10 is not available in synaptic. libebook1.2-12 is tho...

Q: how can I get libebook1.2-10 into synaptic?

Okay, now going to run
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by M!SF!TS on 2011-11-26
> **dFlyer said:**
> I have gLabel installed here and working correctly. I installed it from the archive. Have you tried updating your system with all the current updates and security fixes for 11.10? Are you running a mixed distro install of ubuntu? What build of gLabels are you trying to install? I have 2.2.8-2build2 installed.

I tried installing it from the archive. And I got that error.
So then I google searched it. and ran across ```
sudo apt-get install glabels
```
and that didn't work. so I came here and asked my original question. Because I am certainly not comfortable with trying to compile glabels from source.

So the version I am trying to install is the one in the ubuntu repositories. Yes. My system in up to date. always. It is the first thing I do everyday when I turn my machine on.
I am not running a mixed distro... just downloaded ubuntu 11.10 from [http://www.ubuntu.com](http://www.ubuntu.com) and installed it

---

### Post by M!SF!TS on 2011-11-26
BC59 I ran what you told me to.

```
$ sudo dpkg --configure -a
dpkg: error: dpkg status database is locked by another process

```

```
$ sudo apt-get -f install glabels
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

this was the result

---

### Post by BC59 on 2011-11-26
Try this

```
sudo rm /var/lib/dpkg/lock
```

and then again

```
sudo dpkg --configure -a
```

---

### Post by pip-le-pip on 2011-12-30
Hi,

i've got exactly the same problem and have tried what you suggest. I don't get m!sf!ts errors (i suppose he had synaptic running at the same time), but it doesn't help with the original problem.

hope someone knows how to deal with this?

cheers,
pip

---

