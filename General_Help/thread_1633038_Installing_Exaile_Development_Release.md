---
title: "Installing Exaile Development Release"
date: 2010-11-28
forum: General Help
---

### Post by RastaManPower on 2010-11-28
hello everyone i am trying to install the exaile developmente release. i went to the exaile webpage and followed this instructions:

Bazaar

If you wish to download the latest development code, you can type the following:

```
bzr checkout lp:exaile

```
and to update it:

```
bzr update
```

i have tryed the first command and i am getting an error saying:

nico@nico:~$ bzr checkout lp:exaile

You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".

```

```
what am i supposed to do

EDIT: have tryed this but still no luck :
 nico@nico:~$ bzr launchpad-login nico*****
bzr: ERROR: The user nico***** has not registered any SSH keys with Launchpad.
See <https://launchpad.net/people/+me>

nico@nico:~$ bzr launchpad-login [email]****@gmail.com[/email]
bzr: ERROR: The user name ******@gmail.com is not registered on Launchpad.   
nico@nico:~$

EDIT 2:
i went past the first error by registering the ssh key. but now the second command gives me this output

> nico@nico:~$ bzr update
bzr: ERROR: Not a branch: "/home/nico/".

---

### Post by lidex on 2010-11-28
Just start over and ignore those messages. I just did that with unity. Should work fine.

---

### Post by RastaManPower on 2010-11-29
yeah i tryed and it seems wo work. thanks very much. what is unity by the way? game developing app?

---

### Post by lidex on 2010-11-30
> **RastaManPower said:**
> yeah i tryed and it seems wo work. thanks very much. what is unity by the way? game developing app?

It's the netbook version desktop shell for ubuntu. It's being made the default interface in desktop version of 11.04

---

### Post by RastaManPower on 2010-12-01
thats is the main reason why i deleted ubuntu netbook from my netbook and installed ubuntu desktop. i hate that layout

---

