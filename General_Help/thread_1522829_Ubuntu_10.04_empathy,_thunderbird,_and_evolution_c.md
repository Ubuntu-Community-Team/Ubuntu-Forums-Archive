---
title: "Ubuntu 10.04 empathy, thunderbird, and evolution crash"
date: 2010-07-02
forum: General Help
---

### Post by allpowerful32 on 2010-07-02
Hi,

When I run empathy, thunderbird, or evolution, all of them segfault, and they all appear to do so at the same place.  I am running a fresh install of Ubuntu 10.04 x86_64.

Here is the output when evolution is run under gdb:

starting program: /usr/bin/evolution 
[Thread debugging using libthread_db enabled]
** (evolution:10580): DEBUG: mailto URL command: evolution %s
** (evolution:10580): DEBUG: mailto URL program: evolution
[New Thread 0x7fffdce73710 (LWP 10585)]
[Thread 0x7fffdce73710 (LWP 10585) exited]
[New Thread 0x7fffdce73710 (LWP 10586)]
[New Thread 0x7fffd7fff710 (LWP 10587)]

Program received signal SIGSEGV, Segmentation fault.
__strncmp_ssse3 () at ../sysdeps/x86_64/multiarch/../strcmp.S:100
100    ../sysdeps/x86_64/multiarch/../strcmp.S: No such file or directory.
    in ../sysdeps/x86_64/multiarch/../strcmp.S
(gdb) bt
#0  __strncmp_ssse3 () at ../sysdeps/x86_64/multiarch/../strcmp.S:100
#1  0x00007fffef5faa6a in __xmlParserInputBufferCreateFilename ()
   from /usr/lib/libxml2.so.2
#2  0x00007fffef5cfd9d in xmlNewInputFromFile () from /usr/lib/libxml2.so.2
#3  0x00007fffef5d41c6 in xmlCreateURLParserCtxt () from /usr/lib/libxml2.so.2
#4  0x00007fffef5eaebc in xmlSAXUserParseFile () from /usr/lib/libxml2.so.2
#5  0x00007fffef8f8c67 in glade_parser_parse_file ()
   from /usr/lib/libglade-2.0.so.0
#6  0x00007fffef8f637a in glade_xml_construct ()
   from /usr/lib/libglade-2.0.so.0
#7  0x00007fffef8f7036 in glade_xml_new () from /usr/lib/libglade-2.0.so.0
#8  0x00007fffe0aa86d5 in ?? ()
   from /usr/lib/evolution/2.28/libevolution-mail-shared.so.0
#9  0x00007ffff5fcad46 in ?? () from /usr/lib/evolution/2.28/libeutil.so.0
#10 0x00007ffff5fcb15b in e_config_create_widget ()
   from /usr/lib/evolution/2.28/libeutil.so.0
#11 0x00007ffff5fcb1f6 in e_config_create_window ()
   from /usr/lib/evolution/2.28/libeutil.so.0
#12 0x00007fffe0aa8357 in ?? ()
   from /usr/lib/evolution/2.28/libevolution-mail-shared.so.0
#13 0x00007fffe0aabcc4 in em_account_editor_new ()
   from /usr/lib/evolution/2.28/libevolution-mail-shared.so.0
#14 0x00007fffdd095933 in startup_wizard ()
---Type <return> to continue, or q <return> to quit---

Stack traces from all three programs end in __strncmp_ssse3, called from __xmlParserInputBufferCreateFilename() from /usr/lib/libxml2.so.2, ..., so I suspect they are all suffering from the same problem, and that that problem is in libxml2.

I searched around on google for a while, to no avail.  Is this something I should file a bug report on?  If so, where?

Thanks in advance,

Joshua

---

