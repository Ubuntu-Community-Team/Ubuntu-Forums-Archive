---
title: "ssh security and nx remote desktop not working"
date: 2009-10-07
forum: General Help
---

### Post by exww on 2009-10-07
Im using access.conf to limit user access only to certain IP's on ssh.
It works great on putty but it wont work with NX
the rules are like this:

to allow access
+ : user : IPHERE
and to deny access from all other sources
- : user : ALL

When i try to login with NX it says authentication failed for user

---

### Post by t0p on 2009-10-07
What authentication are you using? Just the ip number? Password? Key? 

You say it fails when using NX. What about if you try to make a ssh connection from the command line?

Is it FreeNX that you are using? Or NoMachine's proprietary server?

---

### Post by exww on 2009-10-07
Ok , im using the nomachine server and connecting to it from home with the nomachine nx client. Im using the standard username and password authentication. The shh connection works great from terminal with Putty. I set it so only i can login with that user account with my ip , all others will be denied.
To be able to login to NX i need to remove the rule that says  "- : user : ALL"

---

### Post by exww on 2009-10-08
bump

---

### Post by Chris Musampa on 2009-10-08
I think freenx authenticates as the 'nx' user so you might need to allow that too, this is purely a hunch so may be a load of cack.

---

### Post by exww on 2009-10-08
ok i added the nx user to access list and that didnt work , also i enabled ssh authentication in nx config but that didnt work aswell :([COLOR=#000000]
[/COLOR]

---

### Post by exww on 2009-10-09
bump

---

### Post by exww on 2009-10-11
still need help with this

---

### Post by exww on 2009-10-13
bump

---

### Post by exww on 2009-10-14
bump

---

### Post by exww on 2009-10-18
bump

---

### Post by exww on 2009-10-25
bump

---

