---
title: "Difficulty restoring home folder from backup"
date: 2010-10-10
forum: General Help
---

### Post by Quadunit404 on 2010-10-10
Before I reinstalled Ubuntu (this time allocating the entire disk to it as I never really used Windows any more) I backed up the entire contents of my /home folder using Deja Dup. Now that I am done reinstalling Ubuntu I am trying to restore the backup. However, when it actually begins restoring the backup, it says "Restore failed: failed with an unknown error" and gives this as the output:

```
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1257, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1250, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1142, in main
    globals.gpg_profile.passphrase = get_passphrase(1, action)
  File "/usr/bin/duplicity", line 129, in get_passphrase
    pass1 = getpass.getpass("GnuPG passphrase: ")
  File "/usr/lib/python2.6/getpass.py", line 83, in unix_getpass
    passwd = fallback_getpass(prompt, stream)
  File "/usr/lib/python2.6/getpass.py", line 118, in fallback_getpass
    return _raw_input(prompt, stream)
  File "/usr/lib/python2.6/getpass.py", line 135, in _raw_input
    raise EOFError
EOFError
```

And if I do get the encryption key right, nothing happens.

Help please? I'd like my stuff back.

---

### Post by Quadunit404 on 2010-10-11
Anybody there?

---

### Post by mikodo on 2010-10-11
Hi,

I have no solution for you. If you do not get a response here, that corrects your problem, you could pose the question to the maintainers of Deja-dup on Launchpad at   [https://answers.launchpad.net/deja-dup](https://answers.launchpad.net/deja-dup) . You can also get to there when using Deja-dup.. click -> Help -> Get Help Online -> Questions for Deja-Dup. If you haven't already, you will have to register there for a Launchpad account, and then log in with it, before you can ask a question.

I, as a test last week, downloaded Ubuntu 10.10 RC, installed it; installed Deja-Dup and was able to bring forward the contents of /home on Ubuntu 10.04 from my external HDD, that I use for backup, into 10.10. So, I know it works. You may have to approach it, some other way to access your data.

Hope this helps.

---

### Post by Quadunit404 on 2010-10-11
I upgraded my Deja Dup installation to 17.0 as apparently my problem was a bug and was fixed in that version, but now it crashes if I try to select the location of my backup. This is the terminal output:

```
GLib-GIO-ERROR **: schema does not contain a key named 'path'
aborting...

```

Help please?

UPDATE: Trying to restore my backup with duplicity. I definitely could use some help because it tells me this when it begins processing the backup volumes:

```
No orphaned or incomplete backup sets found.
Registering (mktemp) temporary file /tmp/duplicity-rQXLKF-tempdir/mktemp-oYDXIF-2
Deleting /tmp/duplicity-rQXLKF-tempdir/mktemp-oYDXIF-2
Forgetting temporary file /tmp/duplicity-rQXLKF-tempdir/mktemp-oYDXIF-2
Processed volume 1 of 617
/home/tom not found in archive, no files restored.
Removing still remembered temporary file /tmp/duplicity-rQXLKF-tempdir/mkstemp-CjD7ll-1

```
I looked in the archives and /home/tom is in both /snapshot and /multivol_snapshot. Somebody mind telling me what I'm doing wrong? My command for duplicity is this:

```

duplicity restore --restore-time=2010-10-10T21:17:59Z --file-to-restore=/home/tom --force file:///media/xplane/Other\ stuff /media/xplane/ --verbosity=9 --gpg-options= --archive-dir=/home/tom/.cache/deja-dup --log-file=/tmp/deja-dup-G1UGDV

``` (Couldn't find any other drive for the job so I put the backup on the drive that has X-Plane on it)

---

### Post by Quadunit404 on 2010-10-11
Bump because I REALLY need help on this.

---

### Post by mikodo on 2010-10-13
I am still using Deja-Dup 14.2 that worked for me last week in my trial re-install. Strange that the update to 17.0 that was to fix the bug you mentioned, didn't seem to affect me with 14.2 and did affect you with version 17.0.  Strange... Did you contact the good folks that are maintaining the app for assistance? They seem quite willing to help others, with their difficulties, and as you say this is a known bug that supposedly they know about and offered a fix for, they might have quick answers for you.... I hope,  Good luck!

---

### Post by Quadunit404 on 2010-10-13
Well, I got the data restored - to the wrong drive. I managed to copy nearly everything back to my laptop yesterday and I still have about 2000-something files left to go.

I figured out what I was doing wrong with Duplicity and got the files restored (to the drive the backup was contained on ](*,) ) now I just need to finish copying back all my old settings. Good GOD my old profile was HUGE (needed to copy back over **60GB** of data)

---

### Post by mikodo on 2010-10-13
Glad to hear you are sorting it out! I had a look at the Deja-dup version you are running and it is an insecure developmental one. I feel more secure with my data using stable releases. I use the PPA and receive the newest fixes on the fly, when they are uploaded to Launchpad.  Anyways, good new to hear your data is safe.   Mike

---

### Post by Ciginator on 2010-12-04
So what did you do in the end? I'm having exactly the same issue ...

---

### Post by Quadunit404 on 2010-12-04
I used Duplicity in a Terminal. I forgot what command I used, though :|

---

