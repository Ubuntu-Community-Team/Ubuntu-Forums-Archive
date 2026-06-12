---
title: "Question on building Python 2.6.7 on Hardy"
date: 2012-02-12
forum: General Help
---

### Post by krosswindz on 2012-02-12
I am trying to install python 2.6.7 for Hardy. I have installed the build-dep for python 2.5. I wondering what I need to do install linuxaudiodev and ossaudiodev modules

```

Failed to find the necessary bits to build these modules:
bsddb185           linuxaudiodev      ossaudiodev
sunaudiodev
To find the necessary bits, look in setup.py in detect_modules() for the module's name.

```

I have searched but havent found a solution. Everyone suggest installing python 2.5 build deps, which I have but I am still having the same problem.

---

### Post by linoseros on 2012-02-12
have you looked at setup.py the detect_modules part for the modules' names ?

---

### Post by krosswindz on 2012-02-12
I have looked into it but I dont know what I am missing, this is the only thing I find in setup.py which mentions both linuxaudiodev and ossaudiodev.

```

        # Platform-specific libraries
        if platform == 'linux2':
            # Linux-specific modules
            exts.append( Extension('linuxaudiodev', ['linuxaudiodev.c']) )
        else:
            missing.append('linuxaudiodev')

        if platform in ('linux2', 'freebsd4', 'freebsd5', 'freebsd6',
                        'freebsd7', 'freebsd8'):
            exts.append( Extension('ossaudiodev', ['ossaudiodev.c']) )
        else:
            missing.append('ossaudiodev')

```

---

### Post by ajgreeny on 2012-02-12
Is there a good reason for using Hardy?  That lost its support a long time ago.

---

### Post by krosswindz on 2012-02-12
Yes, I am running it on my apple tv 1st gen. The nvidia driver that supports HDMI audio runs compiles on hardy. It doesnt compile with newer kernels.

---

### Post by krosswindz on 2012-02-12
I worked fixed this because I was building running in a box using linux-3.0. I edited the makefile to set MACHDEPS to linux2

---

