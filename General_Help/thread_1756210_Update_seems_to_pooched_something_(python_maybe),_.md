---
title: "Update seems to pooched something (python maybe), help please"
date: 2011-05-12
forum: General Help
---

### Post by bill.denbigh on 2011-05-12
I am running ubuntu 11.04 and i use the simple mind mapping tool labyrinth pretty regularly. Today i tried to start it and got this response.

labyrinth
Traceback (most recent call last):
  File "/usr/bin/labyrinth", line 46, in <module>
    from labyrinth import Browser
  File "/usr/lib/python2.7/dist-packages/labyrinth/Browser.py", line 33, in <module>
    import MainWindow
  File "/usr/lib/python2.7/dist-packages/labyrinth/MainWindow.py", line 33, in <module>
    from MapList import MapList
  File "/usr/lib/python2.7/dist-packages/labyrinth/MapList.py", line 218, in <module>
    MapList.load_all_from_dir(utils.get_save_dir ())
  File "/usr/lib/python2.7/dist-packages/labyrinth/MapList.py", line 103, in load_all_from_dir
    cls.new_from_file(dir+f)
  File "/usr/lib/python2.7/dist-packages/labyrinth/MapList.py", line 112, in new_from_file
    map._read_from_file(filename)
  File "/usr/lib/python2.7/dist-packages/labyrinth/MapList.py", line 49, in _read_from_file
    doc = dom.parse (filename)
  File "/usr/lib/python2.7/xml/dom/minidom.py", line 1914, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.7/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.7/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

Can anyone suggest where i can start looking for a solution. I have updated the system to the latest, un-installed labyrinth and re-installed and now i really have no clue what to do to get it working.

Thanks in advance... Bill

---

### Post by bill.denbigh on 2011-05-17
NVM, i give up. I'll use VYM instead...

---

