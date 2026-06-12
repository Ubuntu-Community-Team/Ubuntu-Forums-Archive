---
title: "Testing bash scripts"
date: 2010-04-16
forum: General Help
---

### Post by Mr Nemo on 2010-04-16
Is there anyway to test a bash script without actually running the commands to see if the syntax is proper? Google is of no help.

---

### Post by conradin on 2010-04-16
Im thinking you would need to convert it to a proper language to get the benifits of a compiler.  why dont you post your syntax here?

You might try 
```

man bash

```

to see other options you have, consider a restricted shell, or sending errors to a file with stderr.

---

### Post by prodigy_ on 2010-04-16
There are various debugging options. For dash: -v (verbose, copies all input to stderr), -e (errexit, exits if any untested command fails), -n (noexec, reads commands but doesn't execute them), -u (nounset, doesn't expand unset variables) and -x (xtrace, writes commands as they are actually executed to stderr).

I think that **n** option is what you want. In sh or bash use: ```
set -n
``` to turn noexec **on** and ```
set +n
``` to turn it **off** (yes, these "-" and "+" are a bit unintuitive). Other shells may have different options, so man pages are your friends here (as always).

Personally, for simulation runs I use "nonpersistent" VMWvare guests. All changes are undone at every poweroff of a virtual machine.

---

### Post by Captain Giraffe on 2010-04-16
I think this is a very good question that deserves some thought  prodigys answer, while good, is not feasible in many situations. Do I need to chroot? do I need to vbox my experiments?

---

### Post by prodigy_ on 2010-04-16
VMWare does have its limitations, true. Mainly, the lack of direct access to hardware.

Still, it's useful for testing logic and most of the syntax. Simulating client/server communication isn't a problem either, because you can use bridged networking in a VM.

---

### Post by gmargo on 2010-04-16
> **Mr Nemo said:**
> Is there anyway to test a bash script without actually running the commands to see if the syntax is proper?

While certainly not perfect for every situation, I use a simple "echo" or "printargs" command leader for syntax debugging.

Simple example:
```

#!/bin/sh

# Uncomment to perform test
#TESTMODE=1

# Choose first one for testing
if [ "$TESTMODE" = "1" ] ; then
        ECHO=/home/gmargo/bin/printargs
else
        ECHO=
fi

$ECHO ls -l foo

```You can guess what the source code for "printargs" looks like.  Or you can just use "echo" instead.  The advantage of "printargs" is that you'll see breaks due to spaces in filenames/directories.

---

