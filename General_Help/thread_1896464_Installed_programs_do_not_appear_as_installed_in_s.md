---
title: "Installed programs do not appear as installed in synaptic"
date: 2011-12-17
forum: General Help
---

### Post by yoramdavid on 2011-12-17
Hello all,

I have noticed that some of the programs installed are not listed as installed in synaptic or software management centre.
They do work and if I reinstall the application, they the appear as installed.

Is this a bug or just a corrupt system?

While reinstalling Audacity to confirm this, I just lost my gnom-panel again ! :(

---

### Post by jerrrys on 2011-12-18
sudo apt-get update

Will that give you any errors?

---

### Post by 2F4U on 2011-12-18
How did you install those applications?

---

### Post by yoramdavid on 2011-12-18
> **jerrrys said:**
> sudo apt-get update

Will that give you any errors?

Thank you jerrrys,

yes, there are errors, see below (I have trunkated to leave mostly the lines with errors):

```
yo@yoram-II:~$ sudo apt-get update
Ign http://ppa.launchpad.net karmic InRelease                                     
Ign http://ppa.launchpad.net oneiric InRelease                                    
Ign http://ppa.launchpad.net oneiric InRelease                                                                     
Ign http://ppa.launchpad.net oneiric Release                                      
Obter:7 http://ppa.launchpad.net oneiric Release [9757 B]                         
Err http://ppa.launchpad.net oneiric Release                                         
Err http://ppa.launchpad.net maverick/main Sources                            
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-pt_PT
Ign http://ppa.launchpad.net oneiric/main Translation-pt
Obtidos 1778 B em 58s (30 B/s)  
A ler as listas de pacotes... Pronto
W: Erro GPG: http://download.bitdefender.com bitdefender Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY A373FB480EC4FE05
W: Erro GPG: http://ppa.launchpad.net oneiric Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY 10B3F6FDBE35DEDD
W: Ocorreu um erro durante a verificação da assinatura. O repositório não está actualizado e serão utilizados os ficheiros anteriores de índice. Erro do GPG: http://ppa.launchpad.net oneiric Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY 95FABEFB4499973B

W: Erro GPG: http://ppa.launchpad.net oneiric Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY D702BF6B8C6C1EFD
W: Erro GPG: http://ppa.launchpad.net oneiric Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY 6AF0E1940624A220
W: Erro GPG: http://ppa.launchpad.net oneiric Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY 32B18A1260D8DA0B
W: Falhou obter http://ppa.launchpad.net/listen-devel/ppa/ubuntu/dists/karmic/Release  Unable to find expected entry 'main./source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Falhou obter http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu/dists/oneiric/Release  

W: Falhou obter http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/maverick/main/source/Sources  404  Not Found

W: Falhou obter http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/maverick/main/binary-amd64/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/maverick/main/binary-i386/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Falhou obter http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Falhou obter http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Falhou obter http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Falhou obter http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by yoramdavid on 2011-12-18
> **2F4U said:**
> How did you install those applications?

Thank you 2F4U,

Some from Synaptic, some from software centre and some from command-line.
But for instance, Audacity was installed from software centre and it later did not appeard as installed in there nor in synaptic.

---

### Post by jerrrys on 2011-12-18
First open up your software sources in and try the "find best server" option just to see if it might clear up any 404 errors.  If this cleared out any errors, please post.

If that did nothing you need to first make a copy of /etc/apt/sources.list and then edit out/remove all sources that refer to karmic and maverick.

Then you need to comment out (#) all "ppa"sources. A # in front of a line will deactivate that line.

And then, once again run sudo apt-get update.  If that now works without error; enter sudo apt-get upgrade

I hope this works.  If not, you may need to uncomment those ppa's and use ppa-purge.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ppa+purge&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ppa+purge&sa=Search&cof=FORID:9)

Option #2 would be a fresh install if this is a upgrade gone bad.

If you are unsure about editing your sources.list, please post it.

---

### Post by yoramdavid on 2011-12-18
> **jerrrys said:**
> First open up your software sources in and try the "find best server" option just to see if it might clear up any 404 errors.  If this cleared out any errors, please post.

If that did nothing you need to first make a copy of /etc/apt/sources.list and then edit out/remove all sources that refer to karmic and maverick.

Then you need to comment out (#) all "ppa"sources. A # in front of a line will deactivate that line.

And then, once again run sudo apt-get update.  If that now works without error; enter sudo apt-get upgrade

I hope this works.  If not, you may need to uncomment those ppa's and use ppa-purge.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ppa+purge&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ppa+purge&sa=Search&cof=FORID:9)

Option #2 would be a fresh install if this is a upgrade gone bad.

If you are unsure about editing your sources.list, please post it.

Thank you jerrrys,

I tried the "find best server" option, but either the Internet is too slow where I am at the moment (not at home) and it got stuck at about 50% of searching.

In the sofware centre, I have about 20 entries, and in the sources.list only 7 entries with only 2 from karmic which I commented with a "#".

I still got 404 errors with the"sudo apt-get update" command.

I will check the purge command tomorrow.

I will definetly do a fresh install once I get home, this is not a fresh install, it is an upgrade from Ubuntu 10.10 which was also an upgrade from 10.04.

---

