---
title: "Compiling pxclient errors."
date: 2011-05-07
forum: General Help
---

### Post by blubaustin on 2011-05-07
I am trying to compile pxclient so it is optimized but... I get these errors:

blubaustin@ubuntu:~/Downloads/pxclient_1.2.6$ make
g++ -march=k8-sse3 -O2 -pipe -Wall -Wno-deprecated  -I../ntl-5.5.2/include -c comm.c -o comm.o
In file included from comm.c:33:0:
keyfile.h:72:53: error: ‘ZZ’ has not been declared
comm.c: In function ‘int socket_open(settings_t*, int*)’:
comm.c:57:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:58:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:60:3: warning: deprecated conversion from string constant to ‘char*’
comm.c:64:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:70:3: warning: deprecated conversion from string constant to ‘char*’
comm.c:73:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:79:3: warning: deprecated conversion from string constant to ‘char*’
comm.c:82:2: warning: deprecated conversion from string constant to ‘char*’
comm.c: In function ‘int socket_send(int, char*)’:
comm.c:107:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:110:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:126:4: warning: deprecated conversion from string constant to ‘char*’
comm.c:133:2: warning: deprecated conversion from string constant to ‘char*’
comm.c: In function ‘int socket_receive(int, char*)’:
comm.c:156:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:160:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:169:2: warning: deprecated conversion from string constant to ‘char*’
comm.c: In function ‘int communicate(settings_t*, char*, char*)’:
comm.c:196:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:198:3: warning: deprecated conversion from string constant to ‘char*’
comm.c:202:2: warning: deprecated conversion from string constant to ‘char*’
comm.c: In function ‘int send_keyfile(settings_t*)’:
comm.c:227:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:245:3: warning: deprecated conversion from string constant to ‘char*’
comm.c:246:3: warning: deprecated conversion from string constant to ‘char*’
comm.c:250:2: warning: deprecated conversion from string constant to ‘char*’
comm.c: In function ‘int register_user(settings_t*)’:
comm.c:274:2: warning: deprecated conversion from string constant to ‘char*’
comm.c:285:3: warning: deprecated conversion from string constant to ‘char*’
make: *** [comm.o] Error 1


I have compiled an installed GMP and NTL so, I dont know what is wrong.

---

