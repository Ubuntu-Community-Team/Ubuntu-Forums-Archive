---
title: "Crazy unresolvable circular dependency issues."
date: 2006-05-06
forum: General Help
---

### Post by raid517 on 2006-05-06
Hi I am trying to build a new kernel (that part at least is not hard). However in order to build my new kernel - I need some pretty important tools.

There include build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev (among some others).

However when I try to install these (particularly "build-essential") I get an error message saying that build essential depends on g++ but 'is not going to be installed'

if I try to apt-get g++ I get an error saying that 

```
g++:
 
Depends: g++-4.0 but it is not going to be installed
```

If I try to install g++ and g++-4.0 I get another error saying that

```
g++-4.0:
  Depends: gcc-4.0-base (=4.0.1-4ubuntu9) but 4.0.2-5ubuntu2 is to be installed
```

If I ignore this and try to install g++, g++-4.0 and gcc-4.0-base I get yet another error message saying

Depends: gcc-4.0 (=4.0.1-4ubuntu9) but 4.0.2-5ubuntu2 is to be installed if I again ignore this and try to install g++, g++-4.0, gcc-4.0-base and gcc-4.0 I get an error saying: 

Depends: libstdc++6-4.0-dev but it is not going to be installed. If I again ignore this and try to install libstdc++6-4.0-dev I get the following error:

```
Depends: cpp-4.0 but is not going to be installed. 
```

If I try to install cpp-4.0 I get this final error. (Or at least the last one before I give up).

```
The following packages have unmet dependencies:
cpp-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
g++-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
gcc-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
gij-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
libgcj6: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
libstdc++6-4.0-dev: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
```

So you see it is completely circular and unresolvable. The question is, has anyone got any clue what is going on - and better still, how to fix it?

I though Ubuntu was supposed to be easy to use?

GJ

---

### Post by Sef on 2006-05-06
Have you added multiverse and universe to your repositories?

Here's a howto on how to do it.

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by raid517 on 2006-05-06
Yes I have enabled/uncommented the UNIVERSE entries (and pretty much all of the others too) in my /etc/sources.list file. However I don't recall ever seing anything there pertaining to 'mutiverse.' I don't tend to use Synaptic too much as i prefer the CLI as it is faster and more efficient - but in any case I did nothing other than enable all of the official sources that were presented to me - without adding any external repositories of my own.

So the question is, why would I end up with conflicting packages in this way?

GJ

---

