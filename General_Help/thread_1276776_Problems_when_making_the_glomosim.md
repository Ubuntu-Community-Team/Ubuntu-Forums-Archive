---
title: "Problems when making the glomosim"
date: 2009-09-27
forum: General Help
---

### Post by no_smile_know on 2009-09-27
Hey everybody, 
I got a problem when "make" the glomosim.
I edited some documents and made it. 
Then it comes out like as follow:
root@luck-laptop:~/glomosim/glomosim/main# make
pcc -g -O3 -I../include/ -I../transport -I../transport/tcp -I../application -I../mac -I../main -I../network -I../radio -clock longlong -lm -c ../network/nwip.pc
make: pcc: Command not found
make: *** [../network/nwip.o] Error 127
I'v already installed gcc. 
I will be appreciated for your kindly help.

---

### Post by boyz.226 on 2009-10-29
look up on [this ]("http://rupeshkushwaha.blogspot.com/2009/10/glomosim-with-ubuntu.html")link

---

