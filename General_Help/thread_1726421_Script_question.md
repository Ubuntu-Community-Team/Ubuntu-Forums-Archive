---
title: "Script question"
date: 2011-04-11
forum: General Help
---

### Post by Elvish Legion on 2011-04-11
I have a script I use to launch two programs at once.  However I have a question about it, is there anyway to have it check and see if one of them is already open and not open if it finds it?

Right now its really basic

cd /path/to/file/
wine program.exe

cd /path/to/file2
wine program2.exe

I want to have it check and see if file 2 is already running and if so not launch a second copy of it

Is this possible?

---

### Post by mendhak on 2011-04-11
Hi, this should be possible ([_see this example_]("http://www.anyexample.com/linux_bsd/bash/check_if_program_is_running_with_bash_shell_script.xml"))

```

if ps ax | grep -v grep | grep program.exe > /dev/null
then
    wine program2.exe
fi

```

---

### Post by seawolf167 on 2011-04-11
> **mendhak said:**
> Hi, this should be possible ([_see this example_]("http://www.anyexample.com/linux_bsd/bash/check_if_program_is_running_with_bash_shell_script.xml"))

```

if ps ax | grep -v grep | grep program.exe > /dev/null
then
    wine program2.exe
fi

```

This should be

```

if ps ax | grep -v grep | grep program.exe > /dev/null
then echo "program.exe is running"
else
    wine program2.exe
fi

```

---

