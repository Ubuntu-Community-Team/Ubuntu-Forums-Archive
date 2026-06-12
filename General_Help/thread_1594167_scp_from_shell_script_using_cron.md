---
title: "scp from shell script using cron"
date: 2010-10-12
forum: General Help
---

### Post by shreyas.atre on 2010-10-12
Hi,

I have a script that I would like to run using 'cron'. I want to use 'scp' to transfer files from one machine to another. I have set up the SSH keys on both machines. When I run the script from bash terminal, it works flawlessly. But when I schedule a 'cron' job to run the same script, 'scp' does not transfer the files.

```

#!/bin/bash

host='shreyas@192.168.1.31'
directory='/home/shreyas/shared'

echo ""
echo "Inside $0"
echo "Time: `date` "
echo "Changing to $HOME/test"
cd ~/test

ls -l

echo "Remotely copying"

scp -v * $host:$directory
retvalue=$?

echo "Return value: $retvalue"
echo "Done"

```

'Return value' is 0 when the script is run from bash directly. But when it runs from 'cron', the 'Return value' is 1. That means, surely, that 'scp' is throwing an error. I don't know which error is being encountered. Could anybody let me know how to make it work?

Thanks and Regards.

---

### Post by P4man on 2010-10-12
No expert but I think you better use absolute paths. The  $HOME folder would not be defined in cron environment, unless you specified it.

---

### Post by shreyas.atre on 2010-10-12
> **P4man said:**
> No expert but I think you better use absolute paths. The  $HOME folder would not be defined in cron environment, unless you specified it.

That does not seem to be the problem, as from the terminal I can successfully execute the script and the files get copied. Only when I try to execute the script through 'cron', it does not work.

Here is how my 'crontab' looks:

```

PATH=/usr/sbin:/usr/bin:/sbin:/bin:/bin/bash:/usr/bin/ssh
* * * * * bash /home/shreyas/remotecopy.sh >> /home/shreyas/mylog.log

```

---

### Post by P4man on 2010-10-12
so what makes you think [COLOR="Red"]~[/COLOR]/test is defined in that environment? Cron environment is (edit) *not* the same as your user's bash.

btw, im not sure that schedule is valid;

---

### Post by shreyas.atre on 2010-10-12
I have updated the script to deal with absolute paths.

```

#!/bin/bash

echo ""
host='shreyas@192.168.1.31'
directory='/home/shreyas/shared'
scp /home/shreyas/test/jvm.txt $host:$directory
retvalue=$?

if [ $retvalue = 0 ]; then
	echo "Done"
else
	echo "Could not copy"
	echo "Return value: $retvalue"
fi
echo ""

```

It still would ***not*** work from 'cron'. I could not find any solution anywhere.

Thanks and Regards.

---

### Post by CharlesA on 2010-10-12
Pipe the (error) output to a file and see what happens.

```
* * * * * bash /home/shreyas/remotecopy.sh >> /home/shreyas/mylog.log 2>> /home/shreyas/err.log
```

Also: I don't think * * * * * is a valid schedule.

EDIT: You also don't need to proceed the command with "bash" since the shebang already has the path to bash. As long as the script has execute properties, you can run it just fine by just using the path.

---

### Post by shreyas.atre on 2010-10-12
Thanks! After piping the error output, I get the following error:
```

Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
lost connection

```

Why does that happen only when executing the script through 'cron'? When I execute the script as ***bash remotecopy.sh***, it works fine; no error output.

Thanks and Regards.

---

### Post by CharlesA on 2010-10-12
Probably because it's asking for a password and cron can't provide it.

As far as I know, you would need to set up a passphrase-less key in order to do what you ask.

Use this to create the key:

```
ssh-keygen
```

And This to copy it to the remote machine:

```
ssh-copy-id
```

---

### Post by shreyas.atre on 2010-10-13
Thanks! I got to know the problem. While creating the key-pair, I had given some passphrase. I created the key-pair again without any passphrase; now it works absolutely fine. Thanks for all the help.

Regards.

---

