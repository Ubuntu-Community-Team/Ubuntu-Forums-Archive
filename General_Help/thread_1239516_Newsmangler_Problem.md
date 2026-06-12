---
title: "Newsmangler Problem"
date: 2009-08-13
forum: General Help
---

### Post by sddfdds on 2009-08-13
2009-08-13 11:45:18,008 [INFO] Using yenc-vanilla module for yEnc encoding.
Traceback (most recent call last):
  File "poster.py", line 146, in <module>
    main()
  File "poster.py", line 141, in main
    generate_par2=options.generate_par2)
  File "/newsmangler-20080806095105/classes/Poster.py", line 79, in post
    self.connect()
  File "/newsmangler-20080806095105/classes/BaseMangler.py", line 74, in connect
    conn.do_connect()
  File "/newsmangler-20080806095105/classes/asyncNNTP.py", line 56, in do_connect
    self.create_socket(socket.AF_INET, socket.SOCK_STREAM)
  File "/usr/lib/python2.6/asyncore.py", line 279, in create_socket
    self.set_socket(sock)
  File "/usr/lib/python2.6/asyncore.py", line 285, in set_socket
    self.add_channel(map)
TypeError: add_channel() takes exactly 1 argument (2 given)

I tried looking at the lines in each of the files, but it all makes no sense to me...does anyone know how to fix this?

Thanks

---

### Post by michy99 on 2009-08-13
never mind

---

### Post by sddfdds on 2010-01-25
anyone?

---

