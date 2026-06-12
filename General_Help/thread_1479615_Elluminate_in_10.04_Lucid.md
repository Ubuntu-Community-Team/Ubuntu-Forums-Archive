---
title: "Elluminate in 10.04 Lucid"
date: 2010-05-10
forum: General Help
---

### Post by windfix on 2010-05-10
I just wanted to post for others that might run across this using Elluminate Live web conferencing.  Elluminate will not work (at least for me) with OpenJDK/Icedtea.  Since Sun Java was deprecated in 10.04, you must 
1. remove OpenJDK (at least, I've heard, to avoid probably confusion and troubleshooting if you have both)
2. install Sun Java 6... see: [http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

From prior experience with Elluminate under Ubuntu, also:

3.  openoffice.org-java-common must be added (you can use Synaptic)
4.  in OpenOffice, under Tools | Options | OpenOffice.org - Java, the Sun Microsystems JRE must be checked and selected
5.  After restarting OpenOffice, select StarOffice path from Elluminate preferences ( mine is located in /usr/lib/openoffice/program/soffice)

I hope that helps someone else!

---

### Post by madmercenary on 2010-07-19
How do i remove OpenJDK?

---

### Post by CitizenUnderdog on 2010-12-08
This seems to still work with Ubuntu 10.10.

Thanks!

---

### Post by swiss-chris on 2011-03-26
I tried following these instructions, but can't solve the problem under 10.4

However, I didn't do step 4 since I don't have OpenOffice installed. Do I have to install the full OpenOffice (which I never use) just to get this sound problem fixed for Elluminate?

---

### Post by windfix on 2011-05-06
@swiss-chris, what sound problem specifically?

@mad, in Synaptic Package Manager remove everything that starts with openjdk and remove icedtea plugin.  Add the Partner Repository, then Sun Java packages will show up.

---

### Post by Der_Kommissar on 2011-05-16
Just a quick note to add to this post - Application sharing within Elluminate Live v10 and Ubuntu 10.04 / 10.10 seems to have limited functionality.  You can share an application, but you can't give control of the app from a 10.04 / 10.10 machine to anyone else.  (If you share from another OS **to** the Ubuntu machine it'll work.  

For reasons I'm not entirely sure of, this is working again with 11.04 and Sun Java 1.6.0_24.

You can use the "Web Tour" feature, but you won't have the ability to post a link to chat from within the web tour or to change pages once you've initiated it.

---

### Post by windfix on 2011-05-16
> **windfix said:**
> I just wanted to post for others that might run across this using Elluminate Live web conferencing.  Elluminate will not work (at least for me) with OpenJDK/Icedtea.  Since Sun Java was deprecated in 10.04, you must 
1. remove OpenJDK (at least, I've heard, to avoid probably confusion and troubleshooting if you have both)
2. install Sun Java 6... see: [http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

From prior experience with Elluminate under Ubuntu, also:

3.  openoffice.org-java-common must be added (you can use Synaptic)
4.  in OpenOffice, under Tools | Options | OpenOffice.org - Java, the Sun Microsystems JRE must be checked and selected
5.  After restarting OpenOffice, select StarOffice path from Elluminate preferences ( mine is located in /usr/lib/openoffice/program/soffice)

I hope that helps someone else!

Note that with newer Ubuntu versions, #3 is now libreoffice-java-common

---

### Post by Mgcross on 2011-08-26
Thanks!

---

### Post by solanas on 2013-01-11
Some workaround to solve the same problem in Ubuntu 12.04 with Elluminate 12 (now called BlackBoard Collaborate Webconference)?

LibreOffice is not recogniced as OpenOffice installation in Elluminate and we can't import .odp presentations in Elluminate.

Thank you.

---

### Post by howefield on 2013-01-11
Old thread closed.

---

