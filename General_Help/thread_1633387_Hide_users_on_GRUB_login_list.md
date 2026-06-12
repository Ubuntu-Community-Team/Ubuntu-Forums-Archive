---
title: "Hide users on GRUB login list"
date: 2010-11-29
forum: General Help
---

### Post by deanoj on 2010-11-29
Hi

When you boot up Ubuntu, you are presented with the login screen, with a list of users that can access the machine.

I want to be able to only show certain users in that list, and hide others.

Is this possible?

Thanks - deanoj

---

### Post by sisco311 on 2010-11-29
Edit the /etc/gdm/gdm.schemas file and add the users to the *Exclude* list:
```

   <schema>
      <key>greeter/Exclude</key>
      <signature>s</signature>
      <default>**user1,user2,**bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap</default>
    </schema>

```

---

