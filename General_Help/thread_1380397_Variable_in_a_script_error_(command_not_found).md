---
title: "Variable in a script error (command not found)"
date: 2010-01-13
forum: General Help
---

### Post by xzased on 2010-01-13
I have the following script:

```
#!/bin/bash

for HOSTS in  server01 server02 server03 
do
echo "Connecting to $HOSTS"
echo "Resetting Password"
echo ""
ssh $HOSTS  '\pass=test && (echo $pass; echo $pass) | passwd --stdin testuser;\'
echo "Finished job on $HOSTS"
echo ""

done

```

When I run the script I get an error message on the hosts that says: pass=test command not found. Any ideas why is not taking it as a variable? Thanks

---

### Post by xzased on 2010-01-13
Nevermind. Got it

---

