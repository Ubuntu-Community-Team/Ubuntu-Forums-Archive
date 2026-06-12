---
title: "Gimme the command"
date: 2010-04-14
forum: General Help
---

### Post by akash.yakovsky on 2010-04-14
Wanna install samba server on my Ubuntu 9.10 via Terminal through either apt-get or aptitude... can you gimme the precise command ???

---

### Post by philinux on 2010-04-14
> **akash.yakovsky said:**
> Wanna install samba server on my Ubuntu 9.10 via Terminal through either apt-get or aptitude... can you gimme the precise command ???

I think you need samba-client and samba-common.

```
aptitude search samba-
p   libsamba-hostconfig-dev                                   - Samba host configuration library - development files                
p   libsamba-hostconfig0                                      - Samba host configuration library                                    
p   libsamba-util-dev                                         - Samba utility function library - development files                  
p   libsamba-util0                                            - Samba utility function library                                      
v   samba-client                                              -                                                                     
i   samba-common                                              - common files used by both the Samba server and client               
i   samba-common-bin                                          - common files used by both the Samba server and client               
p   samba-dbg                                                 - Samba debugging symbols                                             
p   samba-doc                                                 - Samba documentation                                                 
p   samba-doc-pdf                                             - Samba documentation in PDF format                                   
p   samba-ldb-tools                                           - LDAP-like embedded database - tools                                 
p   samba-tools                                               - Samba testing utilities    
```

---

### Post by 98cwitr on 2010-04-14
^^^haha

sudo apt-get install samba*

that will install everything samba ;)

---

### Post by akash.yakovsky on 2010-04-14
my basic intension is to host a few files of music on my network, so as to make them available to other users running Windows..

---

### Post by new_tolinux on 2010-04-14
> **akash.yakovsky said:**
> my basic intension is to host a few files of music on my network, so as to make them available to other users running Windows..
Then I suggest (reading from philinux)
```
sudo apt-get install samba-client samba-common
```Although 98cwitr is absolutely right. This is mentioned 1000s of times on different results you'll get with Google.

---

### Post by Elfy on 2010-04-14
While using google or any of the specific ubuntu search engines is indeed a good idea, posting only that or lmgtfy is not acceptable - from the CoC

> Try to avoid acronyms and jargon when giving instructions. New, or "green" users may not be able to follow you, and many will not ask you for an explanation in order to avoid looking stupid. RTFM, "Go look on google" are two inappropriate responses to a question. If you don't know the answer or don't wish to help, please say nothing instead of brushing off someone's question. Politely showing someone how you searched or obtained the answer to a question is acceptable, even encouraged.

---

### Post by akash.yakovsky on 2010-04-20
thank you, i installed Samba..

but when i tried to share a folder, here i got an error msg like this:
------
Samba's testparm returned error 1: Loaded smb config files from --parameter-name=usershare allow guests
lp_load: refreshing parameters from --parameter-name=usershare allow guests
params.c:OpenConfFile() - Unable to open configuration file "--parameter-name=usershare allow guests":
	No such file or directory
Error loading services.
------
can you help me solve this issue ???

thank you all..

---

