---
title: "How to remove programt that both IS and IS NOT recognized as installed?"
date: 2011-12-30
forum: General Help
---

### Post by aplonis on 2011-12-30
So I installed makehuman-alpha but it turns out I need makehuman-nightly instead. I DL and click OPEN on makehuman-nightly but installer on Oneiric says "conflicts with makehuman-alpha". So then I try to remove using the PACKAGES thingy at left but from there it appears that makehuman-alpha is not installed.

I know that's long-winded. I mainly just need to remove the 'alpha so I can install the 'nightly. I installed the 'alpha from a deb package DL'd from MakeHuman.org. Why does Oneiric not recognize that it IS installed so that I can remove it?

If I type "makehuman" into a terminal then the 'alpha insallation DOES load up and run. So Oneiric DOES know that makehuman-alpha there, simply calling it "makehuman". How can I remove that 'alpha version so as to start over with the 'nightly version? Searching the PACKAGES utility on both "makehuman" and "makehuman-alpha" turns up nothing found as being installed. Kind of makes it hard to remove.

---

### Post by matt_symes on 2011-12-30
Hi

Open a terminal and type

```
dpkg -l | grep makehuman
```

That is a small L after dpkg. Post back results.

Kind regards

---

### Post by corncob on 2011-12-30
You might try System > Administration > Computer Janitor

---

### Post by aplonis on 2011-12-30
> **matt_symes said:**
> Hi

Open a terminal and type

```
dpkg -l | grep makehuman
```

Okay, did that. I get this...

```

~$ dpkg -l | grep makehuman
ii  makehuman-alpha                        6                                       3d character modeler
~$ ^C

```

---

### Post by matt_symes on 2011-12-30
Hi

Try this. From a terminal

```
sudo dkpg -P makehuman-alpha
```

Enter your password. It will not be echoed to the screen

Kind regards

---

### Post by aplonis on 2011-12-30
> **corncob said:**
> You might try System > Administration > Computer Janitor

On my Lucid tower I'd know how to do that. But this instance is on an Oneiric laptop. I'm still a bit lost with Oneiric and fail to locate the newfangled equivalent to Computer Janitor.

---

### Post by aplonis on 2011-12-30
> **matt_symes said:**
> Hi

Try this. From a terminal

```
sudo dpkg -P makehuman-alpha
```

Enter your password. It will not be echoed to the screen

Kind regards


Thank you! After s/dkpg/dpkg/ that worked nicely.

---

