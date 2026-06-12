---
title: "Running a perl script"
date: 2011-09-01
forum: General Help
---

### Post by Pingouin7 on 2011-09-01
I installed perl with sudo apt-get install perl, but when I try to run a perl script, it just opens it as a text file.
What do I have to do to run perl scripts once perl is installed?

---

### Post by steviefordi on 2011-09-01
Make sure the file is executable with:
```
chmod 755 perlscript.pl
```

The very top line of the script should have a shebang, something like:
```
#!/bin/perl
```

which points to the perl executable.

---

### Post by Pingouin7 on 2011-09-01
> **steviefordi said:**
> The very top line of the script should have a shebang, something like:
```
#!/bin/perl
```which points to the perl executable.
It did start with #!/bin/perl, which is why I was wondering why it didn't work.

---

### Post by jim_deadlock on 2011-09-01
Should be

```
#!/usr/bin/perl
```

---

