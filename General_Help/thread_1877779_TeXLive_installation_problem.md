---
title: "TeXLive installation problem"
date: 2011-11-08
forum: General Help
---

### Post by Randy Schilling on 2011-11-08
Hello -

I'm setting up newly installed U11.10 and working under its Unity desktop.

I ran into a problem with my installation of TeXLive2011.
I chose to install this software by downloading it (from the TUG web site) 
because Synaptic offers only the outdated TexLive2009.

TeXLive's instructions tell us to move to the folder containing install-tl
(so its full path is not necessary),
to add the current folder to the PATH variable with the command,
    PATH=.:$PATH,
and start the installer with the command,
        install-tl -gui wizard.
The TeXLive installer opens, tries to install to 
    /usr/local/texlive/2011
and returns the message 
   "default not allowed or not writeable - please change."
I did not run into this problem awhile ago when I installed TexLive under U10.04.
I checked that I'm working under an administrator account.
I tried starting the installer with the command:
        sudo install-tl -gui wizard
and got a "command not found" error.
I tried logging in as root user with the command,
    sudo passwd root,
started the TexLive installer as before,
        install-tl -gui wizard,
and got the same response.

I think this means that some permissions need to be changed but I want to check with you 
to see if there is a more global way of improving my administrative privileges.

Many thanks and regards - Randy

---

### Post by mc4man on 2011-11-08
Maybe try like this (@ the same prompt as in Ex.
```
 sudo ./install-tl -gui wizard
```

Ex.
> :~/install-tl-20111108$ sudo ./install-tl -gui wizard

screen show moving along at the default install location - /usr/local/..


edit: did you clean out any previous at that location?

(here I'm only leaving the ubuntu texlive-common, texinfo packages, may create an equivs later

---

### Post by Randy Schilling on 2011-11-08
Your instructions seem to be working, the installation is going as I type.
Please, three questions.  
     Does the dot refer to the current directory?
     What does the dot do in your command?
      Is this the correct syntax to extend the PATH variable to include the current directory?
                            PATH=.:$PATH
(I haven't had to think about Bash commands in quite awhile)
Thanks so much and regards - Randy

---

### Post by mc4man on 2011-11-08
Randy - I'm not the best person to ask on technical 'correctness', only been using linux for 4 yrs & am old enough to only remember what I currently need to know..

Anyway I've always assumed that ./ means inside of the current working dir.
Without the . then /install-tl would mean inside a  dir named install-tl which obviously doesn't exist

just install-tl would mean run that command, (if in path), which was the purpose of the PATH=.:$PATH

So either would work - I gave you the ./ to make sure..  - 
PATH=.:$PATH
sudo install-tl

or 
sudo ./install-tl

---

### Post by Randy Schilling on 2011-11-09
Thanks so much for your help Mc4man.

---

