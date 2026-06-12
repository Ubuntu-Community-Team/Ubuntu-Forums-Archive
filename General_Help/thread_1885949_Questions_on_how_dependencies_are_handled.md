---
title: "Questions on how dependencies are handled"
date: 2011-11-24
forum: General Help
---

### Post by obourdon on 2011-11-24
Let's assume I have a package which says "I need A or B" for instance 
lsb-graphics which requires libx11-6 or xlibs

Are there cases where both functionalities are provided by 2 different packages P1 and P2 and if
yes then how is the choice made between P1 and P2

On another side, I have a package P which requires mail-transport-agent
and knowing that the following packages provide this
citadel-mta
courier-mta
dma
esmtp-run
exim4-daemon-heavy
exim4-daemon-light
lsb-invalid-mta
masqmail
msmtp-mta
nullmailer
postfix
sendmail-bin
ssmtp
xmail
 what will determine which one will be chosen when I install P

---

### Post by Gatemaze on 2011-11-24
I assume once marked for installation then the dependency check for the second repeated dependency is satisfied. But I don't know the exact implementation of apt and deb so it is only my guess.

---

