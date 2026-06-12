---
title: "how to make lcoal repo for deb packages?"
date: 2006-02-16
forum: General Help
---

### Post by shams2 on 2006-02-16
hi,
i find the brief instructions to make a local deb repo, but can't undrestand it, can any one tell me in which directory  i put the deb pakcages in this example, and in   which direcotry i should run the command install -d pool :

     # aptitude install dpkg-dev
     # cd /usr/local
     # install -d pool # physical packages are located here
     # install -d dists/unstable/main/binary-i386
     # ls -1 pool | sed 's/_.*$/ priority section/' | uniq > override
     # editor override # adjust priority and section
     # dpkg-scanpackages pool override /usr/local/ \
        > dists/unstable/main/binary-i386/Packages
     # cat > dists/unstable/main/Release << EOF
     Archive: unstable
     Version: 3.0
     Component: main
     Origin: Local
     Label: Local
     Architecture: i386
     EOF
     # echo "deb file:/usr/local unstable main" \
        >> /etc/apt/sources.list

---

### Post by o_fortuna on 2006-02-16
[QUOTE=shams2]hi,
i find the brief instructions to make a local deb repo, but can't undrestand it, can any one tell me in which directory  i put the deb pakcages in this example, and in   which direcotry i should run the command install -d pool :

     # aptitude install dpkg-dev
     # cd /usr/local
     # install -d pool # physical packages are located here
     # install -d dists/unstable/main/binary-i386
     # ls -1 pool | sed 's/_.*$/ priority section/' | uniq > override
     # editor override # adjust priority and section
     # dpkg-scanpackages pool override /usr/local/ \
        > dists/unstable/main/binary-i386/Packages
     # cat > dists/unstable/main/Release << EOF
     Archive: unstable
     Version: 3.0
     Component: main
     Origin: Local
     Label: Local
     Architecture: i386
     EOF
     # echo "deb file:/usr/local unstable main" \
        >> /etc/apt/sources.list[/QUOTE]
From what it looks like, your files should be in /usr/local/pool/dists/unstable/main/binary-i386, but that's just a guess. For me, I always felt like that was just too complicated; dpkg -i was always easier and faster.

---

### Post by StefanoCole on 2006-02-17
You can check the following link: [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html")
and read How to use APT locally

Stefano

---

