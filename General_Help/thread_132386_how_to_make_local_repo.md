---
title: "how to make local repo?"
date: 2006-02-18
forum: General Help
---

### Post by shams2 on 2006-02-18
hi,
these are steps to make a local repo:
     1: aptitude install dpkg-dev
     2: cd /usr/local
     3: install -d pool # physical packages are located here
     4: install -d dists/unstable/main/binary-i386
     5: ls -1 pool | sed 's/_.*$/ priority section/' | uniq > override
     6: editor override # adjust priority and section
     7: dpkg-scanpackages pool override /usr/local/ \
        > dists/unstable/main/binary-i386/Packages
     9: cat > dists/unstable/main/Release << EOF
     Archive: unstable
     Version: 3.0
     Component: main
     Origin: Local
     Label: Local
     Architecture: i386
     EOF
     10: echo "deb file:/usr/local unstable main" \
        >> /etc/apt/sources.list
and this is my progress:

1: dpkg-dev is installed
2: opened the /usr/local/
3: made a direcotry in with ls -d pool
4: made a tree of directories dists/unstable/main/binary-i386 with the 4th commmand and copied the .deb files to the last (binary-i386) direcotry.
5: when i run the 5th command in the current direcotry which is /usr/local it just created a empyty override file. i din't know if it the right way. and noe these are the content of the current directory:
dists  override  pool
6: opened the empty override file don't know how to set priority.
7: when run the 7th command from current diretory this is the error:
Usage: dpkg-scanpackages [-u] [-a<arch>] binarypath overridefile [pathprefix] > Packages
pleas help me.

---

### Post by soongwoo on 2006-04-16
Could you explain it in details?
I mean with more description for why ...

Thanks
soongwoo

---

