---
title: "BASH script question"
date: 2010-02-16
forum: General Help
---

### Post by matej.smeto@gmail.com on 2010-02-16
Hello, 

id like to ask, if it is possible, to "register" custom made bash script in a following way:

i have "hello_world.sh", and i want it to be able to run from terminal from any folder, with command "helloworld" for example.

basically it would work for example like when you type "gedit", text editor is opened. 

So that whenever i will type command "helloworld", my "hello_world.sh" script will run as if located in current dirrectory.

Sorry if this is dumb question, but i am complete newbie in bash scripting, and solution to this would save me a lot of work.


thanx in advance for every helpful answer

greetings from

Smeto

---

### Post by Locutus_of_Borg on 2010-02-16
echo ". ~/.bash_aliases" >> ~/.bashrc && echo 'alias helloworld="sh /path/to/hello_world.sh"' >> ~/.bash_aliases && . ~/bash_aliases

---

### Post by gmargo on 2010-02-16
Create a personal 'bin' directory under your home directory ($HOME/bin) and place the script there.  Rename it to 'helloworld' or whatever you like.  Make it executable (chmod +x helloworld).  Your .bashrc file should already have set your $PATH to include $HOME/bin.  Then run from any directory.

---

### Post by geirha on 2010-02-16
> **gmargo said:**
> Create a personal 'bin' directory under your home directory ($HOME/bin) and place the script there.  Rename it to 'helloworld' or whatever you like.  Make it executable (chmod +x helloworld).  Your .bashrc file should already have set your $PATH to include $HOME/bin.  Then run from any directory.

Actually, it's ~/.profile (with default setup) that adds ~/bin to PATH. ~/.profile only gets sourced when you log in, so after creating ~/bin, log out and log back in again so that the PATH will be inherited by all new shells.

---

