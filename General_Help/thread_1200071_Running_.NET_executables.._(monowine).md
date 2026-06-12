---
title: "Running .NET executables.. (mono/wine)"
date: 2009-06-29
forum: General Help
---

### Post by Addikit on 2009-06-29
Hey guys, I apologize, I know I've been asking a million questions and I don't know anything to really provide back to the community. But I'm having a problem running a pretty simple program that requires .NET Frameworks and I tried following this guide [http://www.goitexpert.com/general/run-asp-and-net-in-ubuntu--and-debian-linux/](http://www.goitexpert.com/general/run-asp-and-net-in-ubuntu--and-debian-linux/) and really I only got as far as installing all of the packages through Synaptic (sudo apt-get didn't work) but I made sure I got everything installed but really I didn't see much else on how to actually run the application. I was under the impression that I don't use Wine, I use Mono to run the application?

Sorry for being such a nub

Also, this is the error I get when trying to run it with Wine "install the Windows version of Mono to run .NET executables" isn't the Windows version of Mono .NET Frameworks? Do I really need to try and install that?

---

### Post by directhex on 2009-06-29
> **Addikit said:**
> Hey guys, I apologize, I know I've been asking a million questions and I don't know anything to really provide back to the community. But I'm having a problem running a pretty simple program that requires .NET Frameworks and I tried following this guide [http://www.goitexpert.com/general/run-asp-and-net-in-ubuntu--and-debian-linux/](http://www.goitexpert.com/general/run-asp-and-net-in-ubuntu--and-debian-linux/) and really I only got as far as installing all of the packages through Synaptic (sudo apt-get didn't work) but I made sure I got everything installed but really I didn't see much else on how to actually run the application. I was under the impression that I don't use Wine, I use Mono to run the application?

Sorry for being such a nub

Also, this is the error I get when trying to run it with Wine "install the Windows version of Mono to run .NET executables" isn't the Windows version of Mono .NET Frameworks? Do I really need to try and install that?

You've given 0 detail on the app or errors, so impossible to give more than general advice

General advice: Wine uses Mono-for-Windows for running .NET apps rather than Microsoft.NET because, for one thing, it's miles easier to get working

General advice: .NET apps may fail to run on Mono on Linux if they 1) use libs not available on Mono 2) do platform-specific things like p/invoke windows libraries

---

### Post by Addikit on 2009-06-29
> **directhex said:**
> You've given 0 detail on the app or errors, so impossible to give more than general advice

General advice: Wine uses Mono-for-Windows for running .NET apps rather than Microsoft.NET because, for one thing, it's miles easier to get working

General advice: .NET apps may fail to run on Mono on Linux if they 1) use libs not available on Mono 2) do platform-specific things like p/invoke windows libraries

If I knew how to further try and run the program I guess I could give more of an error message (if there was one) other than what Wine gives me.

The application is called BlackcatLPT it helps me flash the firmware on cable modems.

---

### Post by directhex on 2009-06-29
> **Addikit said:**
> If I knew how to further try and run the program I guess I could give more of an error message (if there was one) other than what Wine gives me.

The application is called BlackcatLPT it helps me flash the firmware on cable modems.

Won't work with "just" Mono. Calls directly into kernel32.dll (the Windows NT kernel) which is pretty much as non-portable as can be

---

### Post by moster on 2009-06-29
I made before when I was in windows dictionary for myself. It was built in visual basic net. It works in ubuntu too. I do not know in which language your program is made, but it should not be too much problem because all .net program generate at least similar code.

I have installed monodevelop from add/remove and mono-vbnc (visual basic compiler for linux) from synaptic.

If you have all that installed, just in terminal type ```
mono NameOfApplication.exe
``` and cross fingers.

I somehow dubt it will work because you use that prog to comunicate to hardware. It is not very simple...

---

### Post by Addikit on 2009-06-29
> **directhex said:**
> Won't work with "just" Mono. Calls directly into kernel32.dll (the Windows NT kernel) which is pretty much as non-portable as can be

So I wont be able to get it to work?

---

### Post by Addikit on 2009-06-29
> **moster said:**
> I made before when I was in windows dictionary for myself. It was built in visual basic net. It works in ubuntu too. I do not know in which language your program is made, but it should not be too much problem because all .net program generate at least similar code.

I have installed monodevelop from add/remove and mono-vbnc (visual basic compiler for linux) from synaptic.

If you have all that installed, just in terminal type ```
mono NameOfApplication.exe
``` and cross fingers.

I somehow dubt it will work because you use that prog to comunicate to hardware. It is not very simple...

Yeah, it was a fail =/
```

mono /media/Anime/Modem/BlackcatLPT.140/SchwarzeKatze/SchwarzeKatze.exe

** (/media/Anime/Modem/BlackcatLPT.140/SchwarzeKatze/SchwarzeKatze.exe:13842): WARNING **: The following assembly referenced from /media/Anime/Modem/BlackcatLPT.140/SchwarzeKatze/SchwarzeKatze.exe could not be loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=1)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/media/Anime/Modem/BlackcatLPT.140/SchwarzeKatze).


** (/media/Anime/Modem/BlackcatLPT.140/SchwarzeKatze/SchwarzeKatze.exe:13842): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.

```

I suppose I might need to dual boot :(

---

### Post by directhex on 2009-06-29
> **Addikit said:**
> So I wont be able to get it to work?

*MAYBE* if you do as you're told, and install Mono for Windows with WINE. But your app is non-portable, due to invoking parts of kernel32

---

### Post by moster on 2009-06-30
Your program is obviusly made in Visual Basic.NET and I see by your last post that you do not have installed visual basic compiler. SO, you must go to synaptic and search for "visual basic". Now, when  narrow results select "mono-vbnc" and "libmono-microsoft-visualbasic8.0-cil"

NOW, cross fingers again, but even tighter and try again "mono App.exe :D

Again I dubt but this is right way to try, if again not work you can give up.

---

### Post by directhex on 2009-06-30
> **moster said:**
> Your program is obviusly made in Visual Basic.NET and I see by your last post that you do not have installed visual basic compiler. SO, you must go to synaptic and search for "visual basic". Now, when  narrow results select "mono-vbnc" and "libmono-microsoft-visualbasic8.0-cil"

NOW, cross fingers again, but even tighter and try again "mono App.exe :D

Again I dubt but this is right way to try, if again not work you can give up.

How's that gonna help the kernel32 issue?

---

### Post by moster on 2009-06-30
> **directhex said:**
> How's that gonna help the kernel32 issue?

hm, I did not see it... :) I just saw that he do not have everything that he could actually run any VB.NET apps.

edit:
btw, funny avatar :D

---

### Post by Addikit on 2009-07-01
I really appreciate you guys taking the time to look into my issue :)

My sister ended up giving me a laptop that has an LPT port so I wont need to dual boot my system, I can just use that for my extra hobby :)

---

### Post by babygenius55 on 2011-08-22
Why is it that nearly every thread I read pertaining to mono is chock full of snide replies?  It (Whine) directs you to install it.  That's all it does.  Then what?  Wine??? doesn't work.  mono??? doesn't work.

---

### Post by directhex on 2011-08-23
> **babygenius55 said:**
> Why is it that nearly every thread I read pertaining to mono is chock full of snide replies?

Because you're trawling through threads which are over 2 years old?

And in the general case, because correct advice is ignored in favour of wrong advice - this is not limited to Mono threads, it's a general case on Ubuntu Forums.

---

