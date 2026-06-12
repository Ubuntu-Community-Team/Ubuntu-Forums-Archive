---
title: "How to disable (double) USB flash drive autorun"
date: 2011-11-11
forum: General Help
---

### Post by Tornikee on 2011-11-11
Hello,

I'm using 11.10 w/ GNOME shell. When I plug in a USB flash drive, its contents open in an autorun folder, but I also get the small pop-up USB menu for opening it. I would like to only have this menu for such instances, so how can I disable USB autorun folders in 11.10?

Here's the screenshot of both folder and menu: [https://lh5.googleusercontent.com/-B5hvOqsZ7AI/Trz3KVf7eXI/AAAAAAAADAI/ba5zHACSg9s/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A15%25253A44.png](https://lh5.googleusercontent.com/-B5hvOqsZ7AI/Trz3KVf7eXI/AAAAAAAADAI/ba5zHACSg9s/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A15%25253A44.png)

---

### Post by pr3zident on 2011-11-11
> **Tornikee said:**
> Hello,

I'm using 11.10 w/ GNOME shell. When I plug in a USB flash drive, its contents open in an autorun folder, but I also get the small pop-up USB menu for opening it. I would like to only have this menu for such instances, so how can I disable USB autorun folders in 11.10?

Here's the screenshot of both folder and menu: [https://lh5.googleusercontent.com/-B5hvOqsZ7AI/Trz3KVf7eXI/AAAAAAAADAI/ba5zHACSg9s/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A15%25253A44.png](https://lh5.googleusercontent.com/-B5hvOqsZ7AI/Trz3KVf7eXI/AAAAAAAADAI/ba5zHACSg9s/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A15%25253A44.png)

just reread your question 

To disable this
go - System Preferences -- Removable Drives and Media:
and check the settings there ...

---

### Post by Tornikee on 2011-11-11
> **pr3zident said:**
> try this gconf-editor 
app - nautilus - preferences
media_automount_open uncheck this
media_autorun_never check this

Thanks for the reply. This is what I get in gconf editor re the autorun settings:

[https://lh5.googleusercontent.com/-oXCy2PLrSRw/Trz7pI2EqLI/AAAAAAAADBA/O4yb770jhXU/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A39%25253A21.png](https://lh5.googleusercontent.com/-oXCy2PLrSRw/Trz7pI2EqLI/AAAAAAAADBA/O4yb770jhXU/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A39%25253A21.png)

---

### Post by pr3zident on 2011-11-11
> **Tornikee said:**
> Thanks for the reply. This is what I get in gconf editor re the autorun settings:

[https://lh5.googleusercontent.com/-oXCy2PLrSRw/Trz7pI2EqLI/AAAAAAAADBA/O4yb770jhXU/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A39%25253A21.png](https://lh5.googleusercontent.com/-oXCy2PLrSRw/Trz7pI2EqLI/AAAAAAAADBA/O4yb770jhXU/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A39%25253A21.png)

the last comment i sent should help you out

---

### Post by Tornikee on 2011-11-11
> **pr3zident said:**
> the last comment i sent should help you out

Thanks for the assistance.

---

### Post by pr3zident on 2011-11-11
> **Tornikee said:**
> Thanks for the assistance.

np ;)

---

