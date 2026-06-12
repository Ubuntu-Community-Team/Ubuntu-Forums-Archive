---
title: "Installing MDK3-v6 on Ubuntu 11.10"
date: 2011-12-08
forum: General Help
---

### Post by Morfir on 2011-12-08
Hello,

I am trying to install the source code of MDK3 Version 6 ([Link]("http://homepages.tu-darmstadt.de/~p_larbig/wlan/")) on 11.10, however I am running into a few problems making the file.

```
#:~/Downloads/mdk3-v6$ sudo make
[sudo] password for #: 
make -C osdep
make[1]: Entering directory `/home/#/Downloads/mdk3-v6/osdep'
Building for Linux
make[2]: Entering directory `/home/#/Downloads/mdk3-v6/osdep'
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o osdep.o osdep.c
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o common.o common.c
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o network.o network.c
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o linux.o linux.c
linux.c: In function &#8216;is_ndiswrapper&#8217;:
linux.c:165:17: warning: variable &#8216;unused&#8217; set but not used [-Wunused-but-set-variable]
linux.c: In function &#8216;linux_set_rate&#8217;:
linux.c:334:22: warning: variable &#8216;unused&#8217; set but not used [-Wunused-but-set-variable]
linux.c: In function &#8216;linux_set_channel&#8217;:
linux.c:807:22: warning: variable &#8216;unused&#8217; set but not used [-Wunused-but-set-variable]
linux.c: In function &#8216;linux_set_freq&#8217;:
linux.c:896:22: warning: variable &#8216;unused&#8217; set but not used [-Wunused-but-set-variable]
linux.c: In function &#8216;set_monitor&#8217;:
linux.c:1022:22: warning: variable &#8216;unused&#8217; set but not used [-Wunused-but-set-variable]
linux.c: In function &#8216;do_linux_open&#8217;:
linux.c:1366:12: warning: variable &#8216;unused_str&#8217; set but not used [-Wunused-but-set-variable]
linux.c:1352:15: warning: variable &#8216;unused&#8217; set but not used [-Wunused-but-set-variable]
linux.c: In function &#8216;get_battery_state&#8217;:
linux.c:1982:35: warning: variable &#8216;current&#8217; set but not used [-Wunused-but-set-variable]
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o linux_tap.o linux_tap.c
gcc -g -W -Wall -Wextra -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=mdk3-v6  -fPIC -I..    -c -o radiotap/radiotap-parser.o radiotap/radiotap-parser.c
ar cru libosdep.a  osdep.o common.o network.o linux.o linux_tap.o radiotap/radiotap-parser.o common.o
ranlib libosdep.a 
touch .os.Linux
make[2]: Leaving directory `/home/#/Downloads/mdk3-v6/osdep'
make[1]: Leaving directory `/home/#/Downloads/mdk3-v6/osdep'
cc -g -O3 -Wall -Wextra -lpthread mdk3.c osdep/libosdep.a -o mdk3 -Losdep -losdep
mdk3.c: In function &#8216;read_line_from_file&#8217;:
mdk3.c:755:5: warning: passing argument 2 of &#8216;getline&#8217; from incompatible pointer type [enabled by default]
/usr/include/x86_64-linux-gnu/bits/stdio.h:116:1: note: expected &#8216;size_t *&#8217; but argument is of type &#8216;unsigned int *&#8217;
mdk3.c:760:2: warning: passing argument 2 of &#8216;getline&#8217; from incompatible pointer type [enabled by default]
/usr/include/x86_64-linux-gnu/bits/stdio.h:116:1: note: expected &#8216;size_t *&#8217; but argument is of type &#8216;unsigned int *&#8217;
mdk3.c: In function &#8216;bruteforce_ssid&#8217;:
mdk3.c:809:32: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
mdk3.c:828:32: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
mdk3.c:847:32: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
mdk3.c:866:32: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
mdk3.c:888:32: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
mdk3.c:913:32: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
mdk3.c: In function &#8216;ssid_brute_sniffer&#8217;:
mdk3.c:1512:9: warning: variable &#8216;len&#8217; set but not used [-Wunused-but-set-variable]
mdk3.c: In function &#8216;mac_bruteforce_sniffer&#8217;:
mdk3.c:1926:9: warning: variable &#8216;plen&#8217; set but not used [-Wunused-but-set-variable]
mdk3.c: In function &#8216;eapol_machine&#8217;:
mdk3.c:2560:17: warning: variable &#8216;len&#8217; set but not used [-Wunused-but-set-variable]
mdk3.c: In function &#8216;check_probe&#8217;:
mdk3.c:3153:9: warning: variable &#8216;len&#8217; set but not used [-Wunused-but-set-variable]
mdk3.c: In function &#8216;mdk_parser&#8217;:
mdk3.c:3393:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3409:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3413:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3431:5: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3436:5: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3494:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3535:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3555:9: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3565:15: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3569:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3574:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3602:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3608:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3630:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3636:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3640:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3655:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3663:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3672:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c: In function &#8216;main&#8217;:
mdk3.c:3855:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3862:6: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3868:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3871:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3874:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3877:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3880:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3883:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3886:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3889:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3892:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3895:3: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3902:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3904:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3905:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3906:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3907:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3908:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3909:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3910:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3911:2: warning: format not a string literal and no format arguments [-Wformat-security]
mdk3.c:3912:2: warning: format not a string literal and no format arguments [-Wformat-security]
/tmp/ccjoIFlH.o: In function `init_channel_hopper':
/home/#/Downloads/mdk3-v6/mdk3.c:1269: undefined reference to `pthread_create'
/tmp/ccjoIFlH.o: In function `ssid_brute':
/home/#/Downloads/mdk3-v6/mdk3.c:2282: undefined reference to `pthread_create'
/tmp/ccjoIFlH.o: In function `ssid_brute_real':
/home/#/Downloads/mdk3-v6/mdk3.c:2332: undefined reference to `pthread_create'
/tmp/ccjoIFlH.o: In function `intelligent_auth_dos':
/home/#/Downloads/mdk3-v6/mdk3.c:2702: undefined reference to `pthread_create'
/tmp/ccjoIFlH.o: In function `wids_machine':
/home/#/Downloads/mdk3-v6/mdk3.c:2790: undefined reference to `pthread_create'
/tmp/ccjoIFlH.o:/home/#/Downloads/mdk3-v6/mdk3.c:2868: more undefined references to `pthread_create' follow
collect2: ld returned 1 exit status
make: *** [mdk3] Error 1
#:~/Downloads/mdk3-v6$ 

```

I have been searching around and have found that there could be a problem with gcc, which I then tried... ([Link]("http://pastebin.com/rVbzUjyX")) However this did not fix the error. 

I checked the forum and found the same problem posted a while back but the problem was never resolved.

Does anyone have any advice on this situation?

Regards,
Morfir

---

### Post by Orhideous on 2011-12-09
Try to change
```
LINKFLAGS	= -lpthread
``` &#8594; ```
LINKFLAGS = -pthread
```

in **Makefile**.
Also, see [**this**]("http://stackoverflow.com/questions/1662909/undefined-reference-to-pthread-create-in-linux-c-programming").

---

