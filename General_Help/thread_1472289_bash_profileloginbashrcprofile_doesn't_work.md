---
title: "bash_profile/login/bashrc/profile doesn't work"
date: 2010-05-04
forum: General Help
---

### Post by mayapower on 2010-05-04
I am using ubuntu "hardy" 8.04 as a guest on win xp using virtualbox. Some how my vm was keep getting crashed with some annoying "network-manager" error. I uninstalled it as I don't need. Now I have no idea if this could be related to my problem or not.

I am trying to execute a simple bash file.
```

source "/home/prashant/installed/zeno-3.0/.zeno_bash"

```I tried copying this line into .bash_profile/.bash_login/.bashrc/.profile, but nothing work. The variables are not getting initialized of ".zeno_bash" .

Is this is some where related to "network-manager"? How do I solve the problem?


Prashant

---

### Post by gmargo on 2010-05-04
What is the content of the .zeno_bash file?

What result are you expecting to see?  What are you actually seeing?  Are you expecting to see this thing only on the command line, or also when executing a program from the menu?

If you are setting environment variables, are you exporting them correctly?  

Is the script really a bash script or a regular shell script?

(While I don't know what "zeno" is, it is highly unlikely that your problem has anything to do with the network-manager.  My guess is a syntax problem.)

---

