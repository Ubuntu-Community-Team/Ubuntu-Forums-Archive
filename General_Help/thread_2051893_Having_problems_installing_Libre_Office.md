---
title: "Having problems installing Libre Office"
date: 2012-09-02
forum: General Help
---

### Post by thedoctor81877 on 2012-09-02
Hullo. I had OpenOffice installed on my machine (running Ubuntu 12.04), but now i have removed OO, and am trying to install Libre Office. However, when attempting to do so, I keep getting error messages saying that I have unmet dependencies. When I open a terminal and try 

```

apt-get -f install

```

I get the following:

```

Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a3.5.4-0ubuntu1.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help would be grateful. Thanks.

---

### Post by Gordonbp531 on 2012-09-02
Some questions - as 12.04 comes with Libre Office as default, did you uninstall LO before installing OO, and why did you install OO in preference to LO?

Secondly, from what source are you trying to re-install LO?

---

### Post by NikolaiSlenderman on 2012-09-02
As far as I know APT should handle all dependencies, so I think he's trying to install it with  a tarball.

---

### Post by rockstarrem on 2012-09-03
> **gendibal said:**
> Some questions - as 12.04 comes with Libre Office as default, did you uninstall LO before installing OO, and why did you install OO in preference to LO?

Secondly, from what source are you trying to re-install LO?

I'm not OP, but LibreOffice did not come pre-installed for me in Lubuntu 12.04.

---

### Post by 73ckn797 on 2012-09-03
> **rockstarrem said:**
> I'm not OP, but LibreOffice did not come pre-installed for me in Lubuntu 12.04.

The OP did not say they had Lubuntu. It is default in Ubuntu 12.04.

To the OP: have you selected the Ubuntu partner sources? 

From Software Center go to Edit/Software Sources/Other Software and select the Canonical Supported Free (main) and Community Maintained (universe) sources and see what happens.

You could also install Synaptic Package Manager from Software Center and install LO from there.

---

### Post by rockstarrem on 2012-09-03
I guess, but OP has lubuntu listed next to the topic...

---

### Post by 73ckn797 on 2012-09-03
> **rockstarrem said:**
> I guess, but OP has lubuntu listed next to the topic...
I have looked and do not see any reference to Lubuntu besides your comment. Unless I have drank too many beers tonight!!:guitar:

---

### Post by rockstarrem on 2012-09-03
> **73ckn797 said:**
> I have looked and do not see any reference to Lubuntu besides your comment. Unless I have drank too many beers tonight!!:guitar:

See attachment :P

---

### Post by 73ckn797 on 2012-09-04
> **rockstarrem said:**
> See attachment :P
I stand corrected. Those "l" 's can be hard to see sometimes.

However, the OP did only state: "I had OpenOffice installed on my machine (_**running Ubuntu 12.04**_)" so the lower case "l" was not noticed in the user info.

---

### Post by rockstarrem on 2012-09-04
Indeed I did notice that he said Ubuntu. Sometimes I just say Ubuntu though because more people are familiar with it and get scared when they see other flavors of it because they aren't as familiar with it. That's my interpretation at least, but who knows??

---

