---
title: "scripting unzip"
date: 2012-01-18
forum: General Help
---

### Post by douellette on 2012-01-18
I've got a script along the lines of:

#!/bin/bash
cd /tmp
unzip ./testfile.zip
cd

Yet when I run the script I get the error:

Archive:  /usr/bin/unzip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /usr/bin/unzip may be a plain executable, not an archive
unzip:  cannot find zipfile directory in one of /usr/bin/unzip or
        /usr/bin/unzip.zip, and cannot find /usr/bin/unzip.ZIP, period.

Which makes no sense. I can manually cd into /tmp and run:

$ unzip ./testfile.zip

and it works fine. Any thoughts? I know its something stupid. I know the file isn't corrupt as I've successfully unziped it from the command line.  Thanks.

---

### Post by mikaelcrocker on 2012-01-18
instead of chanding director to tmp, just give the full path name, I have found there are some issues.

unzip /tmp/zipfile.zip

Also be sure to check if there are any parameters you need.  I typically use gzip so off the top of my head I'm not sure.  Also in your script of you're trying to 'unzip ./file.zip' that just looks like you're tying to zip and run a script file at the same time.

---

### Post by douellette on 2012-01-20
Thanks for the tips. However it turns out it was something really dumb.
Earlier in the script I had defined a variable
export UNZIP=/usr/bin/unzip
that was not used ANYWHERE in the script. Apparently the unzip command took the variable as the name of the file to unzip (i.e. unzip $UNZIP)
Thus the error message since the file /usr/bin/unzip was a non-compressed binary file. Removing the earlier line resolved the problem and the script ran fine. This makes absolutely no since the man page for zip/unzip don't even mention an environment variable of $UNZIP being used.... go figure.

---

