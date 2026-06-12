---
title: "Evolution works at work but not from home"
date: 2009-06-27
forum: General Help
---

### Post by mrphysics on 2009-06-27
I am new to Ubuntu (9.04) and have been trying to get evolution to work.

When I am at work I can connect and use it fine; however, from home I get a password request loop.

I am able to access the OWA from home, and when using Outlook via wine I can access it from home.

Any suggestions would be most welcome.

Jeff

---

### Post by v3xtra on 2009-06-27
Is the Exchange server located at your work?  I have Evolution working with Exchange at school and at home, but for me there are two different "addresses" that I can use.  The one that I can connect to with for the OWA, and another one that Evolution finds itself when I am connected at school.  I would check and see what address it is using at home.  I'd double check every configuration option as well, and make sure you are just not missing anything.

Are you using the same computer too?  Such as a laptop that you are bringing to work and then trying to use at home?

---

### Post by mrphysics on 2009-06-27
v3xtra - tnx for reply.

I did try the same machine at school and at work. I used the same address in both locations. It connected fine at work but not at home. When I configured Outlook to access the exchange server from home (which I am able too) I used the same address for Evolution and no joy.

I even tried to copy/import the profile from my laptop that worked at school to my desktop at home - no luck.

I can access the exchange server using exchange.myschool.com from home via the web interface.

When setting up evolution at home choose the Exchange server type and when trying to authenticate I get

Could not authenticate to server.

Make sure the username and password are correct and try again.

If I use [https://,](https://,) I get

Could not authenticate to server.

Make sure the username and password are correct and try again.

If I try and use the Exchange MAPI server type, it just closes evolution when I try to authenticate.

Any other ideas?

Jeff

---

