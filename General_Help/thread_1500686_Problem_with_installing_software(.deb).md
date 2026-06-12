---
title: "Problem with installing software(*.deb)"
date: 2010-06-03
forum: General Help
---

### Post by tuxtix on 2010-06-03
I currently using Ubuntu 10.04 LTS
Whenever I try installing any new package(*.deb) it will display red error message that I don't understand.

What happen? and how to solve this problem?

thanks

---

### Post by WorMzy on 2010-06-03
It means that you don't have the necessary packages installed that the package needs. Install libqt3-mt first, then try again. You may also need libqt3-mt-dev. Both are in the repos (sudo apt-get install libqt3-mt libqt3-mt-dev)

---

### Post by tuxtix on 2010-06-03
Thanks WorMzy, but I don't know how to install libqt3-mt.

---

### Post by sanderd17 on 2010-06-03
he gave the commands, but a bit unclear
```

sudo apt-get install libqt3-mt libqt3-mt-dev

```

---

### Post by WorMzy on 2010-06-03
If you're not comfortable using the terminal, you can also find the package(s) in the Ubuntu Software Centre or Synaptic Package Manager, both of which can be accessed from Ubuntu's main menu.

Ubuntu Software Centre: Applications -> Ubuntu Software Centre
Synaptic Package Manager: System -> Administration -> Synaptic Package Manager

---

### Post by tuxtix on 2010-06-03
sanderd17, Do I need to connect to internet before using that command.

---

### Post by azertyh on 2010-06-03
> **tuxtix said:**
> sanderd17, Do I need to connect to internet before using that command.

yes

---

### Post by tuxtix on 2010-06-03
Thanks alot,I will try again. :)

---

### Post by bodhi.zazen on 2010-06-03
First it helps if you tell us what you are trying to install.

Second you should try Add/Remove programs, synaptic, or apt-get , these applications will install dependencies.

Third, just because it is a .deb does not mean it is compatible with Ubuntu. Use the repositories.

If it is a third party Ubuntu compatible .deb, you install the dependencies (after receiving that error message) with :

```
sudo apt-get install -f
```

Then re-install the .deb

See :

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

This link has detailed instructions for installing opera:

[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

