---
title: "Run perlscript with sudo permissions through phpscript"
date: 2010-03-03
forum: General Help
---

### Post by Eax.exe on 2010-03-03
Hi there :)

I'm trying to set up a php-script that calls a perl-script with sudo permissions (the perl-script needs these permissions to run its commands).

This php-script is hosted on a LAMP apache server (in Ubuntu) and is run by the user www-data (pseudouser created by apache).
I have tried adding the line:
```
www-data ALL=(ALL) NOPASSWD:ALL
```
But it doesn't seem to work and it seems like somewhat of a security issue.

How can I do this?
Thanks in advance :)

---

### Post by diesch on 2010-03-03
Make the perl script SUID root and use perl-suid to run it.

---

### Post by Eax.exe on 2010-03-03
> **diesch said:**
> Make the perl script SUID root and use perl-suid to run it.

Can you explain how please? :)

---

### Post by Eax.exe on 2010-03-03
I installed the package "super" containing "setuid" but I have no idea how to use it :/

---

### Post by diesch on 2010-03-03
1. install the package *perl-suid*
2. make root the owner and www-data the group of the file:
```
sudo chown:www-data root your_perl_script
```
3. set the SUID bit, read and exec permissions for the group, no permisions for others:
```
sudo chmod u+s,g=rx,o-rwx your_perl_scrip
```
4. In the first line of the script replace *perl* with *suidperl*
e.g. change
```
#!/usr/bin/perl -w
```
to
```
#!/usr/bin/suidperl -w
```

Now if you run the script it's running as root. [B]

Be careful as[/B] **everyone in the www-data group can run this script as root!**

---

### Post by Eax.exe on 2010-03-03
> **diesch said:**
> 1. install the package *perl-suid*
2. make root the owner and www-data the group of the file:
```
sudo chown:www-data root your_perl_script
```
3. set the SUID bit, read and exec permissions for the group, no permisions for others:
```
sudo chmod u+s,g=rx,o-rwx your_perl_scrip
```
4. In the first line of the script replace *perl* with *suidperl*
e.g. change
```
#!/usr/bin/perl -w
```
to
```
#!/usr/bin/suidperl -w
```

Now if you run the script it's running as root. [B]

Be careful as[/B] **everyone in the www-data group can run this script as root!**

Thank you so so much :)

---

