---
title: "modified http_proxy via bash scripting"
date: 2009-10-03
forum: General Help
---

### Post by Ajat on 2009-10-03
Hi i made bash script program to change the proxy setting
```
#!/bin/bash
echo  "Enter your Username"
read -p "User: " user
echo -e "Enter your Password" 
read -s -p "Password: " pass
prox="http://$user:$word@152.118.24.10:8080"
export  http_proxy=$prox

```

but it appears that http_proxy doesn't change (from echo $http_proxy)
i dont want to edit .bashrc

then i also want to rename apt.conf via bash script. thanks

---

