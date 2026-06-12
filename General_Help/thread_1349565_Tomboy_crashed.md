---
title: "Tomboy crashed"
date: 2009-12-08
forum: General Help
---

### Post by afrodeity on 2009-12-08
Tomboy crashed. I reinstalled mono and now its giving me this weird output in terminal


```

$tomboy

** (/usr/lib/tomboy/Tomboy.exe:32128): WARNING **: The following assembly referenced from /usr/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tomboy/).


** (/usr/lib/tomboy/Tomboy.exe:32128): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Tomboy.Tomboy' from assembly 'Tomboy, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'


```

Is it a problem with the keys, or the path?

---

### Post by afrodeity on 2009-12-08
OK, think I got it.Its the GTK keybindings for Mono which aren't installed. 

[http://ubuntuforums.org/showthread.php?t=474458](http://ubuntuforums.org/showthread.php?t=474458)

---

### Post by afrodeity on 2009-12-08
I've installed gtk-sharp, and reinstalled tomboy, but still same error. I don't get it.

---

### Post by afrodeity on 2009-12-08
It appears to be trying to load gtk-sharp, Version=2.12.0.0

but gtk-sharp 2.12.9-1 is installed. This could be the problem, versioning issue. How do I fix?

---

### Post by afrodeity on 2009-12-09
I downloaded latest version & compiled gtk-sharp from source
```

gacutil -l gtk-sharp
The following assemblies are installed into the GAC:
gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
Number of items = 1

```

now i get

```

** (/usr/lib/tomboy/Tomboy.exe:14502): WARNING **: The following assembly referenced from /usr/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   gnome-panel-sharp    (assemblyref_index=3)
     Version:    2.24.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tomboy/).


** (/usr/lib/tomboy/Tomboy.exe:14502): WARNING **: Could not load file or assembly 'gnome-panel-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

** (/usr/lib/tomboy/Tomboy.exe:14502): WARNING **: The following assembly referenced from /usr/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=12)
     Version:    2.24.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tomboy/).


** (/usr/lib/tomboy/Tomboy.exe:14502): WARNING **: Could not load file or assembly 'gnome-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Tomboy.Logger ---> System.TypeInitializationException: An exception was thrown by the type initializer for Tomboy.Services ---> System.TypeLoadException: A type load exception has occurred.
  at Tomboy.Services..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Tomboy.FileLogger..ctor () [0x00000] 
  at Tomboy.Logger..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 


```

However compiling gnome-sharp not as simple. There are options after ./configure to include the dll, the default is no! How do i change options?

---

### Post by afrodeity on 2009-12-09
Downloaded and installed gnome-desktop-sharp

All of the above with --prefix=/usr/local

Found a better tutorial for all of this [here]("http://www.centriment.com/2009/04/01/building-mono-24-from-source-on-ubuntu-810/comment-page-1/?replytocom=14")

But since i removed the broken default mono I have to press on.

Doing above fixed the gnome-panel-sharp problem but still stuck with gnome-sharp issue.

There's a good FAQ[ here]("http://gtk-sharp.sourceforge.net/faq.html")

[I] Why can't mono find gtk-sharp.dll?
You most likely have installed Gtk# into a prefix other than where mono is installed.  In order for the runtime to locate the Gtk# assemblies, you will need to add their location to the MONO_GAC_PREFIX environment variable. For the default installation prefix, this will mean executing the following command[/I]:

```
export MONO_GAC_PREFIX=/usr/local:$MONO_GAC_PREFIX
```

But doing this hasn't helped find gnome-sharp which

usr/lib/cli/gnome-sharp-2.24
/usr/lib/cli/gnome-sharp-2.24/gnome-sharp.dll
/usr/lib/cli/gnome-sharp-2.24/gnome-sharp.dll.config

---

### Post by afrodeity on 2009-12-09
[http://ubuntuforums.org/showthread.php?t=640121](http://ubuntuforums.org/showthread.php?t=640121)

---

### Post by afrodeity on 2009-12-09
This did it for me:

cd /usr/lib/mono/gac # assuming this is your main gac
sudo find . */*/*.dll -exec gacutil -i '{}' \;

Ignore all the warnings.

---

### Post by afrodeity on 2009-12-09
Somebody should make a nice curses interface for the "curse"

---

### Post by afrodeity on 2009-12-11
Option 1: Totally remove mono & mono-based apps

Option 2: Purge & Reinstall Mono from repos

Option 3: Download latest Mono from Novell & Compile & Install

Option 4. Fix GAC

Option 5: Find & Create Path to Alternative GAC

Option 6: Update GAC & Install Mono App to Cache

Option 7: Become a MonoTheist

---

### Post by afrodeity on 2009-12-11
Option 1: Totally remove mono & mono-based apps

Option 2: Purge & Reinstall Mono from repos

Option 3: Download latest Mono from Novell & Compile & Install

Option 4. Fix GAC

Option 5: Find & Create Path to Alternative GAC

Option 6: Update GAC & Install Mono App to Cache

Option 7: Become a MonoTheist

---

### Post by CupofDice on 2010-01-04
Thanks for making all of the posts :D. Ran into the same problem, and your thread helped greatly.

---

### Post by Bobulous on 2010-01-04
I was using Gnotes (a GNOME clone of Tomboy that is written in C++ so it doesn't require Mono) until I found that hitting Ctrl+Enter while over a link was causing the whole application to crash about half the time.

Tomboy hasn't given me any trouble so far, but I'll try to remember this thread is here if something goes awry.

---

### Post by afrodeity on 2010-01-05
Thanks, for a while there it was self-support between me myself and my echo. Happy it helped somebody.:)

---

