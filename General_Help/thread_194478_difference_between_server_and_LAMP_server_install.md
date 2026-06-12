---
title: "difference between server and LAMP server install"
date: 2006-06-11
forum: General Help
---

### Post by tlo on 2006-06-11
I'm trying to learn php and sql, and since it is apparently pretty hard to install and configure apache, php, and sql to work together, i decided to just install the server install. is the LAMP server install the only way to get the preconfigured setup, or does the normal server install also include thse?

---

### Post by Evoreth on 2006-06-11
Just insert "sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql" into your terminal and it works. Pretty hard, huh?

---

### Post by tlo on 2006-06-12
wait, don't you have to get them to talk to each other? thats it?

---

### Post by MiKuS on 2006-06-12
Thats all i ever do, works like a charm every time.

---

### Post by tlo on 2006-06-12
[QUOTE=MiKuS]Thats all i ever do, works like a charm every time.[/QUOTE]

wish i knew that before i overwrote my ubuntu with a fubar'd ubuntu lamp server lol

---

### Post by Vyizis on 2006-06-12
I second that, i installed my server like that the other day and  it works like a dream.

---

### Post by az on 2006-06-12
[QUOTE=tlo]wait, don't you have to get them to talk to each other? thats it?[/QUOTE]
Say thanks to the package maintainers.

---

### Post by tlo on 2006-06-13
[QUOTE=azz]Say thanks to the package maintainers.[/QUOTE]

package maintainers. that is exactly why linux is better than windows. wamp config == bad, lamp config == one line in the terminal. thank you package maintainers

---

