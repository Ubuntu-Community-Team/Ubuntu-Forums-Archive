---
title: "cron to run recollindex at night with output to file"
date: 2010-10-02
forum: General Help
---

### Post by 55tptag on 2010-10-02
Hi,

Below is my cron entry.  I would like it to run at 1:30AM every day.  And then append the success or failure of the cron job in the file named "recollindexUpdate.log".  

I can get recollindex to run via the cron job.  But nothing appears in the file it creates.

How can I modify the cron job to show what it did?  To show that the index was updated?

```
# m h  dom mon dow   command
30 1 * * * /usr/bin/recollindex  2>&1 >> /home/brian/Documents/cronlogs/recollindexUpdate.log
```

---

### Post by gmargo on 2010-10-02
**recollindex** doesn't print anything, so there's nothing to see.  Instead of running it directly from cron, run a shell script instead so the exit code can be checked and then something useful printed, like this:

```

#!/bin/sh

start=$(date)
recollindex
rc=$?
end=$(date)

if [ $rc -eq 0 ] ; then
        echo "Command OK, start=$start, end=$end"
else
        echo "Command FAIL, start=$start, end=$end, rc=$rc"
fi

```

---

### Post by 55tptag on 2010-10-02
Thank you!

---

### Post by 55tptag on 2010-10-05
Hi,

I just created and ran the shell script you wrote for me:
```

#!/bin/sh

start=$(date)
recollindex
rc=$?
end=$(date)

if [ $rc -eq 0 ] ; then
        echo "Command OK, start=$start, end=$end"
else
        echo "Command FAIL, start=$start, end=$end, rc=$rc"
fi
```

After I ran it I got the following error:

```
$ ./recollForCron.sh 
bash: ./recollForCron.sh: /bin/sh^M: bad interpreter: No such file or directory
```

I don't know anything about shell scripts.  Maybe I did something wrong?

---

### Post by gmargo on 2010-10-06
This is a dos-format (CR/LF line endings) vs. unix-format (LF line endings) issue.  The copy/paste from the web site to your editor left the file in a dos-format state.  Which bash will choke on.

To convert dos format to unix format, use the **dos2unix** program from the **dos2unix** package.  Or use **vim** and it's "fileformat" option to convert.  There's probably other ways. Which editor did you use?

---

### Post by 55tptag on 2010-10-06
Thanks for the information.  To answer your question I had cut and pasted your shell script using the editor named gedit.

Instead of installing dos2unix I just typed it up in vi.

Unfortunately, when I ran the script recollindex crapped out with an error.  See a portion below:
```

yt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/norden.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/sdf.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/gophermap.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/maps.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/phlogs.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/users.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/computers.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/caps.txt.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/incoming.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/NetBSD.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.sbd/hacking.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/pub.msf] mime []
:3:../internfile/internfile.cpp:260:FileInterner:: ignored: [/home/brian/BUPS/bups.09.29.2010_Ubuntu10.04/.thunderbird/bqnncvyt.default/ImapMail/mail.freeshell.org/e7791f1e.sbd/etc.msf] mime []
terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
Aborted
RCLMFILT: rclchm : : EOF on input
Command FAIL, start=Wed Oct  6 15:17:14 EDT 2010, end=Wed Oct  6 15:24:39 EDT 2010, rc=134

```

The index updates fine when I manually use the programs GUI.

Thanks for your help.

---

