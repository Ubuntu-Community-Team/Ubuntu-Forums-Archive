---
title: "What version of Mono do I have and how do I upgrade to latest"
date: 2010-05-06
forum: General Help
---

### Post by gregarobinson on 2010-05-06
I am new to Linux and Ubuntu. I have been working with it for a few days now. 

I am trying to port a .NET 3.5 application over to Ubuntu. I need to know what version of Mono the Ubuntu box is running, and, if it's not the latest how do I upgrade to the latest version of Mono. 

I have MonoDevelop running. I have been able to Build the .NET solution successfully, but I am missing 2 dlls that Googling tells me should be included in Mono. 

Thanks in advance.

---

### Post by Wamiduku on 2011-03-10
The OP is probably not even on the forums anymore, but I was searching for the same info, so I'll post what I found for the benefit of the next person searching.

> **gregarobinson said:**
> I need to know what version of Mono the Ubuntu box is running

mono --version


>  ...and, if it's not the latest how do I upgrade to the latest version of Mono.

[http://ubuntuforums.org/showthread.php?t=1591370](http://ubuntuforums.org/showthread.php?t=1591370)

...if you think it's worth all the work.

---

### Post by WitchCraft on 2011-03-12
From 2.4 to 2.6 is definitely worth it, because XMLwriter/reader contains errors when overloaded with encoding.

From 2.6 to 2.8 doesn't make much difference, maybe bugfixes.

From 2.8 to 2.10 is advisable, because 2.10 contains the Razor template engine (ASP.NET MVC 3) and the VB .NET 4.0 compiler for Linux (until 2.10, only VB.NET 2.0 was possible, which was a bad thing because nHibernate 3 requires .NET 3.5+).

---

### Post by Asham on 2011-07-13
From the looks of it though its a long time til 2.10 is out. They released beta 3 for **2.6** about two months ago.

---

### Post by Wamiduku on 2011-07-13
> **Asham said:**
> From the looks of it though its a long time til 2.10 is out. They released beta 3 for **2.6** about two months ago.
The latest stable version is 2.10.2 and it was released in April. See [http://www.go-mono.com/mono-downloads/download.html](http://www.go-mono.com/mono-downloads/download.html).

Version 2.6 is not in beta. It was released in December 2009.

---

### Post by Asham on 2011-07-13
I did not read as carefully as I should. You are correct. The version number I was referring to is for **MonoDevelop** which is a different project. Sorry about that.

---

### Post by directhex on 2011-07-14
Oneiric contains Mono 2.10.1 and MonoDevelop 2.6 beta 3, FWIW

---

