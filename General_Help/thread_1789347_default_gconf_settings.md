---
title: "default gconf settings"
date: 2011-06-23
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-23
how can i set the default users configuration

i want to prevent popup about a partition being full since nobody cares (it is a partition for virtual machines)

change the title button order so someone who spent the last 15 years using windows will know where the buttons are
edit:
figured it out had to copy some stuff from ~/.gconf
and the 0 byte %gconf.xml files are important
default profile stuff goes in /etc/skel
```
/etc/skel
|-- .bash_logout
|-- .bashrc
|-- examples.desktop
`-- .gconf
    |-- apps
    |   |-- %gconf.xml
    |   |-- gnome_settings_daemon
    |   |   |-- %gconf.xml
    |   |   `-- plugins
    |   |       |-- %gconf.xml
    |   |       `-- housekeeping
    |   |           `-- %gconf.xml
    |   `-- metacity
    |       |-- %gconf.xml
    |       `-- general
    |           `-- %gconf.xml
    `-- desktop
        |-- %gconf.xml
        `-- gnome
            |-- %gconf.xml
            `-- peripherals
                |-- %gconf.xml
                `-- mouse
                    `-- %gconf.xml
```

---

