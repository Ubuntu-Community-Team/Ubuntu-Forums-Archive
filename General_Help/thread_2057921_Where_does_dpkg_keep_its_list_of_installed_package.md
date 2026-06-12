---
title: "Where does dpkg keep its list of installed packages?"
date: 2012-09-14
forum: General Help
---

### Post by Rallg on 2012-09-14
I'm using 12.10 QQ 32-bit, but this question probably applies to all distros:

I can use dpkg -l to get a list of all installed packages. Presumably, dpkg merely reads an existing file buried somewhere in the system, then outputs that file to me (perhaps processed first).

But I wish to look at the original file, the one that is read by dpkg. What is that file name? Where is it?

---

### Post by hwttdz on 2012-09-14
/var/lib/dpkg/status?  You probably want to look at the source (or at least doc) of dpkg to be sure.

---

### Post by Lars Noodén on 2012-09-14
I think it might be  /var/lib/dpkg/status, but I am not sure.

---

### Post by Rallg on 2012-09-14
Marked solved. The info was there, as suggested above. However, the file wasn't as useful as I thought it might be. I'm going to try something called "checkinstall" to see if it's more useul. I'm experimenting, so if others are wondering what use is is to them, just forget about it. ):P

---

### Post by Lars Noodén on 2012-09-15
What are you trying to do or what information do you need?  There might be an easy way using the existing tools.

---

