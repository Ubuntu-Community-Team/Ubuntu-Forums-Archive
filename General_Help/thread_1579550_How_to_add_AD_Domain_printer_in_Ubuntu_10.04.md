---
title: "How to add AD Domain printer in Ubuntu 10.04"
date: 2010-09-22
forum: General Help
---

### Post by qakiudldu on 2010-09-22
Using Ubuntu 10.04

I am trying to use the network printers shared within my University's AD domain. 
In Windows XP, I simply went to 'run' and typed "\\[domain]", then it asked for my ID and passwords and list of printers came up from which I could just pick and add to my printer list. How can this be achieved in Ubuntu 10.04? 

What I tried: 
System->Administration->printing->Add->Network Printer -> Windows printer via Samba -> Browse, then I see the domain but when I input my id, domain name and password, access is denied...

Any help would be appreciated. 
Thanks, BFD

---

### Post by robsoles on 2010-09-22
Can you open file shares from the domain using your Ubuntu PC?

---

### Post by qakiudldu on 2010-09-23
> **robsoles said:**
> Can you open file shares from the domain using your Ubuntu PC?

No I cannot.

---

### Post by robsoles on 2010-09-23
When you open 'places'->'network', what is in the file-browser window that opens?

(you might need to 'sudo apt-get install smbfs' or something, although I haven't had to from vanilla installs of Ubuntu for at least a wee while now.)

---

### Post by qakiudldu on 2010-09-23
I see a bunch of computers, and at the bottom there is a folder called 'windows network'. When I double click on that, I see the domain name as another folder. When I double click on the domain, it asks me for my user name and domain name and password, but I cannot go pass this stage... keeps asking me again and again. 

I input the credentials as this:
username
domain.com
passwd

Perhaps my grammar is wrong? 
Cheers, Q

---

### Post by robsoles on 2010-09-23
The domain name as given by the file-browser should suffice in the domain box. You can afford to tell us your right username and the right domain name but of course password should be omitted or converted to ****** (and as precaution if showing '****' don't use same number of asterisk as characters in your password!).

You notate 'domain.com' as the domain name you use, are you using exactly the domain name as given by file-browser at previous step?

---

