---
title: "All browsers unable to read cookies????"
date: 2009-12-05
forum: General Help
---

### Post by itsJim on 2009-12-05
I'm not really sure what is going on here but I am unable to use a few sites; this happens with both firefox and opera. Here are a few examples:
[LIST]
[*]facebook.com: brings me to a login screen with no errors. 

[*]netflix.com: gives me an error saying cookies aren't enabled.

[*]mail.google.com: loading bar goes nuts. https works fine.

[*]None of my login information is saved on any other sites.
[/LIST]
I know the cookies are being saved because I see them in the firefox preferences. I tried deleting ~/.mozilla and the same issue still occurs. The permissions on ~/.mozilla are set to jim:jim, 700.

This may or may not have to do with the raid 0 on /home breaking. Not sure why, I can still rwx everything but it's the only thing I can think of because it was working fine on the initial install. I'm still waiting on newegg for the replacement drive.

Anyone have any ideas on what is going on here?

---

### Post by akakingess on 2009-12-05
Which browsers have you tried, and have you tried a "new" profile within Firefox, you can start into the Profile Manager by using the terminal and typing "firefox -p" , and you should be able to try a new fresh profile, with no add-ons, etc. just to try to narrow down where the problem lies.

---

### Post by itsJim on 2009-12-05
firefox and opera. deleting ~/.mozilla started firefox with no add-ons installed and the issue remained.

---

### Post by akakingess on 2009-12-05
I am almost definite that there is nothing within Ubuntu that could be causing this problem, so I would definitely start looking at the Raid issue, even though you as the user may have rwx rights, I don't think that applies to software that you are running necessarily. Again, I am just trying to help, but am by no means an expert on the matter, hopefully someone who may have experienced this or has more experience with Raid on your home partition can chime in...

---

