---
title: "Problem with installing SFLPone in Ubuntu 11.04"
date: 2011-05-01
forum: General Help
---

### Post by priyanjan on 2011-05-01
Hi, 
i am new in Ubuntu.I have installed Ubuntu 11.04 and I have installed SFLphone by Software Center.It installed properly but when i tried to open the application,it did not open.Therefore,I removed the application and tried using terminal by following commands:

```

sudo add-apt-repository ppa:savoirfairelinux
sudo apt-get update
sudo apt-get install sflphone-client-gnome

```

But i am getting following message when i run last command:

The following packages have unmet dependencies:
 sflphone-client-gnome : Depends: libebook1.2-9 but it is not installable
                         Depends: libedataserver1.2-13 but it is not installable
                         Depends: libedataserverui1.2-8 but it is not installable
                         Depends: libwebkit-1.0-2 but it is not installable
E: Broken packages



Please help

---

