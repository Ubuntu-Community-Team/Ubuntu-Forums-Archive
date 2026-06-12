---
title: "firestarter/startup apps problem"
date: 2010-02-17
forum: General Help
---

### Post by borchid487 on 2010-02-17
Hi, I'm trying to set firestarter as a startup application using the gui but it will not run due to permissions problems, any thoughts? 

thanks.

---

### Post by bluefrog on 2010-02-17
add a "bypass" password in the sudoers file

user ALL=NOPASSWD: command

---

### Post by Ordes on 2010-02-17
u know that you dont need to autostart firestarter for you to make it run..

firestarter is basiccly just a tool to configure your IP tables, so the settings while always be loaded up even when u dont load up firestarter. when u set your firewall, you just need to load firestarter if you:
a) want to make changes to your firewall
b) monitor your firewall behaivour

if you want to make a test, you can just load up firestarter set output to restricted (everything) and restart. Even without loading up firestarter you still wont be able to access the internet, as you blocked all output..

---

### Post by 3rdalbum on 2010-02-17
> **borchid487 said:**
> Hi, I'm trying to set firestarter as a startup application using the gui but it will not run due to permissions problems, any thoughts? 

thanks.

1. Firestarter is not a firewall - it's a program that lets you configure the built-in firewall. You don't need it open on login - the firewall will run with your configured settings as soon as the kernel loads.

2. Only root can modify firewall rules. In order to launch Firestarter as root, you need to preface it with "gksudo":

```
gksudo firestarter
```

3. Firestarter hasn't had any serious development for years. It's overkill for a single desktop machine, too. I recommend gUFW instead - it's easier to use. It doesn't have the logging capabilities of Firestarter, but then for a single personal machine you don't need it (who needs to know about attempted incoming connections? They're being blocked anyway!) and a lot of people get scared when they see blocked incoming connections, and think that the Russian Mafia is trying to hack them or something.

4. If you have an ADSL/cable modem or any sort of router, you're already protected by that device's firewall and you don't need an additional one running on your computer.

---

### Post by WaveMyBlackFlag on 2010-04-13
More proof you (I) can answer a question without asking anyone.  the search tool is all you need most times.

---

