---
title: "Could not initialize the package information!!!"
date: 2010-11-04
forum: General Help
---

### Post by binarylife on 2010-11-04
hi,When I open update manager, or sudo apt-get update 
it gives me this fatal error .. I've removed all other software sources ! but still the same problem,... :


could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/awn-testing-ppa-maverick.list'


I can't also open  software center, synaptic.
also it gives me this afterward 
:
E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/awn-testing-ppa-maverick.list
E: Unable to lock the list directory

and : 
E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/awn-testing-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


 I think its for avant windows navigator .

---

### Post by oldos2er on 2010-11-04
Looks like you've got a typo there. Can you post the output of **cat /etc/apt/sources.list.d/awn-testing-ppa-maverick.list** ?

---

### Post by binarylife on 2010-11-04
> **oldos2er said:**
> Looks like you've got a typo there. Can you post the output of **cat /etc/apt/sources.list.d/awn-testing-ppa-maverick.list** ?

```
tarek@SlimShady:~$ cat /etc/apt/sources.list.d/awn-testing-ppa-maverick.list
ain
tarek@SlimShady:~$ 


```

what does ain mean ?

---

### Post by oldos2er on 2010-11-04
Means nothing that I'm aware of. I would remove that file and then update your sources. ```
sudo rm /etc/apt/sources.list.d/awn-testing-ppa-maverick.list 
sudo apt-get update
```

If you go to [https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa) and click 'Technical details about this PPA' you'll find instructions on adding it.

---

### Post by binarylife on 2010-11-05
> **oldos2er said:**
> Means nothing that I'm aware of. I would remove that file and then update your sources. ```
sudo rm /etc/apt/sources.list.d/awn-testing-ppa-maverick.list 
sudo apt-get update
```

If you go to [https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa) and click 'Technical details about this PPA' you'll find instructions on adding it.

Wow , that worked ! 
You saved my life man :) 
thanks a lot !!

---

### Post by oldos2er on 2010-11-05
You're welcome. Enjoy Ubuntu!

---

### Post by binarylife on 2010-11-05
> **oldos2er said:**
> You're welcome. Enjoy Ubuntu!

Sure I will , I am in love with it !! lol

---

### Post by nirmal3326 on 2010-11-13
thanx buddy for your valuable input

same issue happened to me with chromium- daily..

i used the same remove file command  and  got my update manager going

regards
nirmal

---

### Post by binarylife on 2010-11-13
> **nirmal3326 said:**
> thanx buddy for your valuable input

same issue happened to me with chromium- daily..

i used the same remove file command  and  got my update manager going

regards
nirmal

We are welcome , enjoy Ubuntu  : )

---

