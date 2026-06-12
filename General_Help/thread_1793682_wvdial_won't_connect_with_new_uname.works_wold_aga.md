---
title: "wvdial won't connect with new uname.works w/old again ..."
date: 2011-06-29
forum: General Help
---

### Post by lexrexus on 2011-06-29
Ubuntu 8.04

wvdial won't connect with new username.works w/old again ...  New umame accepted by isp windows 98 computer..  So, is there another place to change uname besides wvdial.conf???      Or something else??  

Talk computer baby-talk, please.  

If there's another place to change, why isn't it mentioned in Man wvdial?

---

### Post by lexrexus on 2011-07-12
Hello?  If there's another place to change my username to get online with wvdial, why isn't it mentioned in 'Man wvdial?'

If there is no such other place, why will wvdial work with the old username but not with the new?  

The old username will not work for much longer...

The ISP says they can't find why - its not them: I changed to the new Username with Mom's old Dell and it gets online fine.

:confused::confused::confused::confused::confused::confused::confused:

---

### Post by mali2297 on 2011-07-12
Could you give us some more information on what kind of modem you have et cetera? 

Does the ISP just use some dummy password or has that also changed? 

Can it be something simple such as wrong case in the user name? (I do not know if it matters.)

---

### Post by lexrexus on 2011-07-12
> **mali2297 said:**
> Could you give us some more information on what kind of modem you have et cetera? 

Does the ISP just use some dummy password or has that also changed? 

Can it be something simple such as wrong case in the user name? (I do not know if it matters.)

''''''''''
Thank you for replying!

Pword is the same,  and works again when I switch uname back to the old one without touching the password.

I have gone over the uname and switched back and forth between old and new several times - and with the isp on the phone, too.

Modem works with old uname, sounds like it works w/new, but isp can't accept the new uname - is there something in ubuntu linux that checks the uname from wvdial.conf and changes it or something....?????????
Again, new uname change successful in Mom's old win98 dell.

Help?:o

---

### Post by lexrexus on 2011-07-13
Hello???

---

### Post by mali2297 on 2011-07-13
If you want to check if your old user name is set in some other configuration file, you could recursively search /etc with grep. Command:
```

sudo grep -r oldusername /etc

```
This will list all occurences of oldusername in any file under /etc and its subdirectories.

As a last resort, you could try some other tool like Network Manager or configure pppd directly.

---

### Post by lexrexus on 2011-07-13
> **mali2297 said:**
> If you want to check if your old user name is set in some other configuration file, you could recursively search /etc with grep. Command:
```

sudo grep -r oldusername /etc

```
This will list all occurences of oldusername in any file under /etc and its subdirectories.

As a last resort, you could try some other tool like Network Manager or configure pppd directly.

=============
Thanks for the reply:  Looks like its in 3:
ppp/paps & 2 others - will try changing there when have time and get back to let you know!    :):):)

---

### Post by lexrexus on 2011-07-13
> **lexrexus said:**
> =============
Thanks for the reply:  Looks like its in 3:
ppp/paps & 2 others - will try changing there when have time and get back to let you know!    :):):)

=========

Thanks for the reply:  Looks like its in 3:
ppp/paps & 2 others - will try changing there when have time and get back to let you know!    :):):)[/QUOTE]

That was it! I'm online with the new uname!  
For those with wvdial and ubuntu 8.04 we need change as follows to use a new uname:

jk@jk-desktop:~$ sudo nano /etc/ppp/pap-secrets

jk@jk-desktop:~$ sudo nano /etc/ppp/peers/ppp0

jk@jk-desktop:~$ sudo nano /etc/ppp/chap-secrets


Besides wvdial.conf


I didn't have a clue as to how to proceed - Thanks again:D

---

