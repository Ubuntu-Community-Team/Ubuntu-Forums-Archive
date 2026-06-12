---
title: "Weird behaviour when installing zlib with make"
date: 2010-02-22
forum: General Help
---

### Post by me97esn on 2010-02-22
Hi, I am trying to install zlib, but can't get it to work.
This is what I am doing:
```
cd /tmp
wget http://www.gzip.org/zlib/zlib-1.2.3.tar.gz
gunzip zlib-1.2.3.tar.gz 
tar -xvf zlib-1.2.3.tar 
cd zlib-1.2.3/
sudo make clean
```But the output from the last line is:
```
emil@emils:/tmp/zlib-1.2.3$ sudo make clean
rm -f *.o *~ example minigzip \
       libz.* foo.gz so_locations \
       _match.s maketree contrib/infback9/*.o
```If I then try ```
sudo make install
```this is my output:
```
emil@emils:/tmp/zlib-1.2.3$ sudo make install
cp zlib.h zconf.h /usr/local/include
chmod 644 /usr/local/include/zlib.h /usr/local/include/zconf.h
cp libz.so.1.2.3 /usr/local/lib
cd /usr/local/lib; chmod 755 libz.so.1.2.3
cd /usr/local/lib; if test -f libz.so.1.2.3; then \
      rm -f libz.so libz.so.1; \
      ln -s libz.so.1.2.3 libz.so; \
      ln -s libz.so.1.2.3 libz.so.1; \
      (ldconfig || true)  >/dev/null 2>&1; \
    fi
cp zlib.3 /usr/local/share/man/man3
chmod 644 /usr/local/share/man/man3/zlib.3
emil@emils:/tmp/zlib-1.2.3$ 
```That's not what's supposed to happen is it? What's wrong?

---

### Post by nixclusive on 2010-02-22
perhaps you're missing the configuration step:
```
cd /tmp
wget http://www.gzip.org/zlib/zlib-1.2.3.tar.gz
tar xf zlib-1.2.3.tar.gz
cd zlib-1.2.3
make clean
**./configure**
make
sudo make install
```

Alternatively, you can use the package manager to install the package which should be a lot safer.

---

