---
title: "Package in universe not showing up in Synaptic"
date: 2012-03-23
forum: General Help
---

### Post by Bre Ntt on 2012-03-23
Hi, I'm trying to install the package listed here:

[http://packages.ubuntu.com/precise/zathura](http://packages.ubuntu.com/precise/zathura)

According to that page, it should be in the universe. I'm pretty sure I've set packages in the universe to show up in synaptic, but for some reason this one does not show up.

I've never quite understood how synaptic works, so I might be overlooking something simple. But it seems odd that the package would be listed as being in universe on [http://packages.ubuntu.com](http://packages.ubuntu.com) but not show up in synaptic. 

As a related aside, I'm looking for a pdf viewer that has multiple bookmarking capabilities, preferably something I can install from synaptic, since I've not yet managed to have a succesful installation that was not from synaptic or apt-get, and do not have the time to figure out how to do it (I've have rather large pdfs to read!). Any suggestions? Everything I've found either does not have bookmarking capabilities or does not seem to have packages available from synaptic or apt-get.

---

### Post by duncan12 on 2012-03-23
Have you tried ```
sudo apt-get install zathura
```

---

### Post by Bre Ntt on 2012-03-23
Yes
```

sudo apt-get install zathura
[sudo] password for **...***:*...**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zathura

```

---

### Post by wildmanne39 on 2012-03-23
Hi, do you have the universe repository checked?
Thanks

---

### Post by Bre Ntt on 2012-03-24
Yes, universe is definitely enabled.

---

### Post by wildmanne39 on 2012-03-24
Hi, I think it probably has to do with which version of ubunntu you are using, I am using 11.10 and it is in the package manager.
Thanks

---

### Post by Elfy on 2012-03-24
10.10 and after it seems [http://packages.ubuntu.com/search?searchon=sourcenames&keywords=zathura](http://packages.ubuntu.com/search?searchon=sourcenames&keywords=zathura)

If you are still using the EOL Intrepid then it is not in those repos.

---

### Post by matt_symes on 2012-03-24
Hi

You can enable the universe repository from the terminal with

```
sudo sed -i '/[^#]*universe/ s/#//g' /etc/apt/sources.list
```

You can then reload the repos with

```
sudo apt-get update
```

You can check if the package is available with (from the terminal)

```
apt-cache search zathura
```

and you can install it with

```
sudo apt-get install zathura
```

However, as forstpiskie said, if you are using Interpid then you will need the old repos.

Kind regards

---

### Post by Bre Ntt on 2012-03-24
I'm 10.04 LTS, guess that's the problem.

Thank you.

---

