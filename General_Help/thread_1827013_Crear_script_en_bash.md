---
title: "Crear script en bash"
date: 2011-08-17
forum: General Help
---

### Post by waresoft on 2011-08-17
Hola a todos espero me puedan ayudar con lo siguiente.
Estoy intentando crear un script en Bash que me permita escoger entre varias opciones para decidir a que maquinas conectarme via ssh.
Pasa que por pega necesito conectarme a diferentes servidores y me da lata estar escribiendo el llamado a cada una siempre, por eso quiero medio automatizar esto.

Intente hacerlo pero siempre se conecta a la primera opción, les dejo el código y espero me puedan ayudar.

```
#!/bin/bash

r1=1
r2=2
r3=3

clear
echo "A que maquina desea conectar:"
echo "      1. Server 1
      2. Server 2
      3. Server 3"


echo "R:"; read r

if [ $r=$r1 ]

then

 ssh usuario@128.2.1.1

exit



elif [ $r=$r2 ]

then

 ssh usuario@128.2.1.2

exit

else [ $r=$r3 ]

  ssh usuario@128.2.1.3

fi
```

---

### Post by seawolf167 on 2011-08-17
I don't speak Spanish :( so if you can read this my only suggestion would be to visit the Spanish Forums [here]("http://www.ubuntu-es.org/?q=forum") for help in your language!

---

### Post by papibe on 2011-08-18
If the server addresses are sequential as in your example, you can do something very simple: use the variable you read to call ssh:
```
#!/bin/bash

clear

echo "A que maquina desea conectar:"
echo "      1. Server 1"
echo "      2. Server 2"
echo "      3. Server 3"

echo -n "R:"; read r

ssh usuario@128.2.1."$r"

```

Regards.

---

