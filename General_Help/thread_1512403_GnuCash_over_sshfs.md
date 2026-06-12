---
title: "GnuCash over sshfs?"
date: 2010-06-18
forum: General Help
---

### Post by tropdoug on 2010-06-18
I use GnuCash on my desktop but want to be able to access it from my laptop. I can connect via sshfs to the program icon on my desktop but when I click it I am told I cannot do this due to security issues. 

does anyone know if its possible to get this to work?

:guitar:

---

### Post by tropdoug on 2010-06-22
well it was a simple fix really. I was trying to open the wrong sort of file. Firstly I was trying to open the program across the network rather than using the program on the local system and opening the correct data file on the remote system. 

For anyone else that is interested the file you need to find is whateveryouhavecalledyouraccounts.gz so in my case /Documents/GnuCash/dkss.gz - Ignore the plethroa of xac and other files just find this one and bob's your uncle.

Once it has been opened once the program will automatically look for it upon opening.


*NOTE you have to close the first Gnucash window that does not give you an option of opening a file, then once that has closed you can access the open file menu. *

---

