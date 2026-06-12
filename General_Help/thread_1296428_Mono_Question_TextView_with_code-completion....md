---
title: "Mono Question: TextView with code-completion..."
date: 2009-10-20
forum: General Help
---

### Post by mikep_bluefish on 2009-10-20
Hi everyone :mrgreen:

I've been working MonoDevelop for a few months now but I still consider my self a newbie when it comes to the Mono framework.

[B]I need to create a text editor that will provide code-completion for C#.
Something like MonoDevelop's source view..

I can't seem to find though how this can be achieved.. :confused:

If anyone can give me a few pointers (tips, links, forums...) that might give me some sort of a head start, I would really appreciate it[/B] [-o<

I know I'm asking this in the wrong forum but I don't seem to find any info except the official Mono website. 8-[

Plus, I made a post on the [www.go-mono.com/forums](www.go-mono.com/forums) but I got a response that my request must pass through approval, :-s so I guess it might take a while before I get an answer from there.. :sad:

---

### Post by directhex on 2009-10-20
Code completion is a pretty heavyweight task, requiring an advanced engine capable of analysing context (in order to determine the correct way to complete what you're doing, in context, rather than at random)

You could start off with using GTKSourceView rather than TextView, and overriding the changed event to make things happen whenever people do stuff to it?

---

