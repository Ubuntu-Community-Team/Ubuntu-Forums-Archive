---
title: "Virtualbox Error NS_ERROR_FAILURE (0x80004005)"
date: 2010-10-28
forum: General Help
---

### Post by RastaManPower on 2010-10-28
hello guys after reboting my virtual machine it was not loading anymore. it was giving me this error:
Hard disk '/home/nico/.VirtualBox/HardDisks/WinXP.vdi' with UUID {e96e587f-feac-4811-ae3a-b93678fadb73} cannot be directly attached to the virtual machine 'WinXP' ('/home/nico/.VirtualBox/Machines/WinXP/WinXP.xml') because it has 1 differencing child hard disks.
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {6d9212cb-a5c0-48b7-bbc1-3fa2ba2ee6d2}


i found a way to fix this so i wanted to post it here so if it happens to somone  he can fix it.  all i did is created a new virtual machine and used the old hard disk (the *.vdi file) that you find in /home/USER/.VirtualBox/HardDisks/****.vdi
by doing this you wont lose any data on the virtual machine and everything will work as it did before.
sorry for the english, i am italian :)

---

### Post by Geek2theCore on 2011-01-15
In my case it was simple.  I had a saved machine state.  I discarded it and it loaded fine.

---

