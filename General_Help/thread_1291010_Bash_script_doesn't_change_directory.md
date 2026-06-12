---
title: "Bash script doesn't change directory"
date: 2009-10-14
forum: General Help
---

### Post by Pi72 on 2009-10-14
I'm doing a script with a double purpose, to be used in other scripts. If it's called with one parameter, it creates a directory with the same name as the first parameter (which is an ARJ file) with ".unc" added. Changes to it, and uncompresses the file in it.

If a second parameter is given, then the script changes to the folder provided in that second parameter first. In the end, it goes back to the directory where you invoked the script (which is important for the calling scripts).

However, after making the directory, it doesn't change into it. That **cd "${dir}"** does nothing. Do you see any obvious error? I've been one hour with this and still can't figure out what is wrong or how to fix it. It makes the folder, but doesn't go into it. Is it 

For now forget about the second parameter. Calling the script from the same directory where the file is, such as "unarj2dir test.arj" just gives me endless errors as if it enters some kind of loop forever and ever... It simply doesn't change to the newly created folder! Btw, there are several versions of this script, so it's important to change to the newly created directory before the next action is performed.

Thanks in advance for any help!

```
#!/bin/bash
pushd .>/dev/null
if [ "$2" != "" ] ; then
  cd "$2"
fi

dir="$1.unc"
mkdir "${dir}"
cd "${dir}"
unarj x -v -y  "../$1"
popd

```

---

### Post by Pi72 on 2009-10-14
Bleh, as usual you discover the error just after asking for help. The error wasn't in the cd command, but it made it look so. Thanks anyway.

---

### Post by justleen on 2009-10-14
```
#!/bin/bash
[ !  -z "$2" ] && cd $2 

dir="$1.unc"
mkdir ${dir}
cd ${dir}
```


that should work..


Edit: late again!  for debubbing bash scripts, try executing them with "sh -x ./script". that will give a step by step of what is actually being done.
Mind all the "" you are using! bash can be really picky when expanding variables.

---

