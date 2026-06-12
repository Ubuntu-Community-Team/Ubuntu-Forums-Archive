---
title: "Duplicity won't use PASSPHRASE env variable"
date: 2012-01-08
forum: General Help
---

### Post by csete on 2012-01-08
Hello,

I'm struggling with a set of scripts that I've long used for remote SSH-based backups using duplicity on 11.10.  This was a fresh machine installation, so it may not be directly related to 11.10, but I can't figure it out.  I'm seeing the following error when I try to run a backup via /etc/crontab:

```

/usr/lib/python2.7/getpass.py:83: GetPassWarning: Can not control echo on the terminal.
  passwd = fallback_getpass(prompt, stream)
Warning: Password input may be echoed.
GnuPG passphrase for signing key: Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1359, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1342, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1297, in main
    globals.gpg_profile.signing_passphrase = get_passphrase(1, action, True)
  File "/usr/bin/duplicity", line 154, in get_passphrase
    pass1 = getpass.getpass(_("GnuPG passphrase for signing key:")+" ")
  File "/usr/lib/python2.7/getpass.py", line 83, in unix_getpass
    passwd = fallback_getpass(prompt, stream)
  File "/usr/lib/python2.7/getpass.py", line 118, in fallback_getpass
    return _raw_input(prompt, stream)
  File "/usr/lib/python2.7/getpass.py", line 135, in _raw_input
    raise EOFError
EOFError

```

This is clearly trying to do an interactive password retrieve, which definitely won't work from within crontab.  However, my script should be passing in the PASSPHRASE via the environment:

```

#!/bin/bash
export PASSPHRASE=xxxxxxxxxxxxxxxxxxxxxxxxxx
export HOME=/root

duplicity --log-file /var/log/duplicity.log --full-if-older-than 1M --include-globbing-filelist /root/bin/filelist.bkp --sign-key XXXXXXXX --ssh-options "-oProtocol=2 -oIdentityFile=/root/bin/duplicity.key" / scp://XXXXX@XXXXX.org/backups/primary >> /var/log/duplicitybackup.log 2>&1

unset PASSPHRASE

echo "Nightly Backup Successful: $(date)" >> /var/log/duplicitybackup.log
echo "Nightly Backup Successful: $(date)" | mail -s "Nightly Backup Successful: $(date)" XXXXX

```

I can't seem to figure out why this is no longer working and why duplicity won't recognize the PASSPHRASE environment variable.  Can anyone offer any help?

Thanks,
Craig

---

### Post by csete on 2012-01-09
Does anyone have any ideas for me to try or places I can look?

Thanks again,
Craig

---

