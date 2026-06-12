---
title: "aptitude question"
date: 2010-10-27
forum: General Help
---

### Post by eli_12345 on 2010-10-27
Hi,

i hope this is the right place to ask my question:

I'm kinda new to Linux and need to install all octave-forge packages on some Ubuntu systems (octave-forge provides some extra packages to the mathematical software octave). Unfortunately for Debian Linux "apt-get install octave-forge" does not work because aptitude "Couldn't find package octave-forge". 

There is only an command available to get a list of the packages i need:
aptitude search ?description\(octave-forge\) 

Is there a way to make aptitude install these packages (maybe via pipe and grep...)? I want to avoid installing them manually because the stuff has to be installed on several machines.

Cheers,
Eli

---

### Post by fibrebiz on 2010-10-27
Maybe Aptitude doesn't have the requisite repository for these packages?

---

### Post by sisco311 on 2010-10-27
I would use awk instead of grep ;), try something like:
```
sudo aptitude install $(aptitude search ?description\(octave-forge\) | awk '{print $2}')
```

---

### Post by dasan on 2010-10-27
If you got all the packages you can make a repository of your own and after adding that repository you can install it by apt-get install

---

### Post by eli_12345 on 2010-10-27
thank you for the quick help... awk solved the problem :)

---

### Post by WorMzy on 2010-10-27
That package exists for Dapper, so I fear that the tutorial is out-of-date. If the author is contactable you could ask him/her to update it for Lucid/Maverick so others don't run into this problem.

---

