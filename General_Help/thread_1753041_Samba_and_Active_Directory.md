---
title: "Samba and Active Directory"
date: 2011-05-08
forum: General Help
---

### Post by UncleBoarder on 2011-05-08
Is there a Samba forum?

Samba and active directory are harder than I thought.  I've been working on this and reading how-tos for about 3 weeks.  I have joined my computer to my domain and sucessfully read my AD users and groups.  However I have not been able to add domain user permissions to my Virtual Windows computers that are using a share provided from my Linux host.  I can READ files, and I can even write, but when I go to install an application it says I don't have permission.  So I tried to add permission and while I CAN find my AD username, when I select apply, it just disappears.

My "success" was based on Samba "security = domain".  But everything I've read says I need "security = ads".  And since I've changed to "security = ads", I've had nothing but problems.  Most I've resolved... except this one.

When I try, "net ads join -Uadmin"

I get this...

**Failed to join domain: failed to set machine spn: Operations error**

Almost everything I've found online tells me not to use Samba4... which I never even installed.  I'm stuck.

Ubuntu 10.04
Samba 3.4.7

---

