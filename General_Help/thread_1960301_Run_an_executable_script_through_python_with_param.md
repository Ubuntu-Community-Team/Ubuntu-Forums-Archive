---
title: "Run an executable script through python with paramiko"
date: 2012-04-17
forum: General Help
---

### Post by fra11 on 2012-04-17
I'm trying to run an executable script through Paramiko and  if in my script I ask for printing something I manage but if I ask to  make a directory it doesn't. Can anyone help me with that? Here is my  script. Thanks a lot
  ```

import paramiko
ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
ssh.connect('hostname', username='myusername')
cmd = "/home/cocktail2/vitalini/reverse_transforation/printing.sh"
stdin, stdout, stderr = ssh.exec_command(cmd)
print stdout.readlines()
ssh.close

```
  and prynting.sh looks like
  ```

#!/bin/bash
mkdir ./prova 
echo 'filebase is filebase'

```

---

### Post by wojox on 2012-04-17
Your trying to create a directory off of root. You would need Admin privledges.

If it's in your home directory try: 
```
mkdir ~/prova
```

---

### Post by fra11 on 2012-04-17
thank you very much, now it works. However, now I'm having the same issue while running through the shell script another shell script in background,

execute.sh

```

cd /home/cocktail2/vitalini/reverse_transforation
filebase1=$(echo $1)
mkdir /home/cocktail2/vitalini/reverse_transforation/$filebase1
cd /home/cocktail2/vitalini/reverse_transforation/$filebase1
cp /home/cocktail2/vitalini/cg_gro/cg_gro_zip/${filebase1}.gro ./
nohup /home/cocktail2/vitalini/reverse_transforation/reverse_transformation.sh $filebase1 &
cd /home/cocktail2/vitalini/reverse_transforation

``` 

While my pyton script looks like

```

#Import libraries
import os
import random
import subprocess
import time
import paramiko
import itertools
import commands

#make a list of the filse in a folder
#commands.getstatusoutput('/home/cocktail2/vitalini/reverse_transforation/printing.sh')  
lista = os.listdir('/home/cocktail2/vitalini/cg_gro/cg_gro_zip/')
#make a list of 100 random different elements from lista
element =[]
while len(element) < 100:
    nome = random.choice(lista)
    element.append(nome)
    if element.count(nome) > 1:
       element.remove(nome)
#create a list of hostnames
#print element
hostlist=[]
i=4
hostlist.append("hostaddress"% i)
login=[]
for x in range(len(hostlist)):
   ssh = paramiko.SSHClient()
   ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
   ssh.connect(hostlist[x], username='myhostname')
   stdin, stdout, strerr = ssh.exec_command("uptime")
   uptimeout = stdout.readlines()
   uptimesplit1 = uptimeout[0].split(', ')
   print uptimesplit1
   uptimesplit = uptimesplit1[3].split(': ')
   print uptimesplit
   login.append([uptimesplit[1],hostlist[x]])
   filebase1="300-125-260"
   cmd = "/home/cocktail2/vitalini/reverse_transforation/execute.sh %s" % filebase1
   stdin, stdout, stderr = ssh.exec_command(cmd)
   print stdout.readlines()
   ssh.close
 #sort the list login previously definded so that it goes from te lower load to the higher
#print login

```

Can you help mi with that too?
Thanks a lot

---

