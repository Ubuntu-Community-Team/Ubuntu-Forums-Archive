---
title: "Exaile stopped opening"
date: 2010-11-06
forum: General Help
---

### Post by Blue_Mercury on 2010-11-06
Today I turned on my computer and opened Exaile, the music player I use on Ubuntu 10.04.  
The splash shows, goes away, then nothing happens.  Trying to run the program again yields the same result as does opening a file with that program.

I tried totally removing Exaile using the synaptic package manager, and reinstalled it, but that did not work.

I have been using this program for a year now and have never had any problems with it, it is definitely one of the best Gnome muisc players.


Running this program from the terminal yields:

~$ exaile
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
INFO    : HAL Providers: [<cd.CDHandler object at 0xab0746c>]

---

### Post by Blue_Mercury on 2010-11-07
bump

---

### Post by Blue_Mercury on 2010-11-07
I solved this problem by adding the Exaile repository to the software sources and upgrading to the newest version (not listed in the default software sources)

---

