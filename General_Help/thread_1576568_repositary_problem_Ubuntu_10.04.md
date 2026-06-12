---
title: "repositary problem Ubuntu 10.04"
date: 2010-09-17
forum: General Help
---

### Post by tony044 on 2010-09-17
[B]When I try to use Synaptic package manager I get the following message:
E: Type'2' is not known on line1 in source.list E: the list of sources could not be read. Go to the repositary dialog to correct the problem.E:_cache-> open() failed, Please report.
I cannot use Synaptic package manager or Update manager while this problem exists and am at a complete loss on how to resolve the problem, any help will be gratefully received Thanks in advance.

Dell inspiron 6400
ram: 2gb
hdd: 250gb
os: ubuntu 10.04
Tony044

[/B]

---

### Post by plucky on 2010-09-17
> **tony044 said:**
> [B]When I try to use Synaptic package manager I get the following message:
E: Type'2' is not known on line1 in source.list E: the list of sources could not be read. Go to the repositary dialog to correct the problem.E:_cache-> open() failed, Please report.
I cannot use Synaptic package manager or Update manager while this problem exists and am at a complete loss on how to resolve the problem, any help will be gratefully received Thanks in advance.

Dell inspiron 6400
ram: 2gb
hdd: 250gb
os: ubuntu 10.04
Tony044

[/B]


Post output from a terminal for ```
cat /etc/apt/sources.list
```

---

