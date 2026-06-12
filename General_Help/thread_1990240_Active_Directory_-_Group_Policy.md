---
title: "Active Directory - Group Policy"
date: 2012-05-29
forum: General Help
---

### Post by huzefa_from_kuwait on 2012-05-29
Hello experts,

I would like to switch my current Win2k3 Active Directory to be linux based, unfortunately the clients would still be infected with Windows 7. The current setup has a set of group policies like disabled cmd, hidden CP etc.

So does someone have experience in this how can I migrate the DC to be linux based.

I read about Samba4 can do all these but can I install it parallel to the current setup, migrate the AD objects and take off the Win DC, or do I need to create a completely new Domain on the Linux DC and migrate the clients to the new domain?

My basic requirements are centralized authentication, group policy, LDAP server and DNS.

Open LDAP and Bind, I suppose can handle the last two.

Also in the future we need to switch all client machines to Ubuntu, so I need some Linux DC that can also handle Ubuntu Clients.

If anyone has implemented such a scenario in the past, kindly share your experiences and problem you faced during such migration.

Thanks.

---

### Post by Cheesemill on 2012-05-29
If you need to use group policy for Windows clients then you have to stick with a Windows DC I'm afraid.

There is commercial software available to control Linux machines using group policy, but it still requires running a Windows server as your DC.

Edit - It looks like you're correct about the new Samba4 being able to act as a group policy controller, follow the documentation here:
[http://wiki.samba.org/index.php/Main_Page](http://wiki.samba.org/index.php/Main_Page)

---

### Post by huzefa_from_kuwait on 2012-06-04
Thanks for the reply, but despite the documentation I would like to know if someone implemented it successfully. 

My requirement is to setup Samba 4 as an additional DC, sync both of them, make the Samba4 DC as default, and take out the Windows DC forever to make the whole network work on Samba4 DC.

Please share your experiences.

Thanks.

---

### Post by huzefa_from_kuwait on 2012-08-01
Hello People,

I have successfully installed Samba and configured replication. Its replicated, LDAP works, GPO works fine too.

Also I transferred DNS from Win2003 to Bind9 , zone is transferred and the local DNS entries get successfully resolved via Bind9 now.

I just have one problem that Bind9 wont forward the internet requests to the ISP's DNS server.

dig @ISP.DNS.SERVER google.com gets me the correct A records so connection issues are not there.

I added the forwarders entry in the named.conf.options file but still it wont forward.

Any thing else I can check.

Thanks.

---

