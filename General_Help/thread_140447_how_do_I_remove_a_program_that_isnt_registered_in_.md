---
title: "how do I remove a program that isnt registered in Synaptic?"
date: 2006-03-06
forum: General Help
---

### Post by wonderdog on 2006-03-06
hi,
How do I completely remove a program that I compiled with the 'make install' command? 
(ie it is not form a deb package and so is not registered with apt-get or Synaptic)

---

### Post by knalle on 2006-03-06
good source packages has a **./uninstall.sh** script or a **make uninstall** target, try that

---

### Post by wonderdog on 2006-03-06
Thanks - I tried that but no joy :-(
The package is qemu 0.8.0 and I installed it without the correct permissions. Now I need to recompile etc.
There is no uninstall.sh script and I get the following message from make uninstall:

$ make uninstall
make: *** No rule to make target `uninstall'.  Stop.

next time I'll do a checkinstall 

Any other suggestions?

---

### Post by codejunkie on 2006-03-06
like **knalle** said, but if you've already deleted the source package, like i have done a couple of times. you'll have to recompile it again with the same options you used the first time, then run ```
sudo make uninstall
``` from inside the source directory to uninstall it.

---

### Post by wonderdog on 2006-03-06
I haven't deleted the source package - I'm running the 'make uninstall' command from within the directory I compiled the package (the same one I tar -xvf'd it to).
I checked the qemu documentation briefly and see no uninstall instructions

---

### Post by knalle on 2006-03-06
if its a filthy source pack you will need to remove manually, walk trough the files, compare timestamps and delete.... :-S is there a better way?

---

### Post by wonderdog on 2006-03-06
thanks, I was really hoping there would be a nice easy command.
Oh well :(

---

### Post by codejunkie on 2006-03-06
[QUOTE=wonderdog]I haven't deleted the source package - I'm running the 'make uninstall' command from within the directory I compiled the package (the same one I tar -xvf'd it to).
I checked the qemu documentation briefly and see no uninstall instructions[/QUOTE]
try running ```
sudo make uninstall
```in the source directory if you just run```
make uninstall
```it won't work because you don't have root permissions.

---

### Post by wonderdog on 2006-03-06
no - I tried ' sudo make uninstall' - I still get the same message:

make: *** No rule to make target `uninstall'.  Stop.

---

### Post by MartinG on 2006-03-06
You could try recompiling but this time use checkinstall, with the same options.  This *should* re-install it, overwriting your first install, but this time registering it with apt.  After that you can use synaptic to remove it.

---

### Post by knalle on 2006-03-06
list the content of the **make** script

---

### Post by dbott67 on 2006-03-06
[QUOTE=wonderdog]no - I tried ' sudo make uninstall' - I still get the same message:

make: *** No rule to make target `uninstall'.  Stop.[/QUOTE]

Try re-installing it as root (i.e. using sudo) again and then 'sudo make uninstall'. 

-Dave

---

### Post by wonderdog on 2006-03-06
I think this is the make script (contents of Makefile)

-include config-host.mak

CFLAGS=-Wall -O2 -g -fno-strict-aliasing 
ifdef CONFIG_DARWIN
CFLAGS+= -mdynamic-no-pic
endif
LDFLAGS=-g
LIBS=
DEFINES+=-D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE
TOOLS=qemu-img$(EXESUF)
ifdef CONFIG_STATIC
LDFLAGS+=-static
endif
DOCS=qemu-doc.html qemu-tech.html qemu.1 qemu-img.1

all: dyngen$(EXESUF) $(TOOLS) $(DOCS)
	for d in $(TARGET_DIRS); do \
	$(MAKE) -C $$d $@ || exit 1 ; \
        done
ifdef CONFIG_KQEMU
ifdef CONFIG_WIN32
	$(MAKE) -C kqemu -f Makefile.winnt
else
	$(MAKE) -C kqemu
endif
endif

qemu-img$(EXESUF): qemu-img.c block.c block-cow.c block-qcow.c aes.c block-vmdk.c block-cloop.c block-dmg.c block-bochs.c block-vpc.c block-vvfat.c
	$(CC) -DQEMU_TOOL $(CFLAGS) $(LDFLAGS) $(DEFINES) -o $@ $^ -lz $(LIBS)

dyngen$(EXESUF): dyngen.c
	$(HOST_CC) $(CFLAGS) $(DEFINES) -o $@ $^

clean:
# avoid old build problems by removing potentially incorrect old files
	rm -f config.mak config.h op-i386.h opc-i386.h gen-op-i386.h op-arm.h opc-arm.h gen-op-arm.h 
	rm -f *.o *.a $(TOOLS) dyngen$(EXESUF) TAGS *.pod *~ */*~
	$(MAKE) -C tests clean
	for d in $(TARGET_DIRS); do \
	$(MAKE) -C $$d $@ || exit 1 ; \
        done
ifdef CONFIG_KQEMU
	$(MAKE) -C kqemu clean
endif

distclean: clean
	rm -f config-host.mak config-host.h
	for d in $(TARGET_DIRS); do \
	rm -rf $$d || exit 1 ; \
        done

KEYMAPS=da     en-gb  et  fr     fr-ch  is  lt  modifiers  no  pt-br  sv \
ar      de     en-us  fi  fr-be  hr     it  lv  nl         pl  ru     th \
common  de-ch  es     fo  fr-ca  hu     ja  mk  nl-be      pt  sl     tr

install: all 
	mkdir -p "$(bindir)"
	install -m 755 -s $(TOOLS) "$(bindir)"
	mkdir -p "$(datadir)"
	install -m 644 pc-bios/bios.bin pc-bios/vgabios.bin \
                       pc-bios/vgabios-cirrus.bin \
                       pc-bios/ppc_rom.bin pc-bios/video.x \
                       pc-bios/proll.elf \
                       pc-bios/linux_boot.bin "$(datadir)"
	mkdir -p "$(docdir)"
	install -m 644 qemu-doc.html  qemu-tech.html "$(docdir)"
ifndef CONFIG_WIN32
	mkdir -p "$(mandir)/man1"
	install qemu.1 qemu-img.1 "$(mandir)/man1"
	mkdir -p "$(datadir)/keymaps"
	install -m 644 $(addprefix keymaps/,$(KEYMAPS)) "$(datadir)/keymaps"
endif
	for d in $(TARGET_DIRS); do \
	$(MAKE) -C $$d $@ || exit 1 ; \
        done
ifdef CONFIG_KQEMU
	cd kqemu ; ./install.sh
endif

# various test targets
test speed test2: all
	$(MAKE) -C tests $@

TAGS: 
	etags *.[ch] tests/*.[ch]

cscope:
	rm -f ./cscope.*
	find . -name "*.[ch]" -print > ./cscope.files
	cscope -b

# documentation
%.html: %.texi
	texi2html -monolithic -number $<

qemu.1: qemu-doc.texi
	./texi2pod.pl $< qemu.pod
	pod2man --section=1 --center=" " --release=" " qemu.pod > $@

qemu-img.1: qemu-img.texi
	./texi2pod.pl $< qemu-img.pod
	pod2man --section=1 --center=" " --release=" " qemu-img.pod > $@

FILE=qemu-$(shell cat VERSION)

# tar release (use 'make -k tar' on a checkouted tree)
tar:
	rm -rf /tmp/$(FILE)
	cp -r . /tmp/$(FILE)
	( cd /tmp ; tar zcvf ~/$(FILE).tar.gz $(FILE) --exclude CVS )
	rm -rf /tmp/$(FILE)

# generate a binary distribution
tarbin:
	( cd / ; tar zcvf ~/qemu-$(VERSION)-i386.tar.gz \
	$(bindir)/qemu \
	$(bindir)/qemu-system-ppc \
	$(bindir)/qemu-system-sparc \
	$(bindir)/qemu-system-x86_64 \
	$(bindir)/qemu-system-mips \
	$(bindir)/qemu-system-arm \
	$(bindir)/qemu-i386 \
        $(bindir)/qemu-arm \
        $(bindir)/qemu-armeb \
        $(bindir)/qemu-sparc \
        $(bindir)/qemu-ppc \
        $(bindir)/qemu-mips \
        $(bindir)/qemu-mipsel \
        $(bindir)/qemu-img \
	$(datadir)/bios.bin \
	$(datadir)/vgabios.bin \
	$(datadir)/vgabios-cirrus.bin \
	$(datadir)/ppc_rom.bin \
	$(datadir)/video.x \
	$(datadir)/proll.elf \
	$(datadir)/linux_boot.bin \
	$(docdir)/qemu-doc.html \
	$(docdir)/qemu-tech.html \
	$(mandir)/man1/qemu.1 $(mandir)/man1/qemu-img.1 )

ifneq ($(wildcard .depend),)
include .depend
endif

---

### Post by wonderdog on 2006-03-06
don't stress over it any more - its getting late here in Australia and I need some sleep :-)
Thanks for the help! - I'll do the time stamp thing and then do as MartinG suggested in the morning.

---

