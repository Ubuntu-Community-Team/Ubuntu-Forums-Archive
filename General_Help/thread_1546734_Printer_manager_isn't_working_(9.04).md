---
title: "Printer manager isn't working (9.04)"
date: 2010-08-05
forum: General Help
---

### Post by gaines2166 on 2010-08-05
I can print from applications, but the printer manager (system>administration>printing) isn't working.  When I click on it a terminal window it opens but then immediately closes.

The system-config-printer file is empty (I also checked with nano), so I assume that has something to do with it.

gaines@gaines:~$ sudo system-config-printer
[sudo] password for gaines: 
/home/gaines/.printer-groups.xml:1: parser error : Document is empty

^
/home/gaines/.printer-groups.xml:1: parser error : Start tag expected, '<' not found

^
Caught non-fatal exception.  Traceback:
File "/usr/share/system-config-printer/XmlHelper.py", line 37, in __init__
    self.xml_doc = libxml2.parseFile (self.group_file_name)
File "/var/lib/python-support/python2.6/libxml2.py", line 1279, in parseFile
    if ret is None:raise parserError('xmlParseFile() failed')
parserError: xmlParseFile() failed
Continuing anyway..
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 6757, in <module>
    focus_on_map)
  File "/usr/share/system-config-printer/system-config-printer.py", line 6705, in main
    print_test_page, focus_on_map)
  File "/usr/share/system-config-printer/system-config-printer.py", line 565, in __init__
    self.groups_pane = GroupsPane ()
  File "/usr/share/system-config-printer/GroupsPane.py", line 144, in __init__
    for group_name, group_node in xml_helper.get_static_groups ():
  File "/usr/share/system-config-printer/XmlHelper.py", line 68, in get_static_groups
    return self.__parse_groups ("static-group")
  File "/usr/share/system-config-printer/XmlHelper.py", line 54, in __parse_groups
    current = self.xml_doc.getRootElement ().children
AttributeError: 'NoneType' object has no attribute 'getRootElement'

Suggestions?

---

