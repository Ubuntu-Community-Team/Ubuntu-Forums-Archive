---
title: "question about using sudo in a bash script"
date: 2010-06-30
forum: General Help
---

### Post by RobertL on 2010-06-30
I invoke a bash script from a python script and the bash script contains a sudo line. I would like the user to have only 1 chance to supply the correct password to sudo. If she doesn't give the right pw I want sudo to exit with a non-zero exit code. Is there a way to make sudo do that?  I don't want the user to have to type control-C to get out of sudo if she doesn't know the pw.

This description of the situation is greatly simplified to make the question clear. I'm aware of alternate approaches to the task and I'm not looking for advice on whether this is a good thing to do.

---

