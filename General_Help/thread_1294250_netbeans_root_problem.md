---
title: "netbeans root problem"
date: 2009-10-18
forum: General Help
---

### Post by ceycey60 on 2009-10-18
i want to develop php application using netbeans IDE, i can use geany and open it typing "sudo geany" command to terminal. But when i open netbeans with that command, i cannot open normally (double-click) it and get some errors

---

### Post by MartinEve on 2009-10-18
If it is a graphical application you should launch with gksudo (for gnome) or kdesudo (for kde).

Can I ask why your IDE requires root? This seems a highly unnecessary security risk...

---

### Post by ceycey60 on 2009-10-18
> **MartinEve said:**
> If it is a graphical application you should launch with gksudo (for gnome) or kdesudo (for kde).

Can I ask why your IDE requires root? This seems a highly unnecessary security risk...

my php files are located at "var/www" directory and i can't access those files without root permissions

---

### Post by ceycey60 on 2009-10-18
what can i do? :confused:

---

### Post by Dark9204 on 2009-10-18
> **ceycey60 said:**
> my php files are located at "var/www" directory and i can't access those files without root permissions

You have 2 options here as i see it.

1. Change the owner to to your user. Makes things it a lot more easier to manage, but lowers security.
          "sudo chown -R <user> <target>"
             or:
            "sudo chown -R <user:group> <target>"
                 (change owner) -R(recursive)

               For example: sudo chown -R username www.

2. Run Netbeans as sudo with the "gksu" when you launch it.) This will ask you for your sudo password the graphical way.

Hopes everything turns out right for you! ;)

---

