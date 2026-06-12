---
title: "Turn on autocomplete with tab key for user root."
date: 2006-06-06
forum: General Help
---

### Post by CyberAngel on 2006-06-06
Probably most of you know that when you are using the console to do things the  "tab" key on keyboard autocompletes what you are writing or displays all the possible suggestions...
That (in combination with yakuake :)) is one of the most usefull things for me.

Dapper has this feature (as all of linuxes i have seen so far) but it is more advanced. It can autocomplete not only the first command or the files but even the parameters of many commands!!!

e.g when you press ```
apt-g<tab> r<tab> a<tab><tab>
``` this will return in console all the installed packages that are able to be removed and starts with an "a"

for me it returns the following:
```
$ apt-get remove a
acpi              adduser           alsa-base         amarok-xine       appres            apt-utils         artsbuilder       at
acpid             adept             alsa-utils        anacron           apt               ark               aspell            automatixpure64
acpi-support      akregator         amarok            app-install-data  aptitude          arts              aspell-en         avidemux

```

OK to the point now. That feature is enabled only for the default created user (the one you are entering when you installing dapper). How can I enable it for the root user too?

---

### Post by Ramses de Norre on 2006-06-06
```
sudo cp ~/.bash_aliases /root/.bash_aliases
sudo vi /root/.bashrc

```
Search following lines and uncomment them all:
```
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```
```
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi
```
Root should have full autocompletion now.

---

### Post by Ramses de Norre on 2006-06-06
My post appeared twice..

---

### Post by CyberAngel on 2006-06-06
Thank you!! It works now :)

---

