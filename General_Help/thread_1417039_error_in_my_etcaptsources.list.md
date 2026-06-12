---
title: "error in my /etc/apt/sources.list"
date: 2010-02-26
forum: General Help
---

### Post by megahost on 2010-02-26
I need some help I was attempting to get a better version of WINE, when something mucked it all up. So I followed instructions on WineHQ which said

first to this

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"

And yes i have Hardy Heron
then...

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

then an apt-get update

Now i get this when i try to open my Package installer

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

i did what it said and continued to get errors

---

### Post by oldos2er on 2010-02-26
Can you copy and paste the errors here? Also please post the output of **cat /etc/apt/sources.list.d/winehq.list**

---

