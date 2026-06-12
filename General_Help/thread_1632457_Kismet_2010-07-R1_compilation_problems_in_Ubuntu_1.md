---
title: "Kismet 2010-07-R1 compilation problems in Ubuntu 10.10"
date: 2010-11-28
forum: General Help
---

### Post by sinnet on 2010-11-28
Hello. I am trying to compile Kismet 2010-07-R1 under Ubuntu 10.10. I already haunted which dependencies I needed to install, which include: build-essential libncurses5 libncurses5-dev libpcap0.8 libpcap0.8-dev but I am getting 2 strange warnings while I do ./configure:

> configure: WARNING: Using local radiotap headers

config.status: WARNING:  'Makefile.inc.in' seems to ignore the --datarootdir settingAfter running ./configure, I tried running make dep, and make.

make dep throws:

> Makefile:281: .depend: No such file or directory
Generating dependencies... 
make[1]: Entering directory `/home/luis/Downloads/kismet-2010-07-R1'
make[2]: Entering directory `/home/luis/Downloads/kismet-2010-07-R1'
make[2]: `.depend' is up to date.
make[2]: Leaving directory `/home/luis/Downloads/kismet-2010-07-R1'
make[1]: Leaving directory `/home/luis/Downloads/kismet-2010-07-R1'which seems to be fine but make command looks like it didn't finish, this are the last lines:

> g++ -I/usr/include/ncurses -Wall -g -O2 -c popenclient.cc -o popenclient.o 
g++ -I/usr/include/ncurses -Wall -g -O2 -c kis_clinetframe.cc -o kis_clinetframe.o 
g++ -I/usr/include/ncurses -Wall -g -O2 -c text_cliframe.cc -o text_cliframe.o 
g++ -I/usr/include/ncurses -Wall -g -O2 -c kis_panel_widgets.cc -o kis_panel_widgets.o 
g++ -I/usr/include/ncurses -Wall -g -O2 -c kis_panel_network.cc -o kis_panel_network.o 
g++ -I/usr/include/ncurses -Wall -g -O2 -c kis_panel_windows.cc -o kis_panel_windows.o 
g++ -I/usr/include/ncurses -Wall -g -O2 -c kis_panel_details.cc -o kis_panel_details.o 
g++ -I/usr/include/ncurses -Wall -g -O2 -c kis_panel_preferences.cc -o kis_panel_preferences.o 
g++ -I/usr/include/ncurses -Wall -g -O2 -c kis_panel_frontend.cc -o kis_panel_frontend.o 
g++ -I/usr/include/ncurses -Wall -g -O2 -c kismet_client.cc -o kismet_client.o 
g++ -rdynamic -o kismet_client util.o ringbuf.o messagebus.o configfile.o getopt.o soundcontrol.o timetracker.o ipc_remote.o clinetframework.o tcpclient.o popenclient.o kis_clinetframe.o text_cliframe.o kis_panel_widgets.o kis_panel_network.o kis_panel_windows.o kis_panel_details.o kis_panel_preferences.o kis_panel_frontend.o kismet_client.o -lstdc++ -ldl -lncurses -lpanelThen sudo checkinstall throws this:


> ========================= Installation results ===========================
make -e commoninstall
make[1]: Entering directory `/home/luis/Downloads/kismet-2010-07-R1'
mkdir -p /usr/local/etc
mkdir -p /usr/local/bin
if test -e kismet_client; then \
        echo "Installing client"; \
        /usr/bin/install -c -o "root" -g "root" -m 555 scripts/kismet /usr/local/bin/kismet; \
        /usr/bin/install -c -o "root" -g "root" -m 555 kismet_client /usr/local/bin/kismet_client; \
    fi;
Installing client
/usr/bin/install -c -o "root" -g "root" -m 555 kismet_server /usr/local/bin/kismet_server; 
/usr/bin/install -c -o "root" -g "root" -m 555 kismet_drone /usr/local/bin/kismet_drone;
mkdir -p /usr/local/share/man/man1
/usr/bin/install -c -o "root" -g "man" -m 644 man/kismet.1 /usr/local/share/man/man1/kismet.1
/usr/bin/install -c -o "root" -g "man" -m 644 man/kismet_drone.1 /usr/local/share/man/man1/kismet_drone.1
mkdir -p /usr/local/share/man/man5
/usr/bin/install -c -o "root" -g "man" -m 644 man/kismet.conf.5 /usr/local/share/man/man5/kismet.conf.5
/usr/bin/install -c -o "root" -g "man" -m 644 man/kismet_drone.conf.5 /usr/local/share/man/man5/kismet_drone.conf.5
mkdir -p /usr/local/share/kismet//wav/
mkdir: cannot create directory `/usr/local/share/kismet': No such file or directory
make[1]: *** [commoninstall] Error 1
make[1]: Leaving directory `/home/luis/Downloads/kismet-2010-07-R1'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.
I can't figure what is happening by myself, any advice?

Thanks

---

### Post by sinnet on 2010-11-28
User "_knudfl_" at [www.linuxquestions.org]("http://www.linuxquestions.org") gave me the solution:

> ./configure ends with this text :
Configuration complete. _Run 'make dep'_ to generate dependencies
and 'make' followed by 'make install' to compile and install.
 
                                                 [QUOTE]make[2]: `.depend' is up to date.    But it doesn't really matter, when "depend" is created. 
In Kismet, make will do it, when you omitted 'make dep'.


'checkinstall' will not work with all software.
To be expected by say every 50 application.
With Kismet, it is easy worked around :
Just do : '_sudo make install_' .. and next : 'sudo checkinstall'

[/QUOTE]

Posting here just in case someone searches for it.

---

