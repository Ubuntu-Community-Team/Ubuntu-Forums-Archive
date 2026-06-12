---
title: "Install Mono for .Net apps"
date: 2009-07-09
forum: General Help
---

### Post by CrusaderAD on 2009-07-09
How exactly do you install Mono for Ubuntu? I try to run a VB app I made and it says:

> install the Windows version of Mono to run .NET executables

Yes, I tried:

```
sudo apt-get install mono
```

It says:

> This may mean that the package is missing, has been obsoleted, or
is only available from another source

Any ideas?

---

### Post by Oblivion_4 on 2009-07-09
ubuntu comes with mono because there are one or two apps that depend on the mono libraries. One of them is Tomboy notes. However, if you want to do C# in ubuntu you will be limited to the C# v2.0 apis because there are a number of problems with porting C# v3.0 or higher to linux.

For one, linux distros don't want to get sued for porting C#3.0 to linux or creating applications they want credit for. For two, most linux programmers are overly biased against anything made by microsoft in general.

---

### Post by directhex on 2009-07-09
> **raptormanad said:**
> How exactly do you install Mono for Ubuntu? I try to run a VB app I made and it says:



Yes, I tried:

```
sudo apt-get install mono
```

It says:



Any ideas?

There's no "mono" package, but there's a "mono" source package, which produces about 100 binary packages.

Generally, run "mono myapp.exe". If it bails out, usually it'll tell you an assembly is missing (I guess in your case it'll be Microsoft.VisualBasic 8.0.0.0). Install the missing libs - e.g. libmono-microsoft-visualbasic8.0-cil in this example.

Another reason an app might fail to run, if all libraries are present, is that the app is badly written - for example, you try to read registry values without try{}catch{}, or you use "foo\bar" for file paths instead of System.IO.Path.Combine("foo","bar"). The latter example there's a horrible hack (export MONO_IOMAP=all), but some cases not.

Oh, and if you DllImport any Windows-only libraries, you're out of luck.

---

### Post by CrusaderAD on 2009-07-10
Thanks for the replies, I'll have to look into it more.

---

