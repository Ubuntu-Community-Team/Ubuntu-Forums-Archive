---
title: "Mono: PublicKey  Different"
date: 2010-12-03
forum: General Help
---

### Post by AndrewAtkinson on 2010-12-03
On Ubuntu 10.04 (64bit)
Trying to run a dot net application on Mono I get the following error

```
andrew@janda:~/Desktop$ mono PocketTopo.exe 

** (PocketTopo.exe:2752): WARNING **: The following assembly referenced from /home/andrew/Desktop/PocketTopo.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=1)
     Version:    2.0.0.0
     Public Key: 969db8053d3322ac
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/andrew/Desktop/).


** (PocketTopo.exe:2752): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=969db8053d3322ac, Retargetable=Yes' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=969db8053d3322ac, Retargetable=Yes' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=969db8053d3322ac, Retargetable=Yes'
```Now looking this up on this and other forums generally tells me to install 
libmono-winforms2.0-cil
however, this is install  and trying 
gacutil -l | grep System.Windows.Forms
I get

```
System.Windows.Forms, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```Which I think shows that it is there and in the right place.

However, I notice that the PublicKey (Token) is different, is this causing the problem, if so can it be solved

thanks

---

### Post by directhex on 2010-12-03
> **AndrewAtkinson said:**
> On Ubuntu 10.04 (64bit)
Trying to run a dot net application on Mono I get the following error

```
andrew@janda:~/Desktop$ mono PocketTopo.exe 

** (PocketTopo.exe:2752): WARNING **: The following assembly referenced from /home/andrew/Desktop/PocketTopo.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=1)
     Version:    2.0.0.0
     Public Key: 969db8053d3322ac
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/andrew/Desktop/).


** (PocketTopo.exe:2752): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=969db8053d3322ac, Retargetable=Yes' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=969db8053d3322ac, Retargetable=Yes' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=969db8053d3322ac, Retargetable=Yes'
```Now looking this up on this and other forums generally tells me to install 
libmono-winforms2.0-cil
however, this is install  and trying 
gacutil -l | grep System.Windows.Forms
I get

```
System.Windows.Forms, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```Which I think shows that it is there and in the right place.

However, I notice that the PublicKey (Token) is different, is this causing the problem, if so can it be solved

thanks

Looks like your app is built against the .NET Compact Framework, not .NET. Mono doesn't support CF (although I believe JB Evain wrote an app to convert CF assembly references to non-CF)

b77a5c561934e089 is the Microsoft.NET key
969db8053d3322ac is the Compact Framework key

---

### Post by AndrewAtkinson on 2010-12-03
Okay that makes sense, but is a shame

I think I have found JB Evain code, at

[http://evain.net/public/cf-cecil-patcher.cs.html](http://evain.net/public/cf-cecil-patcher.cs.html)

but I have no idea what to do with this? Could you point me in the right direction for my research?

---

### Post by directhex on 2010-12-03
> **AndrewAtkinson said:**
> Okay that makes sense, but is a shame

I think I have found JB Evain code, at

[http://evain.net/public/cf-cecil-patcher.cs.html](http://evain.net/public/cf-cecil-patcher.cs.html)

but I have no idea what to do with this? Could you point me in the right direction for my research?

Compile it with the C# compiler of your choice (e.g. gmcs), and run "mono cf-patcher.exe foo.exe" (or "cf-patcher.exe foo.exe" on ms.net). It needs Cecil, so don't forget an -r:Mono.Cecil.dll

---

### Post by AndrewAtkinson on 2010-12-03
So I made a file cf-cecil-patcher.cs

And ran

$ gmcs -r:Cecil.dll cf-cecil-patcher.cs
error CS0006: cannot find metadata file `Mono.Cecil.dll'

A bit of searching (most of which was well beyond me) lead me to find the the
Mono.Cecil.dll

in the following 2 locations

/usr/lib/mono-cecil
/usr/lib/mono/gac/Mono.Cecil/0.6.9.0__0738eb9f132ed756

So went for

```
$ gmcs -L /usr/lib/mono-cecil -L /usr/lib/mono/gac/Mono.Cecil/0.6.9.0__0738eb9f132ed756 -r:Mono.Cecil.dll cf-cecil-patcher.cs 
warning CS8029: Compatibility: Use -lib:ARG instead of --L arg
warning CS8029: Compatibility: Use -lib:ARG instead of --L arg
Compilation succeeded - 2 warning(s)

```okay warnings, -lib would have allowed a comma separated list, but it compiled.

So

```
$ mono cf-cecil-patcher.exe PocketTopo.exe 

** (cf-cecil-patcher.exe:3642): WARNING **: The following assembly referenced from /home/andrew/Desktop/cf-cecil-patcher.exe could not be loaded:
     Assembly:   Mono.Cecil    (assemblyref_index=0)
     Version:    0.6.0.0
     Public Key: (none)
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/andrew/Desktop/).


** (cf-cecil-patcher.exe:3642): WARNING **: Could not load file or assembly 'Mono.Cecil, Version=0.6.0.0, Culture=neutral, PublicKeyToken=null' or one of its dependencies.
The entry point method could not be loaded
```That is a shame!

```
$ gacutil -l | grep Mono.Cecil
Mono.Cecil, Version=0.6.9.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756

```Does this mean that the patch does not cover this function?

Thanks

---

### Post by directhex on 2010-12-03
> **AndrewAtkinson said:**
> So I made a file cf-cecil-patcher.cs

And ran

$ gmcs -r:Cecil.dll cf-cecil-patcher.cs
error CS0006: cannot find metadata file `Mono.Cecil.dll'

A bit of searching (most of which was well beyond me) lead me to find the the
Mono.Cecil.dll

in the following 2 locations

/usr/lib/mono-cecil
/usr/lib/mono/gac/Mono.Cecil/0.6.9.0__0738eb9f132ed756

So went for

```
$ gmcs -L /usr/lib/mono-cecil -L /usr/lib/mono/gac/Mono.Cecil/0.6.9.0__0738eb9f132ed756 -r:Mono.Cecil.dll cf-cecil-patcher.cs 
warning CS8029: Compatibility: Use -lib:ARG instead of --L arg
warning CS8029: Compatibility: Use -lib:ARG instead of --L arg
Compilation succeeded - 2 warning(s)

```okay warnings, -lib would have allowed a comma separated list, but it compiled.

So

```
$ mono cf-cecil-patcher.exe PocketTopo.exe 

** (cf-cecil-patcher.exe:3642): WARNING **: The following assembly referenced from /home/andrew/Desktop/cf-cecil-patcher.exe could not be loaded:
     Assembly:   Mono.Cecil    (assemblyref_index=0)
     Version:    0.6.0.0
     Public Key: (none)
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/andrew/Desktop/).


** (cf-cecil-patcher.exe:3642): WARNING **: Could not load file or assembly 'Mono.Cecil, Version=0.6.0.0, Culture=neutral, PublicKeyToken=null' or one of its dependencies.
The entry point method could not be loaded
```That is a shame!

```
$ gacutil -l | grep Mono.Cecil
Mono.Cecil, Version=0.6.9.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756

```Does this mean that the patch does not cover this function?

Thanks

You specified two search paths for Mono.Cecil, but only one of them is systemwidef for running apps.

Try copying /usr/lib/mono-cecil/Mono.Cecil.dll to the same folder as cf-cecil-patcher.exe

---

### Post by AndrewAtkinson on 2010-12-04
Okay copied into the Directory, but got exactly the same error.

To help my learning, how could I have identified the systemwide version or got it chosen when I compiled.
Can I go back and do that now?

---

### Post by directhex on 2010-12-04
> **AndrewAtkinson said:**
> Okay copied into the Directory, but got exactly the same error.

To help my learning, how could I have identified the systemwide version or got it chosen when I compiled.
Can I go back and do that now?

jms@osc-bigmac:/tmp$ gmcs -pkg:mono-cecil cf-cecil-patcher.cs
jms@osc-bigmac:/tmp$ cp $(pkg-config --variable=Libraries mono-cecil) .
jms@osc-bigmac:/tmp$ mono cf-cecil-patcher.exe
Mono Assembly To Compact Framework Patcher
usage: cf-patcher.exe assembly

---

### Post by AndrewAtkinson on 2010-12-07
Okay needed to spend a bit of time working out what your commands where trying to do, not sure I have totally followed it fully but went for it

```
Survey$ gmcs -pkg:mono-cecil cf-cecil-patcher.cs
Survey$ cp $(pkg-config --variable=Libraries mono-cecil) .
Survey$ mono cf-cecil-patcher.exe
Mono Assembly To Compact Framework Patcher
usage: cf-patcher.exe assembly
Survey$ mono cf-cecil-patcher.exe PocketTopo.exe 
Assembly PocketTopo.exe patched
```I hope the last line was the right thing to do? It did something different, but still no PocketTopo running.

mono PocketTopo.exe gives the same error as in the first post of the thread?

---

### Post by directhex on 2010-12-07
> **AndrewAtkinson said:**
> Okay needed to spend a bit of time working out what your commands where trying to do, not sure I have totally followed it fully but went for it

```
Survey$ gmcs -pkg:mono-cecil cf-cecil-patcher.cs
Survey$ cp $(pkg-config --variable=Libraries mono-cecil) .
Survey$ mono cf-cecil-patcher.exe
Mono Assembly To Compact Framework Patcher
usage: cf-patcher.exe assembly
Survey$ mono cf-cecil-patcher.exe PocketTopo.exe 
Assembly PocketTopo.exe patched
```I hope the last line was the right thing to do? It did something different, but still no PocketTopo running.

mono PocketTopo.exe gives the same error as in the first post of the thread?

Okay, after only 4 days, you've said what you're trying to run.

Ignoring the public key issue (the cf-cecil-patcher.cs file needs adjusting to do what you want), PocketTopo uses System.Windows.Forms.DataGrid, which is not in Mono, so you can't run it. End of story.

---

### Post by AndrewAtkinson on 2010-12-07
I beg to differ, I had the line PocketTopo.exe in the fist post, so I did say what I was trying to run, and gave the error. 

Or was 
mono PocketTopo.exe

not enough, maybe that reveals my ignorance in trying to do this. But that is not the point, I am trying to learn and give enough info so others following this thread can also learn. 

If despite trying to give all the info that is needed, a polite prompting would be better than leading me astray. Also a little explanation of why things you suggested are done might have helped, with this information I probably could have spotted that you had not picked up that I was trying to run PocketTopo.

An example that I would like to know the answer to is: how do you know it is trying to use System.Windows.Forms.DataGrid ?
As far as I can tell the error only refers to System.Windows.Forms


Whatever, there was no need for the rude line

             > Okay, after only 4 days, you've said what you're trying to run.If anything this says more about your support than the errors I may or may not have done, due to me being a beginner at this.

All that said, if I ignore the quote above, thanks for your help, I have learnt a little more, and I hope you can pointers about giving reasons allows you to help others even more in future, I hope one day to have enough knowledge to help others myself.

I suppose that counts as solved: it does not work.

---

### Post by directhex on 2010-12-07
> If despite trying to give all the info that is needed, a polite prompting would be better than leading me astray. Also a little explanation of why things you suggested are done might have helped, with this information I probably could have spotted that you had not picked up that I was trying to run PocketTopo.

90-95% of people asking for help in these parts really really don't care about "why", nor about a correct solution - just something quick that works. Apologies for assuming you were part of that majority.

> An example that I would like to know the answer to is: how do you know it is trying to use System.Windows.Forms.DataGrid ?
As far as I can tell the error only refers to System.Windows.Forms

"monodis --assemblyref name-of-assembly.exe" returns a list of all the libraries used by a given app. Every "Name" field refers to a .dll file which should be available in "gacutil -l" or the current folder.

---

