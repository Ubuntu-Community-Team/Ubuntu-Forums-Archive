---
title: "Bumblebee wants to remove my libc-bin"
date: 2012-08-14
forum: General Help
---

### Post by rrrobles on 2012-08-14
I followed the instructions to install bumblebee, but it wants to remove my libc-bin!
I'm using Ubuntu 11.10

```
sudo apt-get install bumblebee bumblebee-nvidia
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Os pacotes extra a seguir serão instalados:
  bbswitch-dkms gcc-4.6-base:i386 libc-bin:i386 libc-dev-bin libc6 libc6:i386
  libc6-dev libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386
  libdrm2:i386 libexpat1 libexpat1:i386 libffi6:i386 libgcc1:i386
  libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa libglapi-mesa:i386 libllvm2.9:i386 libpciaccess0:i386
  libstdc++6:i386 libx11-6:i386 libxau6:i386 libxcb1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxv1:i386 libxxf86vm1:i386
  nvidia-current nvidia-settings python-central screen-resolution-extra
  virtualgl virtualgl-libs virtualgl-libs:i386 virtualgl-libs-ia32:i386
  zlib1g:i386
Pacotes sugeridos:
  glibc-doc glibc-doc:i386 locales:i386 libglide3 libglide3:i386 pciutils:i386
Pacotes recomendados:
  virtualgl-libs-ia32
Os pacotes a seguir serão REMOVIDOS:
  libc-bin
Os NOVOS pacotes a seguir serão instalados:
  bbswitch-dkms bumblebee bumblebee-nvidia gcc-4.6-base:i386 libc-bin:i386
  libc6:i386 libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386
  libdrm2:i386 libexpat1:i386 libffi6:i386 libgcc1:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libllvm2.9:i386 libpciaccess0:i386
  libstdc++6:i386 libx11-6:i386 libxau6:i386 libxcb1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxv1:i386 libxxf86vm1:i386
  nvidia-current nvidia-settings python-central screen-resolution-extra
  virtualgl virtualgl-libs virtualgl-libs:i386 virtualgl-libs-ia32:i386
  zlib1g:i386
Os pacotes a seguir serão atualizados:
  libc-dev-bin libc6 libc6-dev libexpat1 libgl1-mesa-dri libgl1-mesa-glx
  libglapi-mesa
AVISO: Os pacotes essenciais a seguir serão removidos.
Isso NÃO deveria ser feito a menos que você saiba exatamente o que você está fazendo!
  libc-bin
7 pacotes atualizados, 37 pacotes novos instalados, 1 a serem removidos e 410 não atualizados.
É preciso baixar 83,7 MB de arquivos.
Depois desta operação, 224 MB adicionais de espaço em disco serão usados.
Você está prestes a fazer algo potencialmente destrutivo.
Para continuar digite a frase 'Sim, faça o que eu digo!'
 ?]
```

I tried it and Ubuntu stops working, so I reinstalled and got stuck at the same point. :confused:

---

### Post by rrrobles on 2012-08-14
Solved. After a complete package update it was installed correctly. :)

---

### Post by ttomisk on 2013-04-02
> **rrrobles said:**
> Solved. After a complete package update it was installed correctly. :)
Hi. I have same problem. How did you make a "complete package update"?
I wrote 
```
sudo apt-get update
```
and then tried to install Bumblebee, 
```
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic
```
but it still wants to remove libc-bin.

---

