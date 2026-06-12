---
title: "How to run .net application using mono  ???"
date: 2010-09-21
forum: General Help
---

### Post by q8.legend on 2010-09-21
Hi

I heared that there is an application for ubuntu that can run .net application under ubuntu... They told me to use mono. Since, wine cannot run .net application, it only can run .exe files....

I did installed mono using this tutorial in this site
[http://mono-project.com/DistroPackages/Ubuntu](http://mono-project.com/DistroPackages/Ubuntu)

and I did installed mono utilities from synaptic. but, I don't know how to run the application using mono !! I tried to click the right mouse and run it with it. but I didn't see mono from the list. also, I tried to search for it from the application & I didn't find it. Maybe its just a setting and cannot run it like an application... If that its right, how can I run the application then ??


Note:
I'm running under ubuntu 10.04 64bit, and i'm trying to run subtitle workshop under ubuntu. It requires the .Net framework 2.0.
When I run it under wine, it tolds me that it needs .net framework to run...

---

### Post by WorMzy on 2010-09-21
There is no GUI for running mono apps, and therefore no "open with" entry for it. Instead, you need to use a terminal. Browse to the location of the .net app with cd, e.g.

```
cd /home/legend/Documents/dotnetapps
```

then run it with

```
mono <appname>
```

---

### Post by Tibuda on 2010-09-21
> **WorMzy said:**
> There is no GUI for running mono apps, and therefore no "open with" entry for it. Instead, you need to use a terminal. Browse to the location of the .net app with cd, e.g.

```
cd /home/legend/Documents/dotnetapps
```

then run it with

```
mono <appname>
```

You can use the "Open with" option in the right-click menu, select "Use a custom command" and type "mono", without using a terminal.

Note that some .net apps won't run on Mono. If you are the developer, you could try to use the [Migration Analyzer](http://www.mono-project.com/MoMA).

---

### Post by q8.legend on 2010-09-21
I got this error when i tried to run it in the terminal

"The assembly mscorlib.dll was not found or could not be loaded. It should have been installed in the `/usr/lib/mono/1.0/mscorlib.dll' directory."

???

---

### Post by directhex on 2010-09-23
> **q8.legend said:**
> I got this error when i tried to run it in the terminal

"The assembly mscorlib.dll was not found or could not be loaded. It should have been installed in the `/usr/lib/mono/1.0/mscorlib.dll' directory."

???

Your app is built for .NET 1.1, and recent versions of Ubuntu only support .NET 2.0->3.5

Install the package [mono-complete](apt:mono-complete) and it should pull in the unsupported 1.1 runtime stuff. If not, there's a Mono parameter to force it to load 1.1 apps using the 2.0 runtime. mono --runtime=v2.0.50727 program.exe

---

### Post by philnice on 2011-01-09
Tibuda, thanks for the tip! i wanted to run nbuexplorer (that works under mono) to open an arc backup file from my nokia 5800, and got the same message through terminal.
Everything works now. :)

---

