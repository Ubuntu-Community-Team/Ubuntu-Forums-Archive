---
title: "2 conky problems - need suggestions"
date: 2009-07-24
forum: General Help
---

### Post by falen_pl on 2009-07-24
Hi,

I've been struggling with those two minor annoyances. I'd appreciate suggestions and solutions.

PROBLEM #1

gmail.parser.py

I have it configured to display new emails' subjects. It works OK but there's one issue. Whenever there's a non-standard character used in the subject (such as a symbol for a GBP), conky won't display it and gives me this output in the terminal:

UnicodeEncodeError: 'ascii' codec can't encode characters in position 17-19: ordinal not in range(128)

Obivously, it's an ecoding problem but I've no idea to make it display right.

My idea would be to make conky write the output to a file, and then just display it. That should by pass the encoding thing. Is that possible and if so how do I implement it?

PROBLEM #2

Display mounted USBs.

I made Conky display how much space left there is on my pendrive. If it's mounted, it looks like this: KINGSTON 2.5GiB / 3.90GiB. However, since I manually edited conkyrc, the KINGSTON part will still be displayed when I plug the device out. I'd rather have Conky automatically detect what devices are mounted and then display their names and space information. Should I use a script?

---

### Post by m_duck on 2009-07-24
The first problem may be able to be solved by using the following option above TEXT in your config:```
override_utf8_locale yes
```This also means you will need to use an xft font so the following will also be needed (but you can change the font to your liking):```
use_xft yes
xftfont Bitstream Vera Sans Mono:size=8
xftalpha 0.8
```For the second I should imagine you could use a script if you want anything that gets mounted to be displayed. However if it is always the same few drives that get mounted, ie /media/KINGSTON or whatever, you could use the ${if_mounted} variable. This could display space info if the drive is mounted and either nothing or a notice saying the drive is not mounted if it is not mounted. Having never used this variable before I can't give specifics but will have a play around later if I have time.

For info: [a list of all the conky variables]("http://conky.sourceforge.net/variables.html") (note not all of these will work, it depends on which options the repo version of conky was compiled with, though the majority of the vars do work).

---

### Post by falen_pl on 2009-07-24
Hey, 

Thanks for the prompt reply.

1) As it turned out, I already had these:

override_utf8_locale yes
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8

in my conkyrc, so these settings don't help with the problem. Using different font doesn't change anything and the terminal still gives mi this output. 

Traceback (most recent call last):
  File "/home/smoothie/Conky/scripts/gmail_parser.py", line 47, in <module>
    readmail(f, int(maxlen)) # Let the feed be chewed by feedparser
  File "/home/smoothie/Conky/scripts/gmail_parser.py", line 39, in readmail
    print '${color white}@: %s' % atom.entries[i].title
UnicodeEncodeError: 'ascii' codec can't encode characters in position 17-20: ordinal not in range(128)

2) I'm familiar with the {if_mounted} variable and indeed, it works for me, but in addition to that, I'd also like to have conky display the same information for any drives I don't own and happen to stick in the usb drive.

Thanks!

---

### Post by UbeBuntu on 2009-09-09
Here is a solution for you gmail_parser.py script:

```

## check-gmail.py -- A command line util to check GMail -*- Python -*-
## modified to display mailbox summary for conky

# ======================================================================
# Copyright (C) 2006 Baishampayan Ghose <b.ghose@ubuntu.com>
# Modified 2008 Hunter Loftis <hbloftis@uncc.edu>
# Time-stamp: Mon Jul 31, 2006 20:45+0530
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
# ======================================================================

import sys
import urllib             # For BasicHTTPAuthentication
import feedparser         # For parsing the feed
from textwrap import wrap

_URL = "https://mail.google.com/gmail/feed/atom"

uname = sys.argv[1]
password = sys.argv[2]
maxlen = sys.argv[3]

urllib.FancyURLopener.prompt_user_passwd = lambda self, host, realm: (uname, password)
	
def auth():
    '''The method to do HTTPBasicAuthentication'''
    opener = urllib.FancyURLopener()
    f = opener.open(_URL)
    feed = f.read()
    return feed

def readmail(feed, maxlen):
	'''Parse the Atom feed and print a summary'''
	atom = feedparser.parse(feed)
	print '${color}Mail: %s@gmail.com (%s new)\n' % (uname, len(atom.entries))
	for i in range(min(len(atom.entries), maxlen)):
		print ' ${color}"%s"' % atom.entries[i].title.encode("utf-8")
		print '    ${color lightgrey}%s' % atom.entries[i].author.encode("utf-8")
	if len(atom.entries) > maxlen:
		print ' ${color}more...'

if __name__ == "__main__":
    f = auth()  # Do auth and then get the feed
    readmail(f, int(maxlen)) # Let the feed be chewed by feedparser

```

Cheers ;)

---

