---
title: "Asp"
date: 2010-12-14
forum: General Help
---

### Post by oerli on 2010-12-14
Hi

I have a few pages written in asp and javascript.
I want to run them on ubuntu. but it doesnt seem to work
Ik installed mono, and i can write some code in a .aspx file, but i don't know what language i am writing in, i looked up code in c# but it doesnt work all the time, so i don't really know what the language is
after every line i have to put a ;
Can someone tell me in what language i have to write my asp pages

Or even better, can anyone tell me how i can make the .asp files work.
Because than i can use the .asp files i have, without rewriting them

grts

---

### Post by jim_deadlock on 2010-12-14
You will not be able to run ASP pages on any type of Linux, it's a Windows language and will only run properly on a Windows server. C# is also for Windows.

---

### Post by directhex on 2010-12-14
> **oerli said:**
> Hi

I have a few pages written in asp and javascript.
I want to run them on ubuntu. but it doesnt seem to work
Ik installed mono, and i can write some code in a .aspx file, but i don't know what language i am writing in, i looked up code in c# but it doesnt work all the time, so i don't really know what the language is
after every line i have to put a ;
Can someone tell me in what language i have to write my asp pages

Or even better, can anyone tell me how i can make the .asp files work.
Because than i can use the .asp files i have, without rewriting them

grts

ASP is a Microsoft-only language. It was last updated in November 2000, and is considered absolutely deprecated, including by Microsoft.

ASP.NET, as supported fully by Mono, is a completely different language. Yeah, the names are similar, but that's the only similarity.

Sun Microsystems used to have a paid product for running ASP on Linux and Solaris, but it was discontinued years ago.

---

