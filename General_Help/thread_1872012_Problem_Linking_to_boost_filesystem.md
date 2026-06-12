---
title: "Problem Linking to boost filesystem"
date: 2011-10-29
forum: General Help
---

### Post by Lyuokdea on 2011-10-29
I seem to be having problems linking to the boost library, though it is installed on my system. Here is the compiler error I'm obtaining, when compiling a code which requires boost: (running on Natty Narwhal)

```

/usr/bin/ld: main.o: undefined reference to symbol 'boost::system::system_category()'
/usr/bin/ld: note: 'boost::system::system_category()' is defined in DSO /usr/lib/libboost_system.so.1.46.1 so try adding it to the linker command line
/usr/lib/libboost_system.so.1.46.1: could not read symbols: Invalid operation
```

I have tried adding compiler LDFLAGS to the configure script:

```

LDFLAGS="-lboost_filesystem -lboost_thread -L/usr/lib/libboost_system.so.1.46.1"

```

this does not seem to correct the problem. 

The installed versions of boost on my system are:

```

dpkg --get-selections | grep "boost"
libboost-date-time1.34.1                        deinstall
libboost-date-time1.38.0                        deinstall
libboost-date-time1.40.0                        deinstall
libboost-date-time1.46-dev                      install
libboost-date-time1.46.1                        install
libboost-dev                                    install
libboost-doc                                    install
libboost-filesystem1.34.1                       deinstall
libboost-filesystem1.38.0                       deinstall
libboost-filesystem1.40.0                       install
libboost-filesystem1.46-dev                     install
libboost-filesystem1.46.1                       install
libboost-graph1.34.1                            deinstall
libboost-graph1.38.0                            deinstall
libboost-graph1.40.0                            deinstall
libboost-iostreams1.34.1                        deinstall
libboost-iostreams1.38.0                        deinstall
libboost-iostreams1.40.0                        deinstall
libboost-iostreams1.42.0                        deinstall
libboost-iostreams1.46-dev                      install
libboost-iostreams1.46.1                        install
libboost-math1.38.0                             deinstall
libboost-mpi1.46-dev                            install
libboost-mpi1.46.1                              install
libboost-program-options1.34.1                  deinstall
libboost-program-options1.35.0                  deinstall
libboost-program-options1.38.0                  deinstall
libboost-program-options1.40.0                  install
libboost-program-options1.42.0                  deinstall
libboost-program-options1.46-dev                install
libboost-program-options1.46.1                  install
libboost-python1.34.1                           deinstall
libboost-python1.38.0                           deinstall
libboost-python1.40.0                           deinstall
libboost-random1.46-dev                         install
libboost-random1.46.1                           install
libboost-regex1.34.1                            deinstall
libboost-regex1.38.0                            deinstall
libboost-regex1.40.0                            install
libboost-regex1.46-dev                          install
libboost-regex1.46.1                            install
libboost-serialization1.34.1                    deinstall
libboost-serialization1.38.0                    deinstall
libboost-serialization1.40.0                    deinstall
libboost-serialization1.42.0                    install
libboost-serialization1.46-dev                  install
libboost-serialization1.46.1                    install
libboost-signals1.34.1                          deinstall
libboost-signals1.38.0                          deinstall
libboost-signals1.40.0                          deinstall
libboost-system-dev                             install
libboost-system1.38.0                           deinstall
libboost-system1.40.0                           install
libboost-system1.46-dev                         install
libboost-system1.46.1                           install
libboost-test1.34.1                             deinstall
libboost-test1.38.0                             deinstall
libboost-test1.40.0                             deinstall
libboost-thread1.34.1                           deinstall
libboost-thread1.38.0                           deinstall
libboost-thread1.40.0                           deinstall
libboost-thread1.46-dev                         install
libboost-thread1.46.1                           install
libboost-wave1.34.1                             deinstall
libboost-wave1.38.0                             deinstall
libboost-wave1.40.0                             deinstall
libboost1.46-dev                                install
libboost1.46-doc                                install

```

Can anybody provide a hand here?

Thanks,

~Lyuokdea

---

### Post by Lyuokdea on 2011-10-29
I keep trying different configure options, but to no avail, I currently have everything I can think of included:

```

./configure LDFLAGS="-lboost_filesystem -lboost_thread -lboost_system -L/usr/lib/libboost_system.so"  BOOST_LIBS="-L/usr/lib/libboost_system.so" CXXFLAGS="-lboost_filesystem -lboost_thread -lboost_system -L/usr/lib/libboost_system.so" CFLAGS="-lboost_filesystem -lboost_thread -lboost_system -L/usr/lib/libboost_system.so"

```

But this has not seemed to help either - there must be something obvious I'm missing.

~Lyuokdea

---

### Post by oldtimer7777 on 2011-10-29
> **Lyuokdea said:**
> I keep trying different configure options, but to no avail, I currently have everything I can think of included:

```

./configure LDFLAGS="-lboost_filesystem -lboost_thread -lboost_system -L/usr/lib/libboost_system.so"  BOOST_LIBS="-L/usr/lib/libboost_system.so" CXXFLAGS="-lboost_filesystem -lboost_thread -lboost_system -L/usr/lib/libboost_system.so" CFLAGS="-lboost_filesystem -lboost_thread -lboost_system -L/usr/lib/libboost_system.so"

```But this has not seemed to help either - there must be something obvious I'm missing.

~Lyuokdea

How long have you been running Wubi on that system?

---

### Post by Lyuokdea on 2011-10-29
> **oldtimer7777 said:**
> How long have you been running Wubi on that system?

I don't believe it's on there - I very recently updated to Narwhal, which seems to have broken this program.

I know the configure script above was a little ridiculous - but I figured I'd just try all the possible compiler options at once.

~Lyuokdea

---

### Post by Lyuokdea on 2011-10-30
Got it!

Not sure why, but switched back to g++-4.4 and it worked instantly - seems to be some problem with the linker in 4.6

~Lyuokdea

---

