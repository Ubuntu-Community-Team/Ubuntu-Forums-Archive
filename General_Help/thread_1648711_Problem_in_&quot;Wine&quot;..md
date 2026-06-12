---
title: "Problem in &quot;Wine&quot;."
date: 2010-12-19
forum: General Help
---

### Post by al prince nofl on 2010-12-19
Hey,

I have much problems in the wine program.
I am using Ubuntu 10.10

That's two of the error messages i get:
[IMG]http://oi54.tinypic.com/2a9b2xe.jpg[/IMG]

So i want to remove the program "wine" 100% then install the last version of it.
[update] I was meaning that i want to remove framework then install the last version of it.
I hope anyone can tell me what to do by terminal to do that.

Thanks,

---

### Post by I'mGeorge on 2010-12-19
your problem seams to be the Microsoft .NET Framework, you could try to download it and install it using wine from here [http://www.microsoft.com/downloads/en/details.aspx?FamilyID=0856eacb-4362-4b0d-8edd-aab15c5e04f5&displaylang=en](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=0856eacb-4362-4b0d-8edd-aab15c5e04f5&displaylang=en) to see how it goes

If you wanna completely remove wine do this
```

apt-get --purge remove wine

```

and if you wanna delete wine's directory also including the programs that were installed inside of it do this

```

rm -f -r ~/.wine

```

---

### Post by al prince nofl on 2010-12-19
> **I'mGeorge said:**
> your problem seams to be the Microsoft .NET Framework, you could try to download it and install it using wine from here [http://www.microsoft.com/downloads/en/details.aspx?FamilyID=0856eacb-4362-4b0d-8edd-aab15c5e04f5&displaylang=en](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=0856eacb-4362-4b0d-8edd-aab15c5e04f5&displaylang=en) to see how it goes



Yeah i think that's what i means, the Microsoft .NET Framework

I opened the link you sent to download the framework then i found there is new version "4" so i downloaded it "Microsoft .NET Framework.

But when i tried to open it i got this message:

The file '/home/alprincenofl/Desktop/dotNetFx40_Full_setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by al prince nofl on 2010-12-19
I also downloaded and test Microsoft .NET Framework v2 -which you sent- but also the same problem.

The file '/home/alprincenofl/Desktop/dotnetfx.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by Vigh on 2010-12-19
try

sudo apt-get remove --purge wine

go to the home folder, click view, show hidden files, delete the .wine folder the . in front just means its hidden

start from scratch in trying to set-up your program through wine

failing that, run a virtual machine, using ORACLE Virtual Box PESU edition

fantastic way of running windows apps whilst still enjoying benefits of linux

you do however still need a copy of windows even if its just XP and lots of memory to do this, running 2 OS simultaneously chews up the memory

---

### Post by Vigh on 2010-12-19
also regarding your may be dangerous to run error,

try installing through the wine installer system

go to wine in applications, click uninstall a wine program

then click install in there and select the executable file

usually works everytime if you do it that way

---

### Post by al prince nofl on 2010-12-19
> **Vigh said:**
> try

sudo apt-get remove --purge wine

go to the home folder, click view, show hidden files, delete the .wine folder the . in front just means its hidden

start from scratch in trying to set-up your program through wine

failing that, run a virtual machine, using ORACLE Virtual Box PESU edition

fantastic way of running windows apps whilst still enjoying benefits of linux

you do however still need a copy of windows even if its just XP and lots of memory to do this, running 2 OS simultaneously chews up the memory


I removed Wine, then installed it from the Ubuntu Software Center: 
Wine Microsoft Windows Compatibility Layer
Wine Microsoft Windows Compatibility Layer (Beta Release)

Tried to install the Microsoft .NET framework but still the same problem/ error.

And i also installed Virtual program but will test it later.

---

### Post by al prince nofl on 2010-12-19
> **Vigh said:**
> also regarding your may be dangerous to run error,

try installing through the wine installer system

go to wine in applications, click uninstall a wine program

then click install in there and select the executable file

usually works everytime if you do it that way

I tried through the wine installer system, and it just shows the version 4 of microsoft .net wile the two files is in the same place. anyway i tired to install but got another error and didn't installed..

---

### Post by Vigh on 2010-12-19
not sure what you are trying to install, if your trying to get office 2007 working in wine,

you need to install microsoft XML parser (MSXML) 3.0
Microsoft visual redistributable C++ 2005
then net framework 1.1 to be able to install it
and all the truetype fonts

in that order I think but could be wrong

if you need the latest .NET framework for example for AutoCAD2010 just stick with a virtual machine, find an old winxp cd and run it in a virtual machine

---

### Post by Vigh on 2010-12-19
with respect to the virtualbox program, its better to get it directly from the ORACLE website and install the PESU edition, the one in software centre is the OSE edition, which doesn't have 100% features, to get the PESU edition you do need to register an email address but it is still free

---

### Post by 3Miro on 2010-12-19
For .NET, use winetricks (remove ~/.wine first, you can have a clean folder to begin with, you don't have to reinstall wine-beta)

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Also, check with winehq database for specific instructions on how to install and run your specific software. Wine settings are specific for each program, so we cannot really help unless we know what the program is (I understand privacy, it is just hard for us to shoot int he dark).

---

### Post by al prince nofl on 2010-12-19
Well thanks for the help but i don't like the virtualbox or virtual idea in main. i installed virtualbox and will use it later when i have time.
I remember that there is way to install/upgrade Microsoft .NET Framework from the wine program by the terminal, i saw that from long time on the wine website and i will try to find it again then test it.

Thanks all,

---

