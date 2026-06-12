---
title: "Adobe Acrobat 9"
date: 2010-02-15
forum: General Help
---

### Post by Truckdogg4 on 2010-02-15
How do you uninstall Adobe Acrobat 9 Pro from Ubuntu? Tried Synaptic Package Manager without any luck. Anyone know what the command using Terminal would be?

---

### Post by Satoru-san on 2010-02-15
in gentoo the package is acroread. I am not sure in ubuntu, so you can search for it

```
apt-cache search adobe reader
sudo apt-get purge <package name>
```I hate acroread, but for some reason, for me it gets pulled in as a dependancy, hopefully that wont happen for you.

:D Welcome to the forums! Enjoy it here! :D
**DONT BLINDLY RUN COMMANDS THAT PEOPLE ON THE FORUMS TELL YOU**
[i]some times people will post malicious command that will destroy your
install[/i]
If you have any questions about what the commands do, ask someone!

---

