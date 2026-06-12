---
title: "Help downgrading libc6"
date: 2012-02-21
forum: General Help
---

### Post by psycho_killer on 2012-02-21
I was fooling around with installing the qt toolkit for python3 and ipython3 (unsuccessfully) and appear to have messed up my package dependencies.  

I have libc6 2.15-0ubuntu2 installed (the Precise version) but apparently it breaks five other packages.

This is the output of 

```
sudo apt-get -f install
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libc-dev-bin : Depends: libc6 (< 2.14) but 2.15-0ubuntu2 is installed
 libc6 : Depends: libc-bin (= 2.15-0ubuntu2)
         Breaks: libc6:i386 (!= 2.15-0ubuntu2) but 2.13-20ubuntu5 is installed
 libc6:i386 : Breaks: libc6 (!= 2.13-20ubuntu5) but 2.15-0ubuntu2 is installed
 libc6-dev : Depends: libc6 (= 2.13-20ubuntu5) but 2.15-0ubuntu2 is installed
 libc6-i386 : Depends: libc6 (= 2.13-20ubuntu5) but 2.15-0ubuntu2 is installed
 libnih1 : Depends: libc6 (< 2.14) but 2.15-0ubuntu2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```


This is what happens when I try forcing the version through synaptic or running:

```
sudo apt-get install libc6=2.13-20ubuntu5
```

```
dpkg: warning: downgrading libc6 from 2.15-0ubuntu2 to 2.13-20ubuntu5.
(Reading database ... 354374 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu2 (using .../libc6_2.13-20ubuntu5_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.13-20ubuntu5_amd64.deb (--unpack):
 './usr/share/doc/libc6/FAQ.gz' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.13-20ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I'm using Ubuntu 11.10 amd64.  Can anyone please help?

---

### Post by psycho_killer on 2012-02-23
Does anyone have any ideas?  I'd hate to have to reinstall my entire system over this...

---

### Post by raja.genupula on 2012-02-23
```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get install -f

```
and then try again . 

all the best and let us know what you got .

---

### Post by psycho_killer on 2012-02-23
> **raja.genupula said:**
> ```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get install -f

```and then try again . 

all the best and let us know what you got .

Thank you, but autoremove gives me the same error message as sudo apt-get -f install, even if I use -f.

```
sudo apt-get -f autoremove

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libc-dev-bin : Depends: libc6 (< 2.14) but 2.15-0ubuntu2 is installed
 libc6 : Depends: libc-bin (= 2.15-0ubuntu2)
         Breaks: libc6:i386 (!= 2.15-0ubuntu2) but 2.13-20ubuntu5 is installed
 libc6:i386 : Breaks: libc6 (!= 2.13-20ubuntu5) but 2.15-0ubuntu2 is installed
 libc6-dev : Depends: libc6 (= 2.13-20ubuntu5) but 2.15-0ubuntu2 is installed
 libc6-i386 : Depends: libc6 (= 2.13-20ubuntu5) but 2.15-0ubuntu2 is installed
 libnih1 : Depends: libc6 (< 2.14) but 2.15-0ubuntu2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

---

### Post by raja.genupula on 2012-02-23
please do them as i mention to you , :)

---

### Post by psycho_killer on 2012-02-23
> **raja.genupula said:**
> please do them as i mention to you , :)

I did. Autoclean gives no output, autoremove gives the above output, and then install gives the output in the first post.

---

### Post by raja.genupula on 2012-02-23
* open synaptic and uninstall that current version of lib6 
 * ```
sudo rm /var/cache/apt/archives/libc6_2.13-20ubuntu5_amd64.deb
```

do that and then now try downgrade of lib pkg . 

all the best and let us know what you got .

---

### Post by psycho_killer on 2012-02-23
> **raja.genupula said:**
> * open synaptic and uninstall that current version of lib6 
 * ```
sudo rm /var/cache/apt/archives/libc6_2.13-20ubuntu5_amd64.deb
```do that and then now try downgrade of lib pkg . 

all the best and let us know what you got .

I'm not sure exactly what you mean - I can't uninstall the current version (2.15) of libc6 because half of the rest of the packages in my system depend on it.  Running the code you provided to remove the older version (2.13) has no effect - I get the same error messages as before.

---

### Post by raja.genupula on 2012-02-23
```
my system depend on it.
```
so if we downgrade lib , may be remaining all apps whose depends on it will face dependencies issue .

---

### Post by iponeverything on 2012-02-23
try this:

```
sudo mv /usr/share/doc/libc6/FAQ.gz /root
```

then rerun

```
sudo apt-get install libc6=2.13-20ubuntu5
```

---

### Post by psycho_killer on 2012-02-23
> **iponeverything said:**
> try this:

```
sudo mv /usr/share/doc/libc6/FAQ.gz /root
```then rerun

```
sudo apt-get install libc6=2.13-20ubuntu5
```

Yeah, I had that thought as well - but moving that file just causes an error with another, and so on.

---

