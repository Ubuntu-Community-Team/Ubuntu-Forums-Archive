---
title: "MDK3-V6 Ubuntu 12.04 LTS HELP"
date: 2012-09-11
forum: General Help
---

### Post by MarkusGander on 2012-09-11
Hello,

I am trying to install the source code of MDK3 Version 6 ([http://homepages.tu-darmstadt.de/%7Ep_larbig/wlan/mdk3-v6.tar.bz2](http://homepages.tu-darmstadt.de/%7Ep_larbig/wlan/mdk3-v6.tar.bz2)) on 12.04 LTS, however I am running into a few problems making the file.

```

pwned@pwned:~/Arbeitsfläche/mdk3-v6$ sudo make
[sudo] password for pwned: 
make -C osdep
make[1]: Betrete Verzeichnis '/home/pwned/Arbeitsfläche/mdk3-v6/osdep'
Building for Linux
make[2]: Betrete Verzeichnis '/home/pwned/Arbeitsfläche/mdk3-v6/osdep'
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o osdep.o osdep.c
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o common.o common.c
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o network.o network.c
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o linux.o linux.c
linux.c: In Funktion »is_ndiswrapper«:
linux.c:165:17: Warnung: Variable »unused« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
linux.c: In Funktion »linux_set_rate«:
linux.c:334:22: Warnung: Variable »unused« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
linux.c: In Funktion »linux_set_channel«:
linux.c:807:22: Warnung: Variable »unused« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
linux.c: In Funktion »linux_set_freq«:
linux.c:896:22: Warnung: Variable »unused« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
linux.c: In Funktion »set_monitor«:
linux.c:1022:22: Warnung: Variable »unused« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
linux.c: In Funktion »do_linux_open«:
linux.c:1366:12: Warnung: Variable »unused_str« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
linux.c:1352:15: Warnung: Variable »unused« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
linux.c: In Funktion »get_battery_state«:
linux.c:1982:35: Warnung: Variable »current« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o linux_tap.o linux_tap.c
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o radiotap/radiotap-parser.o radiotap/radiotap-parser.c
ar cru libosdep.a  osdep.o common.o network.o linux.o linux_tap.o radiotap/radiotap-parser.o common.o
ranlib libosdep.a 
touch .os.Linux
make[2]: Verlasse Verzeichnis '/home/pwned/Arbeitsfläche/mdk3-v6/osdep'
make[1]: Verlasse Verzeichnis '/home/pwned/Arbeitsfläche/mdk3-v6/osdep'
cc -g -O3 -Wall -Wextra -lpthread mdk3.c osdep/libosdep.a -o mdk3 -Losdep -losdep
mdk3.c: In Funktion »read_line_from_file«:
mdk3.c:755:5: Warnung: Übergabe des Arguments 2 von »getline« von inkompatiblem Zeigertyp [standardmäßig aktiviert]
/usr/include/x86_64-linux-gnu/bits/stdio.h:116:1: Anmerkung: »size_t *« erwartet, aber Argument hat Typ »unsigned int *«
mdk3.c:760:2: Warnung: Übergabe des Arguments 2 von »getline« von inkompatiblem Zeigertyp [standardmäßig aktiviert]
/usr/include/x86_64-linux-gnu/bits/stdio.h:116:1: Anmerkung: »size_t *« erwartet, aber Argument hat Typ »unsigned int *«
mdk3.c: In Funktion »bruteforce_ssid«:
mdk3.c:809:32: Warnung: Typkonvertierung von Zeiger auf Ganzzahl anderer Breite [-Wpointer-to-int-cast]
mdk3.c:828:32: Warnung: Typkonvertierung von Zeiger auf Ganzzahl anderer Breite [-Wpointer-to-int-cast]
mdk3.c:847:32: Warnung: Typkonvertierung von Zeiger auf Ganzzahl anderer Breite [-Wpointer-to-int-cast]
mdk3.c:866:32: Warnung: Typkonvertierung von Zeiger auf Ganzzahl anderer Breite [-Wpointer-to-int-cast]
mdk3.c:888:32: Warnung: Typkonvertierung von Zeiger auf Ganzzahl anderer Breite [-Wpointer-to-int-cast]
mdk3.c:913:32: Warnung: Typkonvertierung von Zeiger auf Ganzzahl anderer Breite [-Wpointer-to-int-cast]
mdk3.c: In Funktion »ssid_brute_sniffer«:
mdk3.c:1512:9: Warnung: Variable »len« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
mdk3.c: In Funktion »mac_bruteforce_sniffer«:
mdk3.c:1926:9: Warnung: Variable »plen« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
mdk3.c: In Funktion »eapol_machine«:
mdk3.c:2560:17: Warnung: Variable »len« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
mdk3.c: In Funktion »check_probe«:
mdk3.c:3153:9: Warnung: Variable »len« gesetzt, aber nicht verwendet [-Wunused-but-set-variable]
mdk3.c: In Funktion »mdk_parser«:
mdk3.c:3393:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3409:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3413:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3431:5: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3436:5: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3494:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3535:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3555:9: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3565:15: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3569:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3574:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3602:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3608:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3630:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3636:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3640:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3655:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3663:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3672:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c: In Funktion »main«:
mdk3.c:3855:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3862:6: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3868:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3871:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3874:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3877:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3880:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3883:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3886:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3889:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3892:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3895:3: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3902:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3904:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3905:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3906:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3907:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3908:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3909:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3910:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3911:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
mdk3.c:3912:2: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente [-Wformat-security]
/tmp/cc8tFajx.o: In function `init_channel_hopper':
/home/pwned/Arbeitsfläche/mdk3-v6/mdk3.c:1269: undefined reference to `pthread_create'
/tmp/cc8tFajx.o: In function `ssid_brute':
/home/pwned/Arbeitsfläche/mdk3-v6/mdk3.c:2282: undefined reference to `pthread_create'
/tmp/cc8tFajx.o: In function `ssid_brute_real':
/home/pwned/Arbeitsfläche/mdk3-v6/mdk3.c:2332: undefined reference to `pthread_create'
/tmp/cc8tFajx.o: In function `intelligent_auth_dos':
/home/pwned/Arbeitsfläche/mdk3-v6/mdk3.c:2702: undefined reference to `pthread_create'
/tmp/cc8tFajx.o: In function `wids_machine':
/home/pwned/Arbeitsfläche/mdk3-v6/mdk3.c:2790: undefined reference to `pthread_create'
/tmp/cc8tFajx.o:/home/pwned/Arbeitsfläche/mdk3-v6/mdk3.c:2868: more undefined references to `pthread_create' follow
collect2: ld gab 1 als Ende-Status zurück
make: *** [mdk3] Fehler 1

```Try to change

LINKFLAGS    = -lpthread

to

LINKFLAGS = -pthread


HELP.....

---

