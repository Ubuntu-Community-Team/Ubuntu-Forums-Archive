---
title: "Problem with synaptic package manager"
date: 2011-05-09
forum: General Help
---

### Post by auwally on 2011-05-09
I got ahead of myself and have the following problem with synaptic package manager:

  	 	 	 	 	   	 	 	 	 	 	  E: Type 'nchpad.net/awn-testing/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/awn-testing-ppa-natty.list  
 E: The list of sources could not be read.  
 Go to the repository dialogue to correct the problem.  
 E: _cache->open() failed, please report. 


Any help much appreciated - thank you.

---

### Post by sisco311 on 2011-05-09
Please post the content of /etc/apt/sources.list.d/awn-testing-ppa-natty.list

```
cat /etc/apt/sources.list.d/awn-testing-ppa-natty.list
```

---

### Post by auwally on 2011-05-09
> **sisco311 said:**
> Please post the content of /etc/apt/sources.list.d/awn-testing-ppa-natty.list

```
cat /etc/apt/sources.list.d/awn-testing-ppa-natty.list
```

Thanks - the content is ?:

$ cat /etc/apt/sources.list.d/awn-testing-ppa-natty.list
deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) natty main #Awn Testing Team PPA
nchpad.net/awn-testing/ppa/ubuntu natty main

Is this right?

---

### Post by sisco311 on 2011-05-09
Edit the file:
```
gksu gedit /etc/apt/sources.list.d/awn-testing-ppa-natty.list
```
and replace the last line (nchpad.net/awn-testing/ppa/ubuntu natty main) with:
```
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu natty main
```

Save the file, then run:
```
sudo apt-get update
```

---

### Post by auwally on 2011-05-09
> **sisco311 said:**
> Edit the file:
```
gksu gedit /etc/apt/sources.list.d/awn-testing-ppa-natty.list
```and replace the last line (nchpad.net/awn-testing/ppa/ubuntu natty main) with:
```
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu natty main
```Save the file, then run:
```
sudo apt-get update
```

Sisco311 - Thanks very much for your time and effort it fixed my problem - I owe you a beer or two.

---

### Post by sisco311 on 2011-05-09
You are welcome!

Don't forget to mark this thread as [SOLVE].

---

