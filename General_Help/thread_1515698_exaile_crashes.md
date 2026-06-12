---
title: "exaile crashes"
date: 2010-06-22
forum: General Help
---

### Post by ubunterooster on 2010-06-22
Turn exaile on, and the splash for it comes but exaile never appears itself. Starting it in the terminal I get:```
ubunterooster@ubunterooster-server ~ $ exaile
INFO    : Loading Exaile 0.3.1.1...
INFO    : Loading settings...
INFO    : Setting up deferred idle manager function...
INFO    : Loading plugins...
INFO    : Loading collection...
INFO    : Loading devices...
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 52, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 49, in main
    exaile = main.Exaile()
  File "/usr/lib/exaile/xl/main.py", line 84, in __init__
    self.__init()
  File "/usr/lib/exaile/xl/main.py", line 189, in __init
    location=os.path.join(xdg.get_data_dirs()[0], "covers"))
  File "/usr/lib/exaile/xl/cover.py", line 121, in __init__
    self.load()
  File "/usr/lib/exaile/xl/cover.py", line 330, in load
    data = pickle.load(f)
EOFError
Exception in thread Thread-4:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 484, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/exaile/xl/hal.py", line 66, in connect
    logger.warning("Failed to connect to HAL, " \
AttributeError: 'NoneType' object has no attribute 'warning'

ubunterooster@ubunterooster-server ~ $ 
```

Edit: I did a purge of it, then reinstalled. Problem remains.

---

### Post by ubunterooster on 2010-06-23
I'm more of a dog person than I am a cat person.

(Okay, that was completely unrelated, but it sounds better than "BUMP" )

---

### Post by ubunterooster on 2010-06-24
Bump. (No witty comment this time, sorry)

---

### Post by Fiontie on 2011-01-26
Not sure if it's worth creating another thread because I'm encountering the exact same issue. Everything worked fine before I had to hard reboot the system (with the "Reset" button). Now as I try to run Exaile, the logo appears and then disappears and that's it; the output is exactly aforementioned.


 
 If anyone has solved this problem since the last post, I'd really appreciate any advice.

---

### Post by $teve on 2011-02-28
Have you tried deleting the setting file in ~/.config/exaile? Failing that try deleting the ~/.local/share/exaile folder but BACK IT UP FIRST! I recall having this problem a few years back & im fairly sure one of these solved it. Let us know if it works ;)

---

### Post by Chriske on 2011-03-20
> **$teve said:**
> Have you tried deleting the setting file in ~/.config/exaile? Failing that try deleting the ~/.local/share/exaile folder but BACK IT UP FIRST! I recall having this problem a few years back & im fairly sure one of these solved it. Let us know if it works ;)

Thank you so much $teve!

I had the same problem.

I first deleted  the setting file in ~/.config/exaile. Exaile still would not start.

Then I deleted the ~/.local/share/exaile folder.

I then removed exaile, shut down and started Ubuntu again. I reinstalled exaile and now it works.

So, it's either your second option, or both together that did it.

Thanks again!  ):P

---

