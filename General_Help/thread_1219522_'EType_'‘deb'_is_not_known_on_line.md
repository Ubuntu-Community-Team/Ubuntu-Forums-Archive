---
title: "'E:Type '‘deb' is not known on line"
date: 2009-07-21
forum: General Help
---

### Post by KneoMattrix on 2009-07-21
I am getting the following error when I run the update manger


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '‘deb' is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


And I get the following when I try to use Add/Remove under Applications

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


And the following error when I try to Synaptic Package Manager

E: Type '‘deb' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Can anyone tell me what I need to do to fix this?

Thank you

---

### Post by 3rdalbum on 2009-07-21
> **KneoMattrix said:**
> 'E:Type '&#8216;deb' is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I'd suggest checking the correctness of the file '/etc/apt/sources.list':

```
gksudo gedit /etc/apt/sources.list
```

This brings up a text editor with the sources list. The package manager says that there's a problem with line 54, and from the error message it looks like you've put quotation marks around that line. Remove those quotation marks and save your changes. Go into Synaptic and hit Reload (or run "sudo apt-get update") and everything should be fine again.

In future try to use the System > Administration > Software Sources program to add new repositories; it prevents problems like this.

---

### Post by KneoMattrix on 2009-07-21
That worked. I think I messed up by trying to install Firefox 3.5. Can anyone tell me the best way to install that?

I have tried but when ever I load Firefox it is still 3.0.11

---

### Post by red_starr9 on 2010-07-14
Thanks, I had the same problem when i tried to install tor and privoxy. It was three lines with '' marks in the beginning and end of the source addresses.

thanks for the instruction :>).

---

### Post by lisati on 2010-07-14
Thread closed: necromancy.

---

