---
title: "Ubuntu 11.04 update error?"
date: 2011-09-12
forum: General Help
---

### Post by vikash_chandola on 2011-09-12
see two attachments you will go the error. what is that.
In left image it is searching for update
In second image giving error.

---

### Post by raja.genupula on 2011-09-12
do the update from the terminal

```
sudo apt-get update
```

paste the output here

---

### Post by Frogs Hair on 2011-09-12
For that error I would just try again later at a later time . Do you belong to a network with a few computers ? , if so you could have lost conductivity due to others using the connection . It may also be a temporary ISP glitch  .

---

### Post by vikash_chandola on 2011-09-12
> **raja.genupula said:**
> do the update from the terminal

```
sudo apt-get update
```paste the output here
that is it
```

.........................
gn http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.
vikashchandola@ubuntu$

```Actually i have fully updated my Ubuntu in morning. After updating i recheck to confirm that am i fully up to date. During that check all this appear. I am using MTS MBlaze in Delhi. any idea.

---

### Post by raja.genupula on 2011-09-12
> **vikash_chandola said:**
> that is it
```

.........................
gn http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.
vikashchandola@ubuntu$

```Actually i have fully updated my Ubuntu in morning. After updating i recheck to confirm that am i fully up to date. During that check all this appear. I am using MTS MBlaze in Delhi. any idea.

open your update manager 


in the settings at ubuntu software uncheck the cdrom then try again

---

### Post by vikash_chandola on 2011-09-12
> **raja.genupula said:**
> open your update manager 


in the settings at ubuntu software uncheck the cdrom then try again
thnks bhai. Problem solved.

---

### Post by raja.genupula on 2011-09-12
aah you're welcome

---

