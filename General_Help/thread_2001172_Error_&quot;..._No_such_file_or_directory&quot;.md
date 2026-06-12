---
title: "Error: &quot;... No such file or directory&quot;"
date: 2012-06-10
forum: General Help
---

### Post by koenigcochran on 2012-06-10
Hi,

I'm new to Linux systems and shells generally. I'm checking my installation of a piece of software called "Dakota". The instructions from their site told me I could check this by entering "dakota -version". 

I encountered this error: 

"dakota: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory"

There is a file:         "**/home/jeff/Dakota/bin**/libXm.so.2"

and my $PATH is:                                          

"**/home/jeff/Dakota/bin**:/home/jeff/Dakota/test:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
  
I've read about a dozen or more threads that have not been helpful. Any thoughts? Please keep in mind that I'm as inexperienced as they come. Thank you!

---

### Post by matt_symes on 2012-06-10
Hi

Welcome to the forums koenigcochran :)

Do you have a link to the software you installed and the instructions ?

How did you try to install it ?

That way i can try to install it. I'll see how i get on and i can then tell you what i did.

Kind regards

---

### Post by steeldriver on 2012-06-10
Like matt_symes says, it would help to know what you are trying to install - and how

Maybe you missed a step that would have installed the additional libraries (either from the usual repository or from the package you downloaded) into the standard locations? (e.g. 'make install' rather than just 'make')

If you *are* intended to use libraries from a local directory, then generally the loading of shared libraries from non-standard locations is determined by the LD_LIBRARY_PATH environment variable, not the PATH environment variable - usually you wouldn't need to define LD_LIBRARY_PATH at all (ld knows about the 'standard' library paths) but depending if yours is defined and/or what's already in it you could try either

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/jeff/Dakota/bin
```or

```
export LD_LIBRARY_PATH=/home/jeff/Dakota/bin:$LD_LIBRARY_PATH
```

or (if there's no existing LD_LIBRARY_PATH) just

```
export LD_LIBRARY_PATH=/home/jeff/Dakota/bin
```

as appropriate in your terminal before running the executable

---

### Post by koenigcochran on 2012-06-10
> **steeldriver said:**
> If you *are* intended to use libraries from a local directory, then generally the loading of shared libraries from non-standard locations is determined by the LD_LIBRARY_PATH environment variable, not the PATH environment variable 

This turned out to be the issue. Thank you so much! I'm going to check out the absolute beginners forum soon to see if I can avoid issues like this in the future. 

In the meanwhile, (1) is there a file I can edit containing LD_LIBRARY_PATH, so that I can make sure this directory gets included every time I open bash? Or (2) is it likely I've made some other mistake, and setting LD_LIBRARY_PATH shouldn't be necessary? 

The software is called the "Dakota Project" and can be found at [this government website]("http://dakota.sandia.gov/distributions/download.html#release").

I downloaded the binary and tried to follow the instructions [here]("http://dakota.sandia.gov/distributions/dakota/5.2/install.html#instwinbin") for Unix systems. I extracted the file in /home/jeff. 

Thanks again. I'm happy to see how helpful forum members are--even when I'm sure my questions seem trivial.

---

### Post by steeldriver on 2012-06-10
Well there are a few ways of doing that - probably the neatest (in the sense that it *only* affects the particular executable it's needed for) is to wrap the dakota executable in a little shell script that sets the LD_LIBRARY_PATH (and any other environment variables you need to modify) and then invokes the executable directly. In fact, to keep everything tidy, I would probably:

1. create a local bin dir /home/jeff/bin if you don't already have one

2. the default ~/.profile should detect your /home/jeff/bin directory on next login and automatically add THIS to your $PATH

3. write a little shell script in /usr/jeff/bin called 'run_dakota' or 'dakota.sh' or just plain 'dakota' if you don't like being reminded it's  a shell script (or more importantly if other tools rely on it being invoked as plain 'dakota') and have *it* set both the $PATH and $LD_LIBRARY_PATH before executing /usr/jeff/Dakota/bin/dakota directly

[In fact, you will likely not even need to set $PATH in your shell script since you will be invoking the executable explicitly with its full path - unless there are other sub-programs in the Dakota/bin that the main program relies on and needs to be able to find]

Something like: 

/home/jeff/bin/dakota.sh:
```

#!/bin/bash

# to find local executables (probably don't need /home/jeff/Dakota/bin here)
export PATH=/home/jeff/Dakota/bin:/home/jeff/Dakota/test:$PATH

# to find local Motif libs etc.
export LD_LIBRARY_PATH=/home/jeff/Dakota/bin

/home/jeff/Dakota/bin/dakota

```This way, you can run it anywhere just by typing

```
dakota.sh
```but neither your PATH nor LD_LIBRARY_PATH contain any surprises for other processes. I *think* this is right but there are some much more knowledgeable shell script gurus on here who can step in and correct.

---

### Post by matt_symes on 2012-06-10
Hi

Nice work steeldriver. Not much for me to do here.

I would suggest making the shell script executable

```
chmod 755 dakota.sh
```

> in the sense that it *only* affects the particular executable it's needed for

Sounds like you know the global method of adding a file into 

```
/etc/ld.so.conf.d/
```

Once again. Nice work.

/me strolls off :)

Kind regards

---

### Post by steeldriver on 2012-06-10
Doh! thanks - yes I forgot about making the script executable

NOTE: I edited my response after noticing that the default ~/.profile tests for $HOME/bin and adds that to the $PATH if it exists - no need to manually add it anywhere 

TBH I hadn't thought about using ld.so.conf, I was thinking more along the lines of simply placing the lib(s) in /usr/local/lib which iirc is already on the default ld search path. But LD_LIBRARY_PATH (even though it's officially discouraged I think) seems like a reasonable solution for cases where you want to sandbox a one-off application like this (so long as it is inside a launch script) - I hope that doesn't ruffle any feathers 

Regards

---

