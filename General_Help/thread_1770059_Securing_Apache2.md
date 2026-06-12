---
title: "Securing Apache2"
date: 2011-05-28
forum: General Help
---

### Post by Kromgol on 2011-05-28
Hello.

Been running apache2 for a while now and i've tried looking around to see how i can make it more secure but since i'm now letting another user having his site on my server, is there any more precautions that i can take so the server doesn't get blown up/hacked/whatever?
Every suggestion helps.

Thanks.

---

### Post by sefs on 2011-05-28
1) Keep it patched.

2) Let it, apache, return/leak as little info as possible (such as version etc) about itself or other software running on it. For instance when a browser returns a page not found error version info can be seen in the error page.

3) run php under fcid and suexec, so you don't have to muck about with permissions (setting directories to be 777 etc.) when using scripts like joomla.

4) ...

---

### Post by Kromgol on 2011-05-28
Would be great if you could write some information about what these mods for example. Might just be me, but it's a bit hard to find some good information that's actually readable and that doesn't go to the technical details directly :P

---

### Post by sefs on 2011-05-28
> **Kromgol said:**
> Would be great if you could write some information about what these mods for example. Might just be me, but it's a bit hard to find some good information that's actually readable and that doesn't go to the technical details directly :P

See here...

[http://www.petefreitag.com/item/505.cfm](http://www.petefreitag.com/item/505.cfm)

---

### Post by sefs on 2011-05-28
for 3) see here...

[http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-8.10](http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-8.10)

---

### Post by Kromgol on 2011-05-29
Thanks.

---

### Post by Kromgol on 2011-05-29
I've been sitting for hours trying to get mod_fcgid working, but it refuses to work completely! Every time i follow that guide (Which seems like the only complete guide to getting fcgid to "work" on the whole of the internet) PHP always stops working in the end, by enabling fcgid or trying to install php5-cgi which the guide said was necessary.

Any help?

---

### Post by sefs on 2011-05-29
Which version of ubuntu are you on?

btw this is the guide for 10.04 [http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-10.04)

Are you using virtualhost? and where are they situated? in /var/www or /home?

---

### Post by Kromgol on 2011-05-29
> **sefs said:**
> Which version of ubuntu are you on?

btw this is the guide for 10.04 [http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-10.04)

Are you using virtualhost? and where are they situated? in /var/www or /home?

Looked through that guide as well.
I'm using 11.04, and the files are situated in /var/www

---

