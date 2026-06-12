---
title: "Script Help....UTF-8 Character converter"
date: 2012-02-06
forum: General Help
---

### Post by nikkpap on 2012-02-06
Hi to all...
I have a nautilus script which converts characters from a ISO-xxx
to Utf8 and it working good in single file... (right click on a file and convert) my "Q" is can anyone help me to make work with batch mode (lots file lets say control and select 5-6-9-12 files and convert...) the script is below...

#!/bin/bash
#
# Character Encoding Conversion Script for Nautilus
#
# A simple nautilus script to convert from iso-8859-7
# character encoding to utf-8.

from="iso-8859-7"	# Replace $1 with the input  encoding ex. "iso-8859-7"
to="utf-8"		# Replace $2 with the output encoding ex. "utf-8"

thefile="$*"
if [ $# -gt 0 ];then
iconv -f $from -t $to "${thefile}" > "${thefile}.utf8"
mv "${thefile}.utf8" "${thefile}"
fi
exit 0

thanks in advance bros...
my email is [email]nikkpap@gmail.com[/email]

---

### Post by Khayyam on 2012-02-06
nikkpap ..

I'm not familiar with Nautilis but I assume its will treat multiple files as "$@" (as per regular bash/shell parameter expansion). Untested .. but it should work

```
#!/bin/bash

FROM_ENC="iso-8859-7"
TO_ENC="utf-8"

for i in "$@" ; do
       iconv -f ${FROM_ENC} -t ${TO_ENC} "${i}" > "${i}.utf8"
       mv "${i}.utf8" "${i}"
done
```

---

### Post by Vaphell on 2012-02-06
i think the test is not necessary, for loop won't do anything with the empty set either way.
Also double-quotes are a must ( "$@" ) - otherwise parameters/names will break on spaces.

---

### Post by Khayyam on 2012-02-06
Vaphell ...

I'd edited and added the test condition thinking that I'd oops'd and missed copying it from the OP, damn subconcious, always has to be right, heh.

As for the "$@", best be safe, but I'd assumed the files wouldn't have spaces, I guess perhaps fontfiles copied from Windows/OSX may. Won't hurt and so I've edited it in (and removed the test).

Thanks for the heads-up ..

---

### Post by Khayyam on 2012-02-07
[QUOTE=nikkpap]Thank you [...] it worked.[/QUOTE]

Good .. but you should state that in the thread rather than private messaging me, that way the question can be seen as answered. So, please now [mark the thread as [SOLVED]]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6").

BTW, this script can replace yours, as it does the same thing whether one or many files are passed to it.

Also, this isn't strickly a "Nautilus script", Nautilus just runs the script with the selected files as it input. The script will work just as well from the command line.

Anyhow .. your welcome

---

