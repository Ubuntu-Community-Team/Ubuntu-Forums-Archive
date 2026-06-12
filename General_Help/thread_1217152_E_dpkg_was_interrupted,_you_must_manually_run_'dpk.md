---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2009-07-19
forum: General Help
---

### Post by Lingonet on 2009-07-19
Hi

I get this error, after I tried to install JRE6:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
henrik@Femmansbuntu:~$
```

I get the same error when I type: ```
apt-get update
```
I can't do anything right now. What is the problem?

Thank you!

-Lingotefemmspemmsattsol

---

### Post by sisco311 on 2009-07-19
> E: dpkg was interrupted, you must manually run '**dpkg --configure -a**' to correct the problem. 
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by Lingonet on 2009-07-19
> **sisco311 said:**
> ```
sudo dpkg --configure -a
sudo apt-get update
```

OMG, it helped! It's gone!

Thank you very much Sisco! But can you tell me what the problem was? Im not aware of that.

-Lingot/Pemmsatt

---

### Post by Lingonet on 2009-07-19
Oh, and:

```
You have one broken package on your system. Use the filter 'broken'.
```

What?

Thank you!

---

### Post by balaknair on 2009-07-19
Making changes to the package management tool(apt) requires administrative privileges, which is what sudo does. Adding sudo before a command executes the command with root(admin) privileges.
That's actually a small but confusing mistake in the error message, it should read 'E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.'
I think that was corrected in Jaunty(9.04) though. 

use filter 'broken':
Open the Synaptic package manager(System menu> Administration> Synaptic), click on the 'Edit' menu in the toolbar, and select 'Fix broken packages', 
**or**
To view the 'broken packages', in the Left-hand pane in Synaptic select 'custom filters' from the list in the lower corner, and then select 'broken packages.

See the screenshots if the instructions are not clear.

---

### Post by jerome1232 on 2009-07-19
> **Lingonet said:**
> OMG, it helped! It's gone!

Thank you very much Sisco! But can you tell me what the problem was? Im not aware of that.

-Lingot/Pemmsatt

Exactly what the error said, "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"

You don't get much better errors than that.


The second issue, perhaps it means to open synaptic, click 'custom filters', then click 'broken' and you should see this broken package it's talking about and then decide what to do with it.

---

