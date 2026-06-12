---
title: "Any difference between using update manager and update command (from terminal)?"
date: 2012-10-08
forum: General Help
---

### Post by arroy_0209 on 2012-10-08
Is there any difference between using update manager from main menu and using the commands ```
sudo apt-get update && sudo apt-get upgrade
``` from a terminal? The only difference I notice is that in case of using the manager, I can choose which packages are to be installed and which may be postponed but in case of running command from terminal, all suggested packages must be installed. Are there any other significant differences between these methods?

---

### Post by jerrrys on 2012-10-08
Some find the update-manager too simple and slow.  Others find the terminal too intimidating.  So I guess it boils down to a personal choice.  I myself have found a happy medium, kind of the best of both worlds.

[Synaptic Package Manager ]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

If you want to give it a try, open a terminal and enter:

sudo apt-get install synaptic

---

### Post by Old_Grey_Wolf on 2012-10-08
If you use apt-get upgrade it doesn't install some things that the update manager installs. To install everything the update manager installs use the command apt-get dist-upgrade. Here is a description of the difference in the two commands [http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade](http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade)

---

