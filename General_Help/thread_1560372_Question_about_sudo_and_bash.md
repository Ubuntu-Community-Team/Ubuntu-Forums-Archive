---
title: "Question about sudo and bash"
date: 2010-08-24
forum: General Help
---

### Post by rolandpish on 2010-08-24
Hi, in my ubuntu lucid box, I have a bash script to automatize the creation of a svn repository (this is not a svn question).

In the script, I have these lines of code (among others):

```

# Create the repository
sudo -u www-data svnadmin create --fs-type fsfs $PATH$1 2>&1

# Create a pre-commit hook manually
sudo -u www-data echo '#!/bin/sh
REPOS="$1"
TXN="$2"
...some more content' > $PATH$1/hooks/pre-commit

```

Ok, the second sentence (sudo -u www-data echo ...) cannot complete because it shows a "permission denied" even though the $PATH$1/hooks is owned by www-data:www-data.

Interesting thing is that if I remove the "sudo -u www-data" from the script, and I execute it "outside" as: sudo -u www-data ./createrepo nameofrepo, no more "permission denied" errors are showed.

How can I achieve this "sudo -u www-data" inside the script?

Thanks in advance.

Cheers,
Roland

---

### Post by amauk on 2010-08-24
The redirect is done by the shell, and not by the command

Try something like this (note the escaped quotes)

```
sudo -u www-data sh -c 'echo \'#!/bin/sh
REPOS="$1"
TXN="$2"
...some more content\' > $PATH$1/hooks/pre-commit'
```

---

### Post by DaithiF on 2010-08-25
or an alternative is to use tee.

```
echo 'blah
blah
blah' | sudo -u www-data tee /path/to/file
```

as amauk indicates, you don't need to be sudo'd to echo text (first part of your command), however you do need to be sudo'd to redirect that text onto a file owned by another user.

---

### Post by amauk on 2010-08-25
yeah, use tee instead
it's cleaner

---

### Post by rolandpish on 2010-09-05
Hi there.
Sorry for the delay; was on some vacation days.

Thanks a lot for your replies. Will do that with the tee command (I didn't know about that command).

Thanks a lot for your help!

---

