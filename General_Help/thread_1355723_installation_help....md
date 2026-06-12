---
title: "installation help..."
date: 2009-12-15
forum: General Help
---

### Post by luftadler on 2009-12-15
Hi,

I try to install FWTools but i don't understand the part  with **Bash**. 
Can anyone help me understand about what is talking after ./install.sh

 > Just unpack, run the install.sh script in the new directory, and then add the bin_safe directory to your path.   eg. 
% tar xzvf FWTools-linux-0.9.5.tar.gz
% cd FWTools-linux-0.9.5
% ./install.sh
 If you use Bash as your shell add the following to your startup script  (ie. ~/.bash_profile):  
PATH=$PATH:$HOME/FWTools/bin_safe
 or if you use csh or tcsh as your shell add the following to your .cshrc:  
setenv PATH $PATH:$HOME/FWTools/bin_safe



Thank you!

---

### Post by lewisforlife on 2009-12-15
If you don't know what shell you are using, then you are using Bash.  So what you will do is go to your shell, and:

```
gedit ~/.bash_profile
```

Then copy and paste PATH=$PATH:$HOME/FWTools/bin_safe into the .bash_profile file and save it, and exit out of gedit.

---

