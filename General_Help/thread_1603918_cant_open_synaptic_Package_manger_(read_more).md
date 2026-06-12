---
title: "cant open synaptic Package manger (read more)"
date: 2010-10-23
forum: General Help
---

### Post by asifnaz on 2010-10-23
I opend terminal and typed the command..

sudo apt-get install torcs

while downloading was in process I accidently closed the terminal
clicking X on the windows.


I cant open synaptic Package manger when I try to open it says

"This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first"

how can I close that apt-get application 

plz help me being a new user

---

### Post by mick222 on 2010-10-23
Have you tried rebooting

---

### Post by Quackers on 2010-10-23
In a terminal try 
```
sudo dpkg --configure -a
```
See if it will pick up where it left off.

---

### Post by asifnaz on 2010-10-23
Rebooting worked .Thank you guyz for your help

---

