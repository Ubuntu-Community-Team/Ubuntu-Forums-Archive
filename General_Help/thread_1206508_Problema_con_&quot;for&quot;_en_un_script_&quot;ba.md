---
title: "Problema con &quot;for&quot; en un script &quot;bash&quot;"
date: 2009-07-07
forum: General Help
---

### Post by tirengarfio on 2009-07-07
Hola,

estoy intentando escribir un script para comprbar el puerto 22 de 4 IPs.


IPS={89.17.206.180,89.17.206.185,89.17.206.186,89.17.206.187}

for i in ${IPS}
do
nmap -p 22 {IPS}
done


Pero obtengo este error:

Failed to resolve given hostname/IP: {IPS}.  Note that you can't use '/mask' AND '1-4,7,100-' style IP ranges
WARNING: No targets were specified, so 0 hosts scanned.
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.14 seconds

Alguna idea?

---

### Post by Dynelight on 2009-07-07
Hola.
Estuve buscando un poco como funciona el For.
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html)
Probá así:

```

IPS={89.17.206.180,89.17.206.185,89.17.206.186,89.  17.206.187}

for i in $(IPS)
do
      nmap -p 22 $IPS
done

```

---

### Post by sisco311 on 2009-07-07
```

#!/bin/bash

IPS=( 89.17.206.180 89.17.206.185 89.17.206.186 89.17.206.187 )

for i in ${IPS[@]}; do
  nmap -p 22 $i
done

exit 0
```

---

