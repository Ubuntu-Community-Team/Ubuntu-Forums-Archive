---
title: "Forcing make command?"
date: 2009-08-10
forum: General Help
---

### Post by Morfi777 on 2009-08-10
Hi,

I'm doing make, everything compiles, fine.

After that I make some changes in files and do make again.

After that I got info: nothing to be done...

I know that there is command make -B to force making again but it checks all files, how can I force him to recompile only the files which I changed ?


Cheers

---

### Post by dlmarti on 2009-08-10
Not knowing the package you are trying to compile, I would suggest doing a "make clean" if you believe that the build is out of date and make is not detecting it properly.

---

### Post by Morfi777 on 2009-08-10
> **dlmarti said:**
> Not knowing the package you are trying to compile, I would suggest doing a "make clean" if you believe that the build is out of date and make is not detecting it properly.

Oh yeah but it still start to recomplile all files.


Before it was like that:
I have 20 cpp and 20 h

They have to compile ALL at the first time
After that I changed 2 cpp and 1 h file (for example) and run make again. Then script compliled ONLY those 2 cpp and 1 h but now it shows me that there is nothing to do and I have to recompile ALL files every time :/

---

### Post by regala on 2009-08-10
> **Morfi777 said:**
> Hi,

I'm doing make, everything compiles, fine.

After that I make some changes in files and do make again.

After that I got info: nothing to be done...

I know that there is command make -B to force making again but it checks all files, how can I force him to recompile only the files which I changed ?


Cheers

either your Makefile is wrong, or you don't really save the changes :)
can you show us the content of your Makefile ?

---

### Post by Morfi777 on 2009-08-10
> **regala said:**
> either your Makefile is wrong, or you don't really save the changes :)
can you show us the content of your Makefile ?

Sure:

```
SHELL = /bin/sh
SYSTEM = $(shell uname)
C++ = g++
CC = gcc
DFLAGS = -DGHOST_MYSQL
OFLAGS = -O3
LFLAGS = -L. -L../bncsutil/src/bncsutil/ -L../StormLib/stormlib/ -lbncsutil -lpthread -ldl -lz -lStorm -lmysqlclient_r -lboost_date_time-mt -lboost_thread-mt -lboost_system-mt -lboost_filesystem-mt -lboost_regex-mt
CFLAGS =

ifeq ($(SYSTEM),Darwin)
DFLAGS += -D__APPLE__
OFLAGS += -flat_namespace
else
LFLAGS += -lrt
endif

ifeq ($(SYSTEM),FreeBSD)
DFLAGS += -D__FREEBSD__
endif

ifeq ($(SYSTEM),SunOS)
DFLAGS += -D__SOLARIS__
LFLAGS += -lresolv -lsocket -lnsl
endif

CFLAGS += $(OFLAGS) $(DFLAGS) -I. -I../bncsutil/src/ -I../StormLib/

ifeq ($(SYSTEM),Darwin)
CFLAGS += -I../mysql/include/
endif

OBJS = bncsutilinterface.o bnet.o bnetprotocol.o bnlsclient.o bnlsprotocol.o commandpacket.o config.o crc32.o csvparser.o game.o game_base.o gameplayer.o gameprotocol.o gameslot.o ghost.o ghostdb.o ghostdbmysql.o ghostdbsqlite.o language.o map.o packed.o replay.o savegame.o sha1.o socket.o stats.o statsdota.o statsw3mmd.o util.o
COBJS = sqlite3.o
PROGS = ./ghost++

all: $(OBJS) $(COBJS) $(PROGS)

./ghost++: $(OBJS) $(COBJS)
	$(C++) -o ./ghost++ $(OBJS) $(COBJS) $(LFLAGS)

clean:
	rm -f $(OBJS) $(COBJS) $(PROGS)

$(OBJS): %.o: %.cpp
	$(C++) -o $@ $(CFLAGS) -c $<

$(COBJS): %.o: %.c
	$(CC) -o $@ $(CFLAGS) -c $<

./ghost++: $(OBJS) $(COBJS)

all: $(PROGS)

bncsutilinterface.o: ghost.h util.h bncsutilinterface.h
bnet.o: ghost.h util.h config.h language.h socket.h commandpacket.h ghostdb.h bncsutilinterface.h bnlsclient.h bnetprotocol.h bnet.h map.h packed.h savegame.h gameprotocol.h game.h
bnetprotocol.o: ghost.h util.h bnetprotocol.h
bnlsclient.o: ghost.h util.h socket.h commandpacket.h bnlsprotocol.h bnlsclient.h
bnlsprotocol.o: ghost.h util.h bnlsprotocol.h
commandpacket.o: ghost.h commandpacket.h
config.o: ghost.h config.h
crc32.o: ghost.h crc32.h
csvparser.o: csvparser.h
game.o: ghost.h util.h config.h language.h socket.h ghostdb.h bnet.h map.h packed.h savegame.h gameplayer.h gameprotocol.h game_base.h game.h stats.h statsdota.h statsw3mmd.h
game_base.o: ghost.h util.h config.h language.h socket.h ghostdb.h bnet.h map.h packed.h savegame.h replay.h gameplayer.h gameprotocol.h game_base.h
gameplayer.o: ghost.h util.h language.h socket.h commandpacket.h bnet.h map.h gameplayer.h gameprotocol.h game_base.h
gameprotocol.o: ghost.h util.h crc32.h gameplayer.h gameprotocol.h game_base.h
gameslot.o: ghost.h gameslot.h
ghost.o: ghost.h util.h crc32.h sha1.h csvparser.h config.h language.h socket.h ghostdb.h ghostdbsqlite.h ghostdbmysql.h bnet.h map.h packed.h savegame.h gameprotocol.h game_base.h game.h
ghostdb.o: ghost.h util.h config.h ghostdb.h
ghostdbmysql.o: ghost.h util.h config.h ghostdb.h ghostdbmysql.h
ghostdbsqlite.o: ghost.h util.h config.h ghostdb.h ghostdbsqlite.h
language.o: ghost.h config.h language.h
map.o: ghost.h util.h crc32.h sha1.h config.h map.h
packed.o: ghost.h util.h crc32.h packed.h
replay.o: ghost.h util.h packed.h replay.h gameprotocol.h
savegame.o: ghost.h util.h packed.h savegame.h
sha1.o: sha1.h
socket.o: ghost.h util.h socket.h
stats.o: ghost.h stats.h
statsdota.o: ghost.h util.h ghostdb.h gameplayer.h gameprotocol.h game_base.h stats.h statsdota.h
statsw3mmd.o: ghost.h util.h ghostdb.h gameprotocol.h game_base.h stats.h statsw3mmd.h
util.o: ghost.h util.h

```

---

