---
title: "Need to automate programs on linux computing node"
date: 2010-07-09
forum: General Help
---

### Post by 55 62 75 6E 74 75 6D 65 on 2010-07-09
Hi,

I am running several hundred instances of an open source program on a  login node of a computing cluster and need to automate these jobs with a  shell script. The software has a "batch mode" that allows everything to  be executed via shell script; however, the program seems to need a  terminal session for each instance. I have considered two options thus  far. First, using Xvfb with screen to run the interactive version, which  can handle up to about 30 instances at a time. I do not know if this is  possible, since the program uses a GUI. Second, I considered using  screen alone with the batch mode, but once the computations exceed 500  this means over ten ssh sessions. I guess a script could be written to  so this, but I am not sure how.

Thanks,

55 62 75 6E 74 75 6D 65

---

