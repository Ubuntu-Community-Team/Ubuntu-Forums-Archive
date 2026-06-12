---
title: "installing older gcc/g++ version"
date: 2011-02-06
forum: General Help
---

### Post by r.stiltskin on 2011-02-06
After upgrading to 10.04 LTS I see that older versions (3.x) of gcc are no longer in the repos.  What would be the easiest way to install gcc 3.3.6 or 3.4.6 without breaking my system?

I suspect that I might also need an older version of binutils.  Any ideas about that?

---

### Post by khelben1979 on 2011-02-06
You can choose which version of GCC that you wish, just compile it from source code. [Here]("http://gcc.cybermirror.org/releases/") you got GCC 2.95.1 to 4.5.2 available for download.

> 1. ./configure
2. make
3. make install
to compile it.

---

### Post by r.stiltskin on 2011-02-06
Yes, I realize that I can do that, but I'm worried that the default configuration might mess something up.  I don't fully understand the directory structure.

For example, on my Ubuntu 8.04 system there are separate subdirectories
/usr/include/c++/3.3/
/usr/include/c++/4.1/
/usr/include/c++/4.2/
containing the c++ headers, but the c headers are right there in /usr/include/.  Does that mean that only one set of C headers is shared by all versions?

Also, there was
/usr/lib/gcc/i486-linux-gnu/4.1/
/usr/lib/gcc/i486-linux-gnu/4.2/
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/

and in /usr/bin there was an executable for each of the gcc versions and for each of the g++ versions.

Those were all installed by apt-get, so I didn't worry about any one of them messing up the other.  I used update-alternatives to set the appropriate links to select which I would use.

Now, on my 10.04 system, I suppose I can leave the gcc-4.4 that Synaptic installed in /usr/lib and /usr/include, and build 3.3.6 in a separate directory, say /usr/local/gcc-3.3.  Does that seem reasonable?  And is there any reason why I can't configure update-alternatives to work with that?

I'm wondering though, if I install in /usr/local/gcc-3.3/, is it OK to have the headers there -- e.g. in /usr/local/gcc-3.3/include?  If I invoke the compiler from the command-line (i.e. without a makefile), how does it know where to look for the headers?

---

### Post by khelben1979 on 2011-02-07
> Installation
How to install multiple versions of GCC

It may be desirable to install multiple versions of the compiler on the same system. This can be done by using different prefix paths at configure time and a few symlinks.

Basically, configure the two compilers with different --prefix options, then build and install each compiler. Assume you want "gcc" to be the latest compiler and available in /usr/local/bin; also assume that you want "gcc2" to be the older gcc2 compiler and also available in /usr/local/bin.

The easiest way to do this is to configure the new GCC with --prefix=/usr/local/gcc and the older gcc2 with --prefix=/usr/local/gcc2. Build and install both compilers. Then make a symlink from /usr/local/bin/gcc to /usr/local/gcc/bin/gcc and from /usr/local/bin/gcc2 to /usr/local/gcc2/bin/gcc. Create similar links for the "g++", "c++" and "g77" compiler drivers.

An alternative to using symlinks is to configure with a --program-transform-name option. This option specifies a sed command to process installed program names with. Using it you can, for instance, have all the new GCC programs installed as "new-gcc" and the like. You will still have to specify different --prefix options for new GCC and old GCC, because it is only the executable program names that are transformed. The difference is that you (as administrator) do not have to set up symlinks, but must specify additional directories in your (as a user) PATH. A complication with --program-transform-name is that the sed command invariably contains characters significant to the shell, and these have to be escaped correctly, also it is not possible to use "^" or "$" in the command. Here is the option to prefix "new-" to the new GCC installed programs:

    --program-transform-name='s,\\\\(.*\\\\),new-\\\\1,' 

With the above --prefix option, that will install the new GCC programs into /usr/local/gcc/bin with names prefixed by "new-". You can use --program-transform-name if you have multiple versions of GCC, and wish to be sure about which version you are invoking.

If you use --prefix, GCC may have difficulty locating a GNU assembler or linker on your system, GCC can not find GNU as/GNU ld explains how to deal with this.

Another option that may be easier is to use the --program-prefix= or --program-suffix= options to configure. So if you're installing GCC 2.95.2 and don't want to disturb the current version of GCC in /usr/local/bin/, you could do

    configure --program-suffix=-2.95.2 <other configure options> 

This should result in GCC being installed as /usr/local/bin/gcc-2.95.2 instead of /usr/local/bin/gcc.

[Source of the information]("http://gcc.gnu.org/faq.html#multiple"). Did it help?

---

### Post by r.stiltskin on 2011-02-07
Thanks, that's much clearer than the config info I found at [http://gcc.gnu.org/install/configure.html]("http://gcc.gnu.org/install/configure.html").

But here's another question: someone suggested that I install the gcc 3.3.6 package from the Hardy repository instead of building it.  Is that safe?  (I'm running Lucid.  I'm not concerned with optimizing the build for my system; the generic build is fine.)

---

### Post by khelben1979 on 2011-02-07
I don't think it would be a good idea, compiling from source using prefix should be safer if doing it correctly.

---

### Post by apmcd47 on 2011-02-07
It's a long time since I compiled GCC but I recall that you should compile it at least twice so that it is compiled by itself.

---

### Post by toolzen on 2011-02-07
I'll agree that compiling the source is probably the safest way to go. Just do a --prefix=/usr/local. That will keep everything nice and separate.

Another thing I do is make sure my PATH is set with /usr/local/bin as the first entry, so that the compiled versions of programs that I have will be ran before the native version, and I don't have to type the entire path. That is of course just a matter of preference.

---

### Post by r.stiltskin on 2011-02-08
I ran (from my build directory):
../gcc-3.3.6/configure --prefix=/usr/local/gcc-3.3
then ran make and make install so the new build was installed to /usr/local/gcc-3.3

I created a symlink from /usr/local/bin/g++ to /usr/local/gcc-3.3/bin/g++, and an equivalent link for gcc.  I haven't done extensive testing, but the C compiler seems to work.  g++ has a problem.  It compiles, but the compiled program won't run:

./test: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

SOLVED: I forgot I had to run ldconfig for /usr/local/gcc-3.3/lib.  After doing so, programs seem to be loading correctly.

Thanks for all of your suggestions.

---

