---
title: "I Don't Understand Environment Variables"
date: 2010-12-18
forum: General Help
---

### Post by Mark76 on 2010-12-18
I'm trying to install the firetray addon for Chatzilla, but I keep running up against a brick wall

~/firetray-0.2.8-src$ ./build.sh --dynamic-linking --output-dir=/usr/lib/firefox-addons/extensions 
rm: cannot remove `firetray.xpi': No such file or directory
scons: Reading SConscript files ...
Using GECKO_SDK=
[B]Please set environment variable GECKO_SDK first (or in alternative the variables GECKO_SDK_BIN, GECKO_SDK_INCLUDE, GECKO_SDK_IDL, GECKO_SDK_LIB).
error compiling firetray.xpi
[/B]

I have no idea how to set an environment variable :(

---

### Post by lmarmisa on 2010-12-18
This is the way to define an environment variable in BASH.

Simply type a command similar to this

```

export GECKO_SDK=value

```NOTE: value can be a string

If you want to see the value of the variable, type this command:

```

echo $GECKO_SDK

```If you want to automate the definition of a variable, include its definition in the file ~/.bashrc

---

### Post by Mark76 on 2010-12-18
Thanks. But now I need a tar or deb for corba:IDL.

And I can't find one anywhere. :(

---

