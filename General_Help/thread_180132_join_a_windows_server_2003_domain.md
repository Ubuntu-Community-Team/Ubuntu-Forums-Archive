---
title: "join a windows server 2003 domain"
date: 2006-05-21
forum: General Help
---

### Post by Robgould on 2006-05-21
I am trying to join my 5.10 ubuntu to my server 2003 domain at work.  I am trying to use [SADMS]("http://sadms.sourceforge.net/").  It is asking me for some information that I am just not sure how to find. 

I need to know how to find my:

1.  kdc - kerberos domain controller name
2. netbios domain name
3. netbios server name

I need to get this info from my server 2003 box, but have no idea how.   

Can anyone help me?  Networking is a new thing for me.

---

### Post by Robgould on 2006-05-22
Nobody?

---

### Post by Robgould on 2006-05-23
ok...last bump.  Can anyone help me here?

---

### Post by gumbald on 2006-05-23
Netbios names should be the Windows names surely? Providing they conform...

I've never joined to a domain but would be interested to know how, is there a guide anywhere?

---

### Post by Robgould on 2006-05-30
I did it the easy way.  I installed suse 10.1.  It allows you to join a domain during the install.  It even autodetects that available domains.  All you have to do is select the domain name and provide credentials.  Now that is something that just works.

---

### Post by Abhi Kalyan on 2006-10-20
This is exactly what i have been trying to find, no answers yet.
Triend places
but done know how to use:
places connect to server
  server type windows share
  ??? this could have some value if some one could help out on how to use this are?

---

### Post by twistedtwig on 2006-10-20
i am also looking into this at the mo, but as yet found nothing... fingers crossed someone knows :)

i would think it has something to do with samba but dont know

---

### Post by twistedtwig on 2006-10-20
just found this thread.. if your talking active directory then this may help, (not read it fully my self yet)

[http://ubuntuforums.org/showthread.php?t=280007](http://ubuntuforums.org/showthread.php?t=280007)

which has a link to 

[https://help.ubuntu.com/ubuntu/serve...ing-samba.html](https://help.ubuntu.com/ubuntu/serve...ing-samba.html)

Twiggy

---

### Post by Abhi Kalyan on 2006-10-25
Great Twistedtwig,
checking out the links right away, hope it works,
Will post back as and when a solution arises

---

