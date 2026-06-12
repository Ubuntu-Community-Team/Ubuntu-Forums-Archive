---
title: "electric sheep from repo"
date: 2011-11-24
forum: General Help
---

### Post by boblizar on 2011-11-24
Checked out revision 84.

electricsheepguiMyDialog2.o: undefined reference to symbol 'boost::system::system_category()'

thus checkout 84 yet another failure....  i tried to move some boost dev into the operation but im going to put on my tin foil hat and do things im positive im good at :popcorn:


full error

/usr/bin/ld: electricsheepguiMyDialog2.o: undefined reference to symbol 'boost::system::system_category()'
/usr/bin/ld: note: 'boost::system::system_category()' is defined in DSO /usr/lib/libboost_system.so.1.46.1 so try adding it to the linker command line
/usr/lib/libboost_system.so.1.46.1: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[1]: *** [electricsheep-preferences] Error 1
make[1]: Leaving directory `/home/$USER/electricsheep-read-only/client_generic/MSVC/SettingsGUI'
make: *** [all-recursive] Error 1

update.....
electric sheep revision 89...
undefined reference to symbol 'boost::system::system_category()'

latest source requires some stuff....

```

sudo apt-get install libboost-all-dev libwww-curl-perl libgtop2-dev libavcodec-dev libtinyxml-dev libghc-glut-dev glee-dev

```

more to come

---

