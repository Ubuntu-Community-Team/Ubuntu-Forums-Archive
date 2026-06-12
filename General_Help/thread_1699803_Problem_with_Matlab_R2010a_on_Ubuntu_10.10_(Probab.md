---
title: "Problem with Matlab R2010a on Ubuntu 10.10 (Probably Java problem))"
date: 2011-03-04
forum: General Help
---

### Post by twister89 on 2011-03-04
Hello to everybody,

last night after the correct installation of matlab 2010a on my just formatted ubuntu 10.10 (x86_64) i had a strange problem with java and can't really understand why.

When i lanch from the terminal

```
/matlab path/bin/glnxa64/MATLAB -desktop
```

it appears the splash screen, but no more, and matlab loads in the command line mode. Then when i try to lanch from the matlab prompt "demo" or "helpdesk", it says:

```
>> demo
??? Error using ==> demo at 23
demo is not supported because Java is not currently available
```

Anyone could help me??

I tried also without the graphics effects of compiz and from the ubuntu wiki guide, launching from the ubuntu terminal:

```
export MATLAB_JAVA=/usr/lib/jvm/java-6-openjdk/jre/
```

Thank you for your help guys

---

### Post by Topsiho on 2011-03-04
Hello,

I don't know whether you have a special reason to use Matlab itself.
In the repositories you'll find a very nearly perfect Matlab clone, Octave, which you could use instead of Matlab.

This reply doesn't help you with your Java problem, but you might as well use Octave. And it costs you nothing (us Dutchies love that :) ).

Just google Octave to find more information about it :)

Topsiho

---

### Post by tommpogg on 2011-07-04
Have you tried to launch Matlab without Java Virtual Machine (JVM)?

matlab -nojvm

If it works, it could be a problem of the JVM.

PS: I just discovered [this thread]("http://ubuntuforums.org/showthread.php?t=781078&highlight=compiz+matlab"). It is related to the installation of Matlab 2008a, but it could be useful

---

