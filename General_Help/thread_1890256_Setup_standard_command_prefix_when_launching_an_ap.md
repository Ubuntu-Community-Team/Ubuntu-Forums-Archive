---
title: "Setup standard command prefix when launching an application"
date: 2011-12-03
forum: General Help
---

### Post by Tryfon on 2011-12-03
Hello,

I have an Asus Eee pc 1215n, with two graphic chips on board, an Intel and an NVidia, managed by the NVidia optimus system.
I installed Bublebee and it seems to work just fine, but the problem now is that I must prefix the command 'optirun' before launching an application which I want to be run with NVidia graphics acceleration. For example 'optirun firefox'.
I want to setup this prefix command as standard for certain applications, so that whenever these applications are launched from anywhere, or by any program, they will be launched with the prefix command 'optirun' included.

What is the best way to do this?

---

### Post by hwttdz on 2011-12-03
You can do this with alias's, i.e. put the line
alias firefox="optirun /usr/bin/firefox"
in your .bashrc file, then any time you type firefox at the prompt it will be replaced by "optirun /usr/bin/firefox".  

A clever way would be to make yourself a ~/bin directory and put in there a script which would 
1) remake your path to not include ~/bin
2) launch "optirun programname" when called as programname
3) make a link to this program in ~/bin for each program you want to use this optirun for, so for firefox you'd do
ln -s optirun_script firefox
Then when you do "which firefox" it will tell you ~/bin/firefox, but that's really ~/bin/optirun_script, and optirun_script will see that it was called as firefox, so it knows to launch the firefox in not your bin prefixing it with optirun.

---

### Post by Tryfon on 2011-12-04
Thanks!

---

