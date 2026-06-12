---
title: "set current directory as environment variable"
date: 2010-07-10
forum: General Help
---

### Post by mayapower on 2010-07-10
Hi,

I have a simple shell script name "run.sh".
```

export PYTHONHOME="lib/"
python dispatch.py

```

When I execute the script using terminal/console and I am inside the directory where "run.sh" resides, everything works fine. Overall structure is like this:
```

lib/
python (executable)
dispatch.py
run.sh

```

When I execute the script form another directory by using full path, for example:
```

prashant@ubuntucomp:~$ /home/prashant/downloads/application/./run.sh

```
python executable is not able to find the "lib/" directory because present working directory is "/home/prashant/".

Another option to solve the problem is to set an environment variable that points to directory and use inside the script. In my case I am using similar scripts at many places and I don't to go with permanent environment variable option.

How do I solve this problem?

Cheers

Prashant

---

### Post by gzarkadas on 2010-07-11
Try this:
```

XDIR="`dirname $0`"
export PYTHONHOME="$XDIR/lib"
python "$XDIR/dispatch.py"

```The above executes the installed python executable (the one inside your /usr/bin). If, as you state, you have a python executable inside the directory where run.sh is, then you should change the script to:

```

XDIR="`dirname $0`"
export PYTHONHOME="$XDIR/lib"
"$XDIR/python" "$XDIR/dispatch.py"

```

or, if you don't like to see so much variables in the script and don't care to change the current working directory:

```

cd "`dirname $0`"
export PYTHONHOME=lib/
./python dispatch.py

```

If you don't have spaces in your directories paths, you can ommit the double quotes to make the code "cleaner".

---

