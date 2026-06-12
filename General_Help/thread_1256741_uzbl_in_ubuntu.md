---
title: "uzbl in ubuntu"
date: 2009-09-03
forum: General Help
---

### Post by scheibo on 2009-09-03
Hey, I'm trying to get uzbl (the browser, [www.uzbl.org](www.uzbl.org)) installed on ubuntu 9.04 to play around with it. I'm kind of stuck and would love some help either compiling from source or using the package manager.

When trying to compile from source, im not sure how to go about compiling the dependencies required, and simply following the instructions on the site for installing after cloning from github gives me errors. Then I tried following the lovely instructions here: [http://www.uzbl.org/wiki/ubuntu_howto](http://www.uzbl.org/wiki/ubuntu_howto) for installing from apt (though I'd rather learn how to install from the github), and that seems to work because it has the uzbl programs and docs and what not in place. however, even if i place lines in my .bashrc to set the 'XDG_CONFIG_HOME="/usr/share/uzbl/examples/config uzbl"' and 'XDG_DATA_HOME=/usr/share/uzbl/examples/data' , i still cant use any of the config scripts and what not that make the browser usable. all i can really do is launch from the command line "uzbl --uri www.google.com" or something, and not even be able to type anything into forms.

tl;dr: Hopefully someone knows how to configure uzbl properly to run on ubuntu so that the scripts provided with it work

---

### Post by mrgnash on 2009-09-04
I can't help you with the compiling side of things, but what I can tell you is that, rather than editing my .bashrc, what worked for me was copying /usr/share/uzbl/examples/config to ~/.config/uzbl/config , and the files in /usr/share/uzbl/examples/data to ~/.local/share/uzbl . Then I just made the necessary edits to ~/.config/uzbl/config in order to point it to the relevant scripts in ~/.local/share/uzbl. Hope that helps :)

---

