---
title: "Broken dependencies?"
date: 2006-03-21
forum: General Help
---

### Post by alegomes on 2006-03-21
Hi there. I'm using Ubuntu 5.10 and I wanna compile the kaffe virtual machine (kaffe.org).

When I run the configure script, I get the following error:

```
alegomes@minnie:~/tmp/kaffe-1.1.6$ ./configure --prefix=/opt/kaffe-1.1.6
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

I've read somewhere that if I install g++ my problem would be solved.

Then I tried to install g++. (Sorry, now, everything is in portuguese):

```
alegomes@minnie:~/tmp/kaffe-1.1.6$ sudo apt-get install g++
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Alguns pacotes não puderam ser instalados. Isso pode significar que
você solicitou uma situação impossível ou se você está usando a
distribuição instável, que alguns pacotes requeridos não foram
criados ainda ou foram tirados do Incoming.

Já que você solicitou uma única operação é bem provável que o pacote
esteja simplesmente não instalável e um relato de erro sobre esse
pacotes deve ser enviado.
A informação a seguir pode ajudar a resolver a situação:

Os pacotes a seguir têm dependências desencontradas:
  g++: Depende: g++-4.0 (>= 4.0.1-2) mas não vai ser instalado
E: Pacotes quebrados
```

Ok, so I tried to install g++-4.0

```
alegomes@minnie:~/tmp/kaffe-1.1.6$ sudo apt-get install g++-4.0
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Alguns pacotes não puderam ser instalados. Isso pode significar que
você solicitou uma situação impossível ou se você está usando a
distribuição instável, que alguns pacotes requeridos não foram
criados ainda ou foram tirados do Incoming.

Já que você solicitou uma única operação é bem provável que o pacote
esteja simplesmente não instalável e um relato de erro sobre esse
pacotes deve ser enviado.
A informação a seguir pode ajudar a resolver a situação:

Os pacotes a seguir têm dependências desencontradas:
  g++-4.0: Depende: gcc-4.0-base (= 4.0.1-4ubuntu9) mas 4.0.2-5 está para ser instalado
           Depende: gcc-4.0 (= 4.0.1-4ubuntu9) mas 4.0.2-5 está para ser instalado
           Depende: libstdc++6-4.0-dev (= 4.0.1-4ubuntu9) mas não vai ser instalado
E: Pacotes quebrados
```

Then, gcc-4.0

```
alegomes@minnie:~/tmp/kaffe-1.1.6$ sudo apt-get install gcc-4.0
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
gcc-4.0 já é a versão mais nova.
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 1 não atualizados.
```

Oh, it looks good. So, why is it being complained?

 Now, I'll try to install the  libstdc++6-4.0-dev package:

```
alegomes@minnie:~/tmp/kaffe-1.1.6$ sudo apt-get install libstdc++6-4.0-dev
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Alguns pacotes não puderam ser instalados. Isso pode significar que
você solicitou uma situação impossível ou se você está usando a
distribuição instável, que alguns pacotes requeridos não foram
criados ainda ou foram tirados do Incoming.

Já que você solicitou uma única operação é bem provável que o pacote
esteja simplesmente não instalável e um relato de erro sobre esse
pacotes deve ser enviado.
A informação a seguir pode ajudar a resolver a situação:

Os pacotes a seguir têm dependências desencontradas:
  libstdc++6-4.0-dev: Depende: gcc-4.0-base (= 4.0.1-4ubuntu9) mas 4.0.2-5 está para ser instalado
                      Depende: g++-4.0 (= 4.0.1-4ubuntu9) mas não vai ser instalado
E: Pacotes quebrados
```

Then, gcc-4.0-base:

```
alegomes@minnie:~/tmp/kaffe-1.1.6$ sudo apt-get install gcc-4.0-base
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
gcc-4.0-base já é a versão mais nova.
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 1 não atualizados.
```

Dammit. Seems ok too.

Ok, meybe the problem is on g++-4.0 

```
alegomes@minnie:~/tmp/kaffe-1.1.6$ sudo apt-get install g++-4.0
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Alguns pacotes não puderam ser instalados. Isso pode significar que
você solicitou uma situação impossível ou se você está usando a
distribuição instável, que alguns pacotes requeridos não foram
criados ainda ou foram tirados do Incoming.

Já que você solicitou uma única operação é bem provável que o pacote
esteja simplesmente não instalável e um relato de erro sobre esse
pacotes deve ser enviado.
A informação a seguir pode ajudar a resolver a situação:

Os pacotes a seguir têm dependências desencontradas:
  g++-4.0: Depende: gcc-4.0-base (= 4.0.1-4ubuntu9) mas 4.0.2-5 está para ser instalado
           Depende: gcc-4.0 (= 4.0.1-4ubuntu9) mas 4.0.2-5 está para ser instalado
           Depende: libstdc++6-4.0-dev (= 4.0.1-4ubuntu9) mas não vai ser instalado
E: Pacotes quebrados
```


Could you, please, help me? Do you guess why this is not going on?

thank you all!
Ale!

---

### Post by engla on 2006-03-21
I'm not sure about the details, but the first thing you should install when you need to compile is **build-essential**

sudo apt-get install build-essential

This will install gcc, g++ and *other things that are deemed essential*, like make.

---

### Post by alegomes on 2006-03-22
Didn't work :-(   

```
alegomes@minnie:~/tmp$ sudo apt-get install build-essential
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Alguns pacotes não puderam ser instalados. Isso pode significar que
você solicitou uma situação impossível ou se você está usando a
distribuição instável, que alguns pacotes requeridos não foram
criados ainda ou foram tirados do Incoming.

Já que você solicitou uma única operação é bem provável que o pacote
esteja simplesmente não instalável e um relato de erro sobre esse
pacotes deve ser enviado.
A informação a seguir pode ajudar a resolver a situação:

Os pacotes a seguir têm dependências desencontradas:
  build-essential: Depende: g++ (>= 4:4.0) mas não vai ser instalado
E: Pacotes quebrados
```

regards

---

### Post by Ramses de Norre on 2006-03-22
Could you translate the error messages?

---

### Post by alegomes on 2006-03-22
I'm not sure about the best translation, but it's something related to broken packages. It says that a package depends of another one but that another one will not be installed.

Does it make sense for you?

thank you, friends.

---

