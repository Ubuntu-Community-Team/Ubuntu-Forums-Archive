---
title: "[at] command"
date: 2010-11-26
forum: General Help
---

### Post by Drenriza on 2010-11-26
Anyone who can explain this for me.
> finally I solved the issue. I stop using "at" for quite some time, but  the need come again so I have to take a look again. It seems the problem  lies in /etc/at.deny file. As the command is executed using /bin/sh,  there is a "bin" line in at.deny file. Removing "bin" from the file,  finally allow my program to be executed .. wow ..wat a relieve ..

what is it that the /etc/at.allow and /etc/at.deny needs to contain?

also when using the at command do u then need to do
> at [date] /path/to/file
As a cron job to make it run?

Thanks on advance.

---

### Post by WorMzy on 2010-11-26
Check the at man page:

```
man at
```

>        If the file /etc/at.allow exists, only usernames mentioned  in  it  are
       allowed to use at.

       If  /etc/at.allow  does  not  exist,  /etc/at.deny  is  checked,  every
       username not mentioned in it is then allowed to use at.

       If neither exists, only the superuser is allowed use of at.

       An empty /etc/at.deny means  that  every  user  is  allowed  use  these
       commands, this is the default configuration.


---

