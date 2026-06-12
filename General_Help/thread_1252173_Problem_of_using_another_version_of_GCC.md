---
title: "Problem of using another version of GCC"
date: 2009-08-28
forum: General Help
---

### Post by jackyang on 2009-08-28
Hi
I'm not sure if here is the best place to ask this question, but I feel people here are very generous and helpful. So I post it here.

I'm trying to build a library on my university's server recently. The problem is the library needs GCC version higher or equal to 4.3. On the server it has only GCC 4.1.

So I need to install another GCC on the server, since I don't have root privilege to upgrade the original GCC. So here's what I did:
```

$ tar xzvf gcc-4.3.4.tar.gz -C ./src
$ mkdir obj
$ cd obj
$ $HOME/src/gcc-4.3.4/configure --prefix=$HOME/bin/gcc-4.3.4
$ make
$ make install
```
Everything goes well till here. But when I try to use this version of gcc to configure my library:
```

$ export CC=$HOME/bin/gcc-4.3.4
$ $HOME/src/[mylib]/configure --prefix=$HOME/bin/[mylib]
```
I got this:
```
checking for gcc... gcc-4.3.4
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```
I checked the config.log and found nothing informative.

Can someone help me figure out what's wrong with it?
Thanks.

---

