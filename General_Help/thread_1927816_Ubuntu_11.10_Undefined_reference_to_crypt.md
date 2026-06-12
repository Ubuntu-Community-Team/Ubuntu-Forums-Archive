---
title: "Ubuntu 11.10: Undefined reference to crypt"
date: 2012-02-18
forum: General Help
---

### Post by Reketsu on 2012-02-18
I have a problem with gcc, I'm completely stumped.
I program muds, but i recently upgraded from 10.04 to 11.10 Because i was tired of doing something and getting auto logged out for no reason.
 
Now when i compile my mud theres no problems until the very end when i get
act_comm.c: Undefined reference to 'crypt'
comm.c: Undefined reference to 'crypt'
 
etc
 
This is my makefile
 
 
CC = gcc
#PROF = -p
 
# Uncomment the line below if you have problems with math functions
#MATH_LINK = -lm
 
# Uncomment the two lines below if compiling on a Solaris box
#SOLARIS_FLAG = -Dsun -DSYSV
#SOLARIS_LINK = -lnsl -lsocket
 
#Uncomment the line below if you are getting a line like:
#interp.c:757: warning: int format, time_t arg (arg 7)
#TIME = -DTIMEFORMAT
 
#Uncomment the line below if you are getting implicit decleration of re_exec
#REG = -DREGEX
 
#Uncomment the line below if you are getting undefined re_exec errors
#NEED_REG = -lgnuregex
 
#Uncomment the line below if you are getting undefined crypt errors
NEED_CRYPT = -lcrypt
 
#DBUGFLG = -DREQUESTS
 
#Uncomment the line below if you want a performance increase though beware
#your core files may not be as much of a benefit if you do.
#OPT_FLAG = -finline-functions -funroll-loops -fdefer-pop -fstrength-reduce
 
#C_FLAGS = $(OPT_FLAG) -O -g3 -Wall -Wuninitialized $(PROF) $(NOCRYPT) $(DBUGFLG) -DSMAUG $(SOLARIS_FLAG) $(TIME) $(REG)
C_FLAGS = $(OPT_FLAG) -g3 -Wuninitialized $(PROF) $(NOCRYPT) $(DBUGFLG) -DSMAUG $(SOLARIS_FLAG) $(TIME) $(REG)
L_FLAGS = $(OPT_FLAG) $(PROF) $(SOLARIS_LINK) $(NEED_CRYPT) $(NEED_REG) ${MATH_LINK} -lz
 
#Uncomment the next three comments below if you want to use IMC
#USE_IMC = -DUSE_IMC
 
#IMC_OFILES = imc.o imc-mail.o imc-interp.o imc-util.o imc-config.o \
# imc-events.o imc-version.o imc-mercbase.o ice.o icec.o icec-mercbase.o
 
#IMC_CFILES = imc.c imc-mail.c imc-interp.c imc-util.c imc-config.c \
# imc-events.c imc-version.c imc-mercbase.c ice.c icec.c icec-mercbase.c
 
O_FILES = $(patsubst %.c,o/%.o,$(C_FILES))
 
C_FILES = act_comm.c act_info.c act_move.c act_obj.c act_wiz.c bank.c boards.c \
build.c clans.c comm.c comments.c const.c db.c deity.c fight.c \
handler.c hashstr.c ibuild.c ident.c interp.c magic.c makeobjs.c \
mapout.c misc.c mpxset.c mud_comm.c mud_prog.c player.c polymorph.c \
requests.c reset.c save.c shops.c skills.c special.c tables.c \
track.c update.c grub.c stat_obj.c ban.c services.c planes.c \
imm_host.c $(IMC_CFILES) hotboot.c color.c board.c dbzskills.c space.c \
finger.c house.c editor.c dock.c changes.c hiscores.c renumber.c
 
H_FILES = $(wildcard .h)
 
all:
$(MAKE) -s smaug
 
clean:
rm -f o/*.o smaug *~
 
smaug: $(O_FILES)
rm -f smaug
$(CC) $(L_FLAGS) $(USE_IMC) -o smaug $(O_FILES)
echo "Done compiling mud.";
chmod g+w smaug
chmod a+x smaug
chmod g+w $(O_FILES)
 
o/%.o: %.c
echo " Compiling DBZ:IW - [$@]";
$(CC) -c $(C_FLAGS) $< -o $@
 
.c.o: mud.h
$(CC) -c $(C_FLAGS) $(USE_IMC) $<
 
 
Any kind of help would be apprechiated so i can get back on track.
 
Thanks guys :)

---

