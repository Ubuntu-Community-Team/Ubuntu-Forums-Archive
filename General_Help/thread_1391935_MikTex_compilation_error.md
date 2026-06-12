---
title: "MikTex compilation error"
date: 2010-01-27
forum: General Help
---

### Post by emagar on 2010-01-27
Greetings from Mexico City!

I am newish in the Linux world (Ubuntu 9.10). 

I've been trying to install MikTex without success. The .deb files inevitably lead to an error (system feedback rather uninformative). I next tried to compile the source code I downloaded from the MikTex web page. I untarred it and ran  the following commands with no errors:

```
cmake -G "Unix Makefiles"
make
sudo make install
sudo initexmf --admin --configure

```But when I get to the next command:

```
sudo mpm --admin --update-db

```the machine responds with a puzzling

```
mpm: LZMA decoder error.

```Forum threads offer little information on this. 

I will be grateful for clues...

Gracias!

--Eric

---

