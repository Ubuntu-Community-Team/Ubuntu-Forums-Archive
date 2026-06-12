---
title: "winegcc: gcc-4.5 failed"
date: 2011-01-21
forum: General Help
---

### Post by aenima1891 on 2011-01-21
I'm trying to compile wineasio in Ubuntu 10.10
I've this error during compile...

```
aenima1891@aenima1891-Aspire-5735:~/wineasio$ make
pkg-config --exists jack
winegcc -m32 -shared wineasio.dll.spec -mnocygwin -o wineasio.dll.so asio.o main.o regsvr.o     -ljack  -lodbc32 -lole32 -loleaut32 -lwinspool -lwinmm -lpsapi -lpthread -luuid
winegcc: gcc-4.5 failed
make: *** [wineasio.dll.so] Error 2
aenima1891@aenima1891-Aspire-5735:~/wineasio$ make -lshlwapi
pkg-config --exists jack
winegcc -m32 -shared wineasio.dll.spec -mnocygwin -o wineasio.dll.so asio.o main.o regsvr.o     -ljack  -lodbc32 -lole32 -loleaut32 -lwinspool -lwinmm -lpsapi -lpthread -luuid
winegcc: gcc-4.5 failed
make: *** [wineasio.dll.so] Error 2

```

Can someone help me? thanks!!:)

---

### Post by aenima1891 on 2011-02-02
up

---

### Post by billstei on 2011-04-13
Install (using Synaptic or however you prefer) package gcc-4.5

---

