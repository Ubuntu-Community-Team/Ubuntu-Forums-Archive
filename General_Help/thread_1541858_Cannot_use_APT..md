---
title: "Cannot use APT."
date: 2010-07-29
forum: General Help
---

### Post by hermitt on 2010-07-29
Hi - it seems as if my "APT" is not working correctly.  If I update or try and install any software, all the repositories give me a 404 error, and nothing happens.  For installing software, it gives this error at the end - 

'Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?'

I have used both the United States server and the main server, and neither work.  This is pretty much freshly installed (through virtual box), and I have access to the internet.  

Thanks for any help

---

### Post by jerenept on 2010-07-29
Your internet connection may be broken or unplugged. Can you acess the Internet from Firefox?

It is VERY UNLIKELY this is a problem with apt.

---

### Post by TheStroj on 2010-07-29
You mentioned Virtual Box - internet can cause trouble while using it and I believe that's the reason for APT not working (as the above post said, it's probably your connection).

Try playing around with settings, google can be useful for this kind of stuff.

---

### Post by hermitt on 2010-07-29
everything with the internet (as far as firefox and ssh are concerned) is fine.  no hickups, no timeouts, nothing.  I have also installed 4 other machines through virtual box (all ubuntu...i had some difficulty with guest additions) and all of them could run apt and update, so i don't think it is the virtual machine/internet connection.  
I've googled, but nothing really helpful came up.  Basically from my computer it looks as if the servers are down.

here's one of the repositories that failed.  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  404  Not Found

---

### Post by TheStroj on 2010-07-30
did you try downloading them 'by hand'?

---

### Post by hermitt on 2010-07-30
yep.  on my browser is says "404", and wget doesn't like it either.  I think I may just re-install the virtual machine.  its new enough installed that i won't lose much.  thanks for the help

---

### Post by WorMzy on 2010-07-30
Link works for me. Try it again; perhaps the server was temporarily down, and by chance so was the alternative you tried. Unlikely, but it could happen.

---

### Post by kio_http on 2010-07-30
Check the virtual machine network settings. Try playing with it. I.e change adapters etc.

---

### Post by hermitt on 2010-07-30
i guess it could be a firewall thing (im using my work internet), but all the other machines are linux too, and they are not affected.  same problem after the install of a new virtual machine, so im thinking its the virtual box settings.  will post after i fiddle with them

---

### Post by gonzomalan on 2010-07-31
> **hermitt said:**
> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  404  Not Found

i get something similar when i try to update my less-than-functional lucid partition. my mouse (connected via ps/2) doesn't work past the login screen, so i thought i would try to update my system to see if that would fix it. i got 0 connections to about 62 packages found for downloading. i'll post what i get next time i try it out, i just wanted to save this thread.

---

### Post by gonzomalan on 2010-08-04
i think i've narrowed my problem down to something wrong with X.
as far as apt, i was able to run lucid in recovery mode, select the dpkg (repair broken packages) option, and get all the updates/installs there, and then run a session in failsafeX mode to double check the update manager. i also installed the ubuntu restricted extras.
hope this helps.

---

