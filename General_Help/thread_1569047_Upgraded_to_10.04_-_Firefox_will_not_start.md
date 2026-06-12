---
title: "Upgraded to 10.04 - Firefox will not start"
date: 2010-09-06
forum: General Help
---

### Post by svsig on 2010-09-06
Hi.

I have just upgraded a machine from 09.10 to 10.04 and now Firefox will not start. When I click the icon in the panel, Firefox appears to be starting but then it disappears again. 

What can I do about this? Without Firefox the machine is virtually useless.

Regards,
Sveinung

---

### Post by lovinglinux on 2010-09-06
First delete the files *compatibility.ini* and *secmod.d*b from your Firefox profile folder, located under ~/.mozilla/firefox/<profilename>.

If that doesn't help, see Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Report back with the results.

---

### Post by svsig on 2010-09-07
I managed to solve the problem myself. 

I tried to start Firefox from Terminal and got an error message. It was a problem with libmoon, a free software clone of Silverlight 2.0, that I had tried to install some time ago. When I removed libmoon it worked again.

Sveinung

---

### Post by lovinglinux on 2010-09-07
> **svsig said:**
> I managed to solve the problem myself. 

I tried to start Firefox from Terminal and got an error message. It was a problem with libmoon, a free software clone of Silverlight 2.0, that I had tried to install some time ago. When I removed libmoon it worked again.

Sveinung

Indeed libmoon is known to cause such issues, although it has been a while since I saw someone experiencing issues with it. Good to know.

---

