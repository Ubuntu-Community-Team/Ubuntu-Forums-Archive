---
title: "Festival under Apache"
date: 2009-12-27
forum: General Help
---

### Post by nibl on 2009-12-27
I am trying to run Festival 1.9.6 under Apache on an Ubuntu setup. I can run the php script from the command line, but it fails under Apache...without any error messages. All exit codes are zero.

The program is called via PHP. I can call "text2wave --help" and capture the output. Here with
backticks:

$result = `/path/to/festival/bin/text2wave --help`;
echo $result;

It shows the help message as expected.

Here is a test to prove that permissions are okay. I echo a text file to the same directory the audio file is output to, before calling festival:

--- edited text2wave -----

#!/bin/sh

# test script can write the audio file to the correct destination

echo "hello festival" > /path/to/audiofile

"true" ; exec /path/to/bin/festival --script $0 $*

------------------------------

This proves the web server can run text2wave and write to the
directory.

Maybe it's a path issue with libs or something. Any ideas?

Many Thanks.

---

