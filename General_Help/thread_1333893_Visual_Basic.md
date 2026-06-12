---
title: "Visual Basic???"
date: 2009-11-21
forum: General Help
---

### Post by eranga1988 on 2009-11-21
Hello guyz,
              First of all I wanna say I am new to Ubuntu(Linux). The problem I met was I am studying Visual Basic these days in my university. So I wanna know is there any method to install visual basic on ubuntu 9.10. If there is any method I wanna know each and every step as I am not a Linux professional. Thanx!!!:)
(Sorry about english. I am a Sri Lankan);)

---

### Post by QIII on 2009-11-21
Easily? No.

Visual Basic is a Microsoft product.

You could try to install Wine (not my area of expertise) and see if Visual Studio works, but I doubt it seriously.

There is also the Mono Project, which is working on making it possible to use such products on Linux platforms.  I can't say that it will really do what you need.

[http://www.mono-project.com](http://www.mono-project.com)

---

### Post by river226 on 2009-11-21
here this thread may help you a little:
[http://www.uluga.ubuntuforums.org/showthread.php?t=686431](http://www.uluga.ubuntuforums.org/showthread.php?t=686431)

---

### Post by eranga1988 on 2009-11-21
> **QIII said:**
> Easily? No.

Visual Basic is a Microsoft product.

You could try to install Wine (not my area of expertise) and see if Visual Studio works, but I doubt it seriously.

There is also the Mono Project, which is working on making it possible to use such products on Linux platforms.  I can't say that it will really do what you need.

[http://www.mono-project.com](http://www.mono-project.com)
Thanx dude....:DI will try..When I search on google regarding this problem I got something called Winbuntu. Do you know anything about that???

---

### Post by QIII on 2009-11-21
Let me say that there are a lot of us in this community who wonder why anyone would ever want to ask Microsoft to the party.

This is Linux.

---

### Post by QIII on 2009-11-21
> **eranga1988 said:**
> Do you know anything about that???

Not a clue.

Linux is Linux.  Use Windows if you need it.  There's absolutely nothing wrong with that.

If you want to use Linux, use Linux.  If you want to use Windows, use Windows.

VB.NET is made for Windows and best fed in its own pasture.

---

### Post by directhex on 2009-11-22
[mono-vbnc](apt:mono-vbnc)
[monodevelop](apt:monodevelop)

Assuming you want VB.NET and not VB6, anyway.

Other posters in this thread are right that VB.NET is a horrible language, but are wrong about VB.NET being tied to Windows in any way (other than bad programming).

They're also missing the point a little - the reason by the VB.NET compiler package exists in Ubuntu is because I uploaded it, and I uploaded it not because I want it (I hate VB.NET), but to make sure that when people come along and say "I really love Ubuntu but I want VB.NET to work on my apps or on a programming course that needs it or something", they aren't turned away at the door

```
directhex@despair:/tmp$ cat hello.vb
Module Example
    Sub Main()
        System.Console.WriteLine("Hello UbuntuForums!")
    End Sub
End Module
directhex@despair:/tmp$ vbnc hello.vb
Visual Basic.Net Compiler version 0.0.0.5914 (Mono 2.4.2 - r)
Copyright (C) 2004-2008 Rolf Bjarne Kvinge. All rights reserved.


Assembly 'hello, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' saved successfully to '/tmp/hello.exe'.
Compilation successful
Compilation took 00:00:01.7451410
directhex@despair:/tmp$ mono hello.exe
Hello UbuntuForums!
directhex@despair:/tmp$
```

---

### Post by QIII on 2009-11-23
> **directhex said:**
> Other posters in this thread are right that VB.NET is a horrible language, but are wrong about VB.NET being tied to Windows in any way (other than bad programming).

They're also missing the point a little - the reason by the VB.NET compiler package exists in Ubuntu is because I uploaded it, and I uploaded it not because I want it (I hate VB.NET), but to make sure that when people come along and say "I really love Ubuntu but I want VB.NET to work on my apps or on a programming course that needs it or something", they aren't turned away at the door

.NET is a native Microsoft technology.  It is not in any way wrong or incorrect to say that.  It is, in point of fact, made for Windows.  That a compiler is available in Ubuntu through your efforts does not change that fact.  It simply shows that someone clever enough can adapt and port it.  And the fact remains that the easiest way to develop in .NET is by using its native development environment.

I didn't see anyone pointing the OP to the door.  In fact, a certain poster, who will remain nameless, specifically mentioned mono -- because he is pragmatic.

I make an obscene amount of money using .NET at my day job.  I certainly would not deprive others of doing the same.  Pragmatism is not a bad thing.

---

### Post by directhex on 2009-11-23
> **QIII said:**
> .NET is a native Microsoft technology.  It is not in any way wrong or incorrect to say that.

The ISO/EMCA-standard core of .NET is platform agnostic by design (See: System.IO.Path.DirectorySeparatorChar et al), and Microsoft have had their own cross-platform implementation available for years ([http://en.wikipedia.org/wiki/Rotor_Programming](http://en.wikipedia.org/wiki/Rotor_Programming)). System-specific namespaces notwithstanding (and, conversely, Mono also has some UNIX-specific namespaces for those who want them).

> the fact remains that the easiest way to develop in .NET is by using its native development environment.

No more true than "the easiest way to develop C is by using vi on a UNIX server". Generalizations are wrong, in general. You may well be right *in this instance* that the path of least resistance is to run a legacy Microsoft stack, to ensure that all the guy's teaching materials are pixel-perfect identical, but that's really just semantics of one IDE versus another, and one GUI toolkit versus another. But users should be free to make an *informed* decision about their IT, including their development environment

> I didn't see anyone pointing the OP to the door.  In fact, a certain poster, who will remain nameless, specifically mentioned mono -- because he is pragmatic.

One vague hint, alongside a useless hint regarding Wine, and multiple less than subtle messages saying, and I quote, "Let me say that there are a lot of us in this community who wonder why anyone would ever want to ask Microsoft to the party." You're strongly discouraging someone from using Free Software, and recommending they stick to legacy Microsoft software. The keyword, again, is *informed* choice. Being told there's no usable alternative isn't being informed.

---

### Post by QIII on 2009-11-23
> ([http://en.wikipedia.org/wiki/Rotor_Programming](http://en.wikipedia.org/wiki/Rotor_Programming))No! Really?  Key point: Educational/non commercial use.  He is using it for an educational purpose.  Hence, my reference to mono.  Were I not aware that .NET can be used cross-platform, I would not have mentioned mono.  I am "native" to the US.  That does not mean I can't operate "cross-platform" in Germany.  My own ".NET" includes the German language "library" for easy compiling.  Nevertheless, I am "native" to the US.

> No more true than "the easiest way to develop C is by using vi on a UNIX server"That is a leap and I am sure you are well aware of that, having studied Logic.  I engaged neither in Non Sequitur nor Reductio Ad Absurdum.

> One vague hint, alongside a useless hint regarding WineI hardly call telling someone about mono and providing a link (with the useful and informative caveat that it may not do exactly what he wants) to be vague.  I mentioned wine because it is available, but I also said it was not my area of expertise.  

> "Let me say that there are a lot of us in this community who wonder why anyone would ever want to ask Microsoft to the party."Is this not true?

> You're strongly discouraging someone from using Free Software, and recommending they stick to legacy Microsoft software. The keyword, again, is *informed* choice. Being told there's no usable alternative isn't being informed.No, I wasn't.  And I gave him an alternative.  Thus, I didn't tell him there was no usable alternative.  

Are you saying .NET is not best pastured in its own field?

I use Microsoft products 8 hours a day.  I do not discourage their use.  In fact, I usually tell people that I have no problem with them using Microsoft products.  However, I am not a Microsoft evangelist.

I use Linux and OpenSolaris when I can.  I do not discourage their use.  I tell people I have no problem using either of them.  However, I am not a Linux nor an OpenSolaris evangelist.

If you will read some of my other posts, you will find that I tell others to use what works for them, Microsoft or not.

You evangelize if you care to.

I am stepping away from your flame.

---

### Post by Commander_Keen on 2009-11-23
the best thing to do is to download codeweavers  and install it that way.

---

### Post by QIII on 2009-11-23
Also a viable alternative.

---

