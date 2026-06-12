---
title: "how does code get converted to actual electrical signals"
date: 2010-04-30
forum: General Help
---

### Post by cybo on 2010-04-30
i post this question in this forum because i simply don't know where else i can post it.

my question is stated in the topic. when anyone writes code, (s)he basically writes text. after compilation is finished an executable is generated (at least in most cases). as far as i understand this executable is also basically text, which only a given machine can read. machine is just a collection of circuits organized in a very specific way. circuits operate with electrical signals. so the questions is how does text (code) becomes electrical signals? how is machine able to operate on electrical signals by reading text? how is this gap from text to electrical signals is bridged?

any help is appreciated.

---

### Post by dandnsmith on 2010-04-30
You're asking for a tutorial course in computers and computing.

Both code and text are represented by a set of 1's and 0's - there is no difference except in the way they are derived. Early computers, with very little memory for code and text, used sometimes to interpret the text as code (I knew a very successful set of programs which used some of the code as data).

I cannot think of a quick way to show how the stored code is turned into actions - this is quite an involved process.

I suggest some reading in Wikipedia might offer some help

---

### Post by cybo on 2010-04-30
dandnsmith,
what would be a good place to start?

---

### Post by Duckter on 2010-04-30
This is one of those questions where you have to take a lot of it as blind faith initially until you get your head around it. It is quite a huge amount of information to convey over a forum.

The simplest answer I can give is this (and then provide some links to expand on that).

The code, when it is in the machine has a physical state of 0's and 1's [it might be on the hard drive, memory, cpu but it is there in a physical form at some level of abstraction (<- keyword)]

The hardware at it's simplest level is a bunch of logic gates. They are organised in such a way to produce instructions and operations such as add, subtract, load, etc.

Your simplest form of code is binary. Which essentially is kinda like the raw states of the gates and context information. Code for one machine will only (generally speaking) work on identical hardware because they have to be able to understand what they are reading and processing. This is why you tend to have other layers of abstraction such as assembly. 

A higher level of representation is C/C++, and higher still is Java, even HTML and so forth. They all have to be converted down to a level the hardware can understand (infact it doesnt even have to understand it - but that's neither here nor there) and push out the correct state changes per clock cycle (yep it is all synchronised by clock cycles)

Simplest way to think about it for me is...
Hardware = stuff, the things you have to run code on
Code = context to give to the hardware
[Neither really make much sense without the other]

Some good places for further info (might be a bit heavy, but thats what you get :P)
[http://en.wikipedia.org/wiki/MIPS_architecture](http://en.wikipedia.org/wiki/MIPS_architecture)
[http://en.wikipedia.org/wiki/Von_Neumann_architecture](http://en.wikipedia.org/wiki/Von_Neumann_architecture)

The actual links may not be what you are looking for but if you root around there is definitely links worth following.

[im bound to have made a few over generalizations here so corrections are welcome]

---

### Post by quadproc on 2010-04-30
> **cybo said:**
> 
...
my question is stated in the topic. when anyone writes code, (s)he basically writes text. after compilation is finished an executable is generated (at least in most cases). as far as i understand this executable is also basically text, which only a given machine can read. machine is just a collection of circuits organized in a very specific way. circuits operate with electrical signals. so the questions is how does text (code) becomes electrical signals? how is machine able to operate on electrical signals by reading text? how is this gap from text to electrical signals is bridged?
...
That is quite a question.  Let me see if I can supply a few ideas that might help to explain what happens.

Most digital electronics uses binary levels to represent two different states on any given point (such as a wire or a pin) in the system.  These levels are often called "high" or "low", 1 or 0, "true" or "false", etc.  To relate this to the usual technologies used in computers, a low is usually less than about 0.5 volts while a high is greater than about 2.4 volts.  Signals are not allowed to stay in the region between those two voltages; they are only allowed there temporarily when they are changing.  The exact voltage at any given point is not important; the voltage just has to be in the correct range for its state.  That is, voltages ranging from 0 to 0.5 are fine for a low and voltages ranging from 2.4 to 5.0 are fine for a high.

A disk drive can store information such as source code for a program.  That information is stored as magnetized regions on the disk's surface.  As the disk surface rotates underneath a _magnetic head_, the head intercepts the magnetic field and changes that magnetic field into a voltage (just like a generator does).  (From physics we know that V = mu_zero V cross B where V is voltage, mu_zero is a property of space, V is velocity, and B is magnetic field.)  That voltage is quite small so an amplifier increases its amplitude so that the signal is large enough to be recognized as levels which are either high or low.  Then the voltages can be used to drive the logic inside the computer.  I think that this paragraph answers your question but a little more explanation may help, so that follows.

You might be asking, "how did those disk regions get magnetized?"  Using the same magnetic head, a strong current is forced into the head.  This causes a strong magnetic field to be generated by the head, and that field causes the magnetic coating on the disk surface to become magnetized in the region where the head is located.

Generally, computers are organized to deal with data as bytes.  A byte is 8 bits worth of data so it contains eight independent levels.  Those levels can exist side-by-side simultaneously (parallel), or they can exist one-by-one on a single point (serial) with each level occurring at a slightly later time than the preceding level.  Obviously, timing is crucial with serial signals.  Disk drives use serial data transfer.

Mostly, the source code that a compiler uses will be composed of ASCII characters.  ASCII is an acronym for American Standard Code for Information Interchange.  It specifies that each character is represented by a certain combination of highs and lows in its byte.  So, for example, the character _A_ has a binary representation of 01000001 which can also be represented as hex 41.  The character _B_ is represented by 01000010 (hex 42).  The character _a_ is represented by 01100001 (hex 61).  Each character has a unique representation.

ASCII is not the only encoding of characters in use today.  Others that come to mind are EBCDIC, UTF-8, and unicode.  But those work in the same fashion, they just use different numbers of bits and different encodings between the characters and the associated bit patterns.

All of this explanation is representative of the early implementations of semiconductor computer technology.  As time has passed, designers have figured out ways to improve performance and to reduce costs.  Some of the techniques are quite ingenious and they often involve a considerable encoding of the data.  That encoding is not seen by the user; the electronics hides all of the details from the user.

If any of this needs more explanation then please ask.

quadproc

---

### Post by sgage on 2010-04-30
Wow! What a question! As someone who learned about computers from the bare metal up, I would say, if you are really interested in this you should learn about the various logic circuits, and the meaning of words like "register", "accumulator", etc.. Way back in the day, Osborne Books had a great series. Talking late-70's, early-80's.

I cut my teeth programming 6502 and 8080/Z80 processors to effect an IEE-488 bus handshake on a 6820 PIO, and that's where the "rubber meets the road". Also converting serial to parallel and such.

Put this bit in that register of that chip (this is a command straight to the processor), crank it over, etc. Fill 'er up with 8 bits, and then you've got a byte. Then you tell the bus "here comes a byte for x, yo, x, are you ready for a byte?" The addressed entity says "I'm ready". You say "here it comes". "Did you get it?" "Yes I got it". "Good, here comes another one".

This entire conversation occurs in voltage levels on a set of lines.

It's really interesting down at that level. I used to be able to understand and visualize the entire path from a keypress to a character appearing on the display down to the registers, but that was a long, long time ago (CP/M and DOS).

Now there are so many levels of abstraction that it's mind boggling, but the principles are all the same in the end.

We forget what's at the bottom of it sometimes. I still think of GUI's as a newfangled layer of abstraction. But then, I'm getting old.

Holy crap! I press an "A" on my keyboard, and sure enough, there's an "A", right there in this text window! :P

---

### Post by conradin on 2010-04-30
Its easier to grasp where electrical signals turn to code. But Im a hardware guy. Im not sure how in depth your electrical training is. If you know about building logic gates and making circuits do things like not, &, or, compare, XOR NOR ect, then what you are essentially doing is programing with hardware. 

If you grap that easily, add another level of complexity. Storage, shifting bits, clocks, memory, ect. There are such things as devices used to program other hardware although that is somewhat dated. Punch hole card systems from the 70s used mechanical mechanisms to program (input/output) electrical codes. There is tons of history, on this subject, google it. The systems in use today aren't the only ways to do certain tasks. I'm noting that the binary operation 1= on 0= off isn't always true. Bell labs often used 0= on, and 1= off. many techniques in hardware programing are subjective to what technology was available at the time. IBM tried trinary and it never really took off from what I can see. 

I agree with Sgage, Indeed. Things like core memory, interwoven coils storing bits at each cross section. Understanding the history helps understand why things are done the way they are.

---

### Post by sgage on 2010-04-30
Yes, conradin, and understanding the layers. And the communication up and down the stack. 

Good stuff!

---

### Post by conradin on 2010-04-30
basically Code never stops being electrical signals. Even when bits are electromagnetically written to a hard drive, to be read later, there is still an electronic principle behind that. When a computer is off, you have no code.

---

### Post by dandnsmith on 2010-05-02
> **conradin said:**
> basically Code never stops being electrical signals. Even when bits are electromagnetically written to a hard drive, to be read later, there is still an electronic principle behind that. When a computer is off, you have no code.

That's an interesting idea - but doesn't fit with my model of the computing world. For me, Code is usually (these days) represented by a set of binary patterns (which can be interpreted by the Central Processing Unit, and cause a set of actions). Early computers stored this as cards or paper tape, in order to compensate for the lack of suitable storage (which came later as Hard Disks etc). 

We then have a progression from the initial representation (the written form) through a translation process to the executable form (punched cards, HDD, USB stick or whatever), and then to the actual execution which involves operations on data to get results (which is electrical, since the problems found with the mechanical computing engines proved insuperable).

The final stage is to turn the computation results back into a readable form.

---

