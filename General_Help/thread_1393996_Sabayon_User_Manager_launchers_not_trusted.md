---
title: "Sabayon User Manager launchers not trusted"
date: 2010-01-30
forum: General Help
---

### Post by stpgod on 2010-01-30
I'm working on setting up a computer lab for my kids' school, and am planning to use Ubuntu LTSP and Sabayon User Manager to lock things down.


When I edit a profile in Sabayon, and create the default desktop icons I'd like them to have (Firefox for example), when the user logs in the icon is generic and when clicked says:


"The application launcher Firefox.desktop is not marked as trusted. If this application launchers source is unknown to you then it may be unsafe to launch."


If I click "Mark as Trusted", the Firefox icon pops up and all is well. However whenever a new user logs in, they have to go through this process and I'm worried it may confuse them. 


Why are application launchers created by Sabayon not trusted by my LTSP users? Am I doing something wrong?


Ubuntu 9.10 by the way. Thanks in advance for any help!

---

### Post by croemmich on 2010-01-30
I'm having this same problem also. It is very frustrating as it simply will not go away. I have added both a start up application to the profile and a ldm rc script to run "chmod +x ~/Desktop/*.desktop" but neither of these are working either.

Thanks!

---

### Post by cohill on 2010-07-07
I'm having the same issue.  Does anyone have any suggestions?  I'm willing to experiment with any suggestions that are offered.

---

