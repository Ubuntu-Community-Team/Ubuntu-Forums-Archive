---
title: "On making browser-based games. What language/program would you recommend?"
date: 2009-06-29
forum: General Help
---

### Post by anthony62490 on 2009-06-29
Maybe this is not the right forum for this question, but you guys are just so darn helpful...

I think I've got it narrowed down to either Javascript or Flash. I'd really prefer not to pay $700 for Flash CS4, but if that's what it takes...

I am looking for the means to create a few simple games that can be embedded into a webpage. I would be learning the language from scratch, since I know nothing about website programming (with the exception of some HTML formatting knowledge), so a language that can be learned fairly quickly would be nice (though challenges are always fun). If you've got any suggestions, I'd like to hear them. Also, a reason as to why you would choose this particular method would be appreciated.

Linux compatibility is not required. If worst comes to worst, I'll just make a Windows Virtual Machine.

---

### Post by anthony62490 on 2009-06-29
bump

---

### Post by Tyke91 on 2009-06-29
Java definitely


Making games in flash with action script is a pain

---

### Post by anthony62490 on 2009-06-30
Java, huh? It's supposed to be similar to C++, so I guess I could be learning two languages at once.

---

### Post by Mighty_Joe on 2009-06-30
> **anthony62490 said:**
> Java, huh? It's supposed to be similar to C++, so I guess I could be learning two languages at once.

As someone who's used both, Java is very different from C++.  Off the top of my head:  
C++ has multiple inheritance.  Java doesn't.
C++ has operator overriding.  Java doesn't.
C++ has direct memory access (pointers, malloc/free).  Java doesn't.
C++ compiles to native code and runs directly on the processor, Java compiles to a byte code and runs in a virtual machine
This doesn't mean one is better than the other (use the right tool for the job!), they're just different.
I've seen a lot more Flash browser games than Java. That said, [here is a forum]("http://www.coderanch.com/forums/f-81/Game-Development") for developing Java Games (I'm a moderator over there, nice folks).

---

### Post by Coding Monkey on 2009-06-30
I'll second the Java suggestion.  You'll want to have a look at applets.
[http://java.sun.com/applets/]("http://java.sun.com/applets/")

The only (slight) drawback is that end users will need to have Java installed in order to play your games.  That shouldn't be much of a problem though, as Java is quite common nowadays.  On the upside, your games should be platform-indepent if you use Java.

---

### Post by bobince on 2009-06-30
Flash is the 'normal' way to build browser games. If you want to take part in the browser game aggregation and sponsorship networks, it will have to be Flash format.

(This doesn't necessarily mean spending hundreds of bucks. As well as various old-version/second-hand/student-edition possibilities there is also the free Flex compiler. Naturally if you take this route you will have to use some other tool to create the graphical assets, but then I don't much like Flash's graphics editing anyway.)

Java applets are an alternative but with much lower mainstream acceptance. Java is a stricter programming environment than JavaScript/ActionScript, which makes it slower and less flexible in getting things done, but more reliable in catching coding errors. (JS is particularly bad in this respect; it goes out of its way to sweep errors under the carpet, resulting in subtle and hard-to-debug misbehaviour.)

Straight in-browser JavaScript can be very effective for lightweight games, but its graphical capabilities are limited to what you can provide by moving <img>s around. Solutions coupling JS with canvas, SVG and/or MS VML are possible, but likely to be a lot of work to get going cross-browser, and not currently widespread.

---

### Post by anthony62490 on 2009-07-07
Well, it looks like I'll be going with Java then. The games I want to make should stay pretty simple. Thank you all very much.

---

