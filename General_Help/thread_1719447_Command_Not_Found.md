---
title: "Command Not Found"
date: 2011-04-01
forum: General Help
---

### Post by tkaplan on 2011-04-01
I'm trying to execute this file in my directory and I've set the path to look into my folder. I've even changed my directory to the folder containing the file. However bash will not execute the file. The file is called bash init_gv.bash. Heres the inside content of the file ..

#!/bin/bash
# Environment Initialization Script for:
#
#    GaussView 3.09
#
#    Copyright 1996-2003 Semichem,Inc.
#
# Change this entry only:
export GV_DIR='/home/export/Gv-3.09'

# Leave this Section alone:
alias gv=$GV_DIR'/gview'
alias gview=$GV_DIR'/gview'
#
if [ "$LD_LIBRARY_PATH" ]
then
   export LD_LIBRARY_PATH=$GV_DIR'/lib:'$LD_LIBRARY_PATH
else
   export LD_LIBRARY_PATH=$GV_DIR/lib
fi
I think using this file will allow me to use the program that is currently installed in my directory. Any idea why this isn't working?

---

### Post by sillav on 2011-04-01
Is it executable?

chmod +x file.sh

---

### Post by Matt__ on 2011-04-01
//edit: removed incorrect statement :/

---

