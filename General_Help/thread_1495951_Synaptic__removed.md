---
title: "Synaptic  removed"
date: 2010-05-28
forum: General Help
---

### Post by msaied86 on 2010-05-28
the synaptic package manager was not opening, so i went to software package and removed it with the intention of installing it another time.

now when i install it it doesnt react , that is it is not being installed?can anybody help me

also i dont have internet connection but this is another story i put it in the dell forum.

so if i lost my synaptic package manager and i want repair my linux version with the CD how i could do this? and if there is no solution how can i install the linux?


thanks in advance

---

### Post by WorMzy on 2010-05-28
What happens when you run 'sudo apt-get install synaptic' in a terminal?

---

### Post by amite on 2010-05-28
open /etc/apt/sources.list
it will open software sources their check in Cdrom  option.Then try 
sudo apt-get update
sudo pt-get upgrade

if needed then sudo apt-get install synaptic

---

### Post by msaied86 on 2010-06-05
thanks guys it works with both now!!!

---

