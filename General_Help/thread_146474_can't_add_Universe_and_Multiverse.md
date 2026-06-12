---
title: "can't add Universe and Multiverse?"
date: 2006-03-18
forum: General Help
---

### Post by ozkan on 2006-03-18
i am trying to add Universe and Multiverse just declared at this link : "http://help.ubuntu.com/starterguide/C/ch03s07.html" but i can't add them , i am trying to check Officially supported, Restricted copyright, Community maintained (Universe)  and Non-free (Multiverse) check boxes in the repository dialog box,  but unfortunatlly i can't save them , they always stay unchecked, how i can make them check.

---

### Post by Ramses de Norre on 2006-03-18
sudo gedit /etc/apt/sources.list
And delete all the #'s in front of lines that start with dep.

---

### Post by Moonhill on 2006-03-18
In the menu bar,

System->Administration->Synaptic Package Manager->Settings->Repositories->Settings

check 'Show disabled software sources' in the top User Interface

Then

Come back to Software Sources

And check those previously unchecked and edit them from 'universe' to 'universe multiverse'

---

### Post by aysiu on 2006-03-18
You can also do this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

