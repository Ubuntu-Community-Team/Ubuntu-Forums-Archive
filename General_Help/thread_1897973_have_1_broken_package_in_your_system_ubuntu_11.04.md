---
title: "have 1 broken package in your system ubuntu 11.04"
date: 2011-12-20
forum: General Help
---

### Post by neelk on 2011-12-20
[SIZE=3] have 1 broken package in your system ubuntu 11.04 use brocken filter to locate it in the synaptic packet manager[/SIZE]
[SIZE=4][COLOR=black]any help thanx[/COLOR][/SIZE]

---

### Post by matt_symes on 2011-12-20
Hi

Open a terminal and type

```
sudo apt-get install -f
```

Enter your password. It will not be echoed to the screen.

Then type 

```
sudo apt-get update
```

Kind regards

---

### Post by emmomalick on 2011-12-20
Go to System > Administration > Synaptic Package Manager and click Edit > Fix Broken Packages.

or in a terminal Applications > Accessories > Terminal

```
sudo apt-get -f install
```

---

### Post by neelk on 2011-12-20
[SIZE=3]intalling stop in Configuring sun-java6-jre and falling to press ok to the agreement input keys did not work 
thank y[/SIZE]

---

### Post by matt_symes on 2011-12-20
Hi

To select <yes> use the TAB key and hit the enter.

Kind regards

---

### Post by matt_symes on 2011-12-20
Hi

To select <yes> (<ok>) use the TAB key and hit the enter.

Kind regards

---

### Post by neelk on 2011-12-20
[SIZE=3]proplem fixed turely appreciated ur help quit than i imaged
thank you so much[/SIZE]

---

