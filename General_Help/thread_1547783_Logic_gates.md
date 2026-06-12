---
title: "Logic gates"
date: 2010-08-07
forum: General Help
---

### Post by J V on 2010-08-07
I'd like to know what makes logic gates tick, but every time I look them up all I get are the icons they represent in a circuit...

I can guess some ways they would work myself but they all seem clumsy implementations, is there a wikipedia page describing this or something?

---

### Post by QLee on 2010-08-07
> **J V said:**
> I'd like to know what makes logic gates tick, but every time I look them up all I get are the icons they represent in a circuit...

I can guess some ways they would work myself but they all seem clumsy implementations, is there a wikipedia page describing this or something?

Well, yes there is a wikipedia page about the topic,
[http://en.wikipedia.org/wiki/Logic_gate](http://en.wikipedia.org/wiki/Logic_gate),
I don't know why you weren't able to find it.

However, your question is concerning basic electronics, it has nothing to do with Ubuntu, probably would have been better to ask in a different forum.

---

### Post by J V on 2010-08-07
Maybe I don't understand some of the diagrams but I can't see how the logic gates are built...

I understand how to use them what they do etc, but how are the logic gates *themselves* built, what makes them tick?

[http://en.wikipedia.org/wiki/NOT_gate](http://en.wikipedia.org/wiki/NOT_gate) - has a bunch of diagrams but I don't see how these could possibly work...

Is there any simplified guide somewhere?

---

### Post by jroa on 2010-08-07
I have a degree in electronics and I am in the process of working on a second one.  I can probably help you out with some diagrams, but I need to know if you understand how a basic transistor works first.

Edit:
You also would need to know how a basic diode and resistor work as well.  Knowing the basics of Boolean algebra would also help, but is not necessary.

---

### Post by J V on 2010-08-07
Boolean algerba: Yes
Resistor: Yes
Transistor: Possibly, must double check
Diode: Looking it up now

Edit: Ok, diode = one-way, transistor = basic switch, correct?

---

### Post by QLee on 2010-08-07
[QUOTE=J V]Maybe I don't understand some of the diagrams but I can't see how the logic gates are built...

I understand how to use them what they do etc, but how are the logic gates *themselves* built, what makes them tick? [/QUOTE]

It isn't something you can see, they are on the little bit of silicon wafer that is buried inside the chip.

It is possible to emulate the operation of them by using relays (as in the way the first "computers" were put together) but it is not a trivial matter to explain this to someone without a basic electronics course. When I learned it, we learned how a relay array could be replaced by the magic of a tiny chip but that was over 30 years ago, I don't know if they still teach that way. Your question sounds a bit like some of the homework we had to do then. If you figure out how to emulate the operation of a gate (which you state you understand) with mechanical relays, you should have a better understanding of what is happening.

---

### Post by jroa on 2010-08-07
Diode is like a check valve.  It allows current to flow in one direction only.

For our purposes, a transistor is like a switch that is controlled by an electric signal.  When a signal is present, the switch is on.  When a signal is not present, the switch is off.  Don't bother looking up a transistor at this point because the explanation you find will likely be way more complicated than it needs to be to understand a logic gate.

If this makes sense, I can draw a quick diagram to try to explain to you.

---

### Post by J V on 2010-08-07
Thanks jroa, I do/it does :)

---

### Post by jroa on 2010-08-07
Not Gate

Ok, first is the Not Gate.

There are four diagrams labeled A,B,C, and D.  In figure A, a resistor is connected to a voltage source which is labeled V+.  We will say that V+ is 5V and a high signal is also 5V.  Because one side of the resistor is connected high and the other side has no path to ground, both sides of the resistor will always be high and will always read 5V when a meter is connected to either side of the resistor.

Figure B is the same resistor, but this time the bottom of the resistor is connected to ground, which is a low signal or 0V.  Even though the top of the resistor is high, the bottom will always be low because of the connection to ground.

So, when the bottom of the resistor has a connection to ground, the output is low and when the bottom of the resistor does not have a connection to ground, the output is high.  Make sense so far?

Figure C shows a switch in between the ground and the resistor.  This was the closest symbol I could find for a switch, but it is not what would normally be used.  Anyway, when the switch is closed, the bottom of the resistor is connected to ground and the output is low.  When the switch is open, there is no connection to ground and the output is high.

Figure D is basically the same thing as C except that we are using a transistor to act like a switch.  When IN is high, the transistor closes or conducts to ground and therefore, the output is low.  When the IN is low, the transistor opens and there is no path to ground, so the output is high.

I hope this makes sense.  I will draw an OR gate next and it might take me a little while.

[IMG]http://i739.photobucket.com/albums/xx38/jorroa5990/Notgate.jpg[/IMG]

---

### Post by J V on 2010-08-07
So if "IN" is powered the resistor is grounded and OUT will not get any power, but if IN is off, then OUT will get power...

I thought it used the same current to pass through the resistor as to the transistor, this makes more sense as there is no timing implication... Cool, I learned something :) More knowledge please!

Edit: Suddenly the wikipedia diagrams are making much more sense, wait a minute, I'll be back if I don't understand something ;P

Ok, looking at the wikipedia NOT diagrams ( [http://en.wikipedia.org/wiki/Inverter_(logic_gate](http://en.wikipedia.org/wiki/Inverter_(logic_gate)) ) what is the difference between NMOS and PMOS? Wouldn't PMOS create a short-circuit if it inverted a zero current without extra measures? I don't see the benefit of this...

Also, the CMOS diagram seems like it's missing a diode between the inverted transistor and Q, otherwise wouldn't the current flow there as well?

---

### Post by jroa on 2010-08-07
OR Gate

I think you understand the basic idea for the Not Gate.  Try to think in terms of high and low instead of having power or not having power, because power is actually the rate at which energy is being used.  I know a lot of people use the word to mean that something is on, but you may confuse yourself when you actually start to learn about power.

Anyway, next is the OR Gate.  I only drew one diagram this time because I think you understand enough that I don't need to break it down into elemental pieces.

This time you have two IN terminals, but still only one out.  The INs are labeled A and B.  Notice that both are connected to diodes.  Remember that a diode only lets current flow in one direction.  When a positive source is on the flat side of the triangle, the diode is called "forward biased".  This is just a fancy way of saying the it is acting like a closed switch.  When a negative source is connected to the flat side of the triangle, the diode is "reverse biased", which is like an open switch.

When both of the diodes are reverse biased, the top of the resistor is be at the same voltage level as the bottom of the resistor and will read 0V if we placed a meter on it.  When either of the two diodes becomes forward biased by applying a high signal to either of the IN terminals, then the "switch closes" and the top of the resistor will read high, or 5V and therefore the OUT will also be high.

So, if A is high, OUT will be high.  If B is high, OUT will be high.  IF both A and B are high, OUT will be high.  And, if both A and B are low, then the OUT will be low.

[IMG]http://i739.photobucket.com/albums/xx38/jorroa5990/ORGate.jpg[/IMG]

---

### Post by jroa on 2010-08-07
> **J V said:**
> So if "IN" is powered the resistor is grounded and OUT will not get any power, but if IN is off, then OUT will get power...

I thought it used the same current to pass through the resistor as to the transistor, this makes more sense as there is no timing implication... Cool, I learned something :) More knowledge please!

Edit: Suddenly the wikipedia diagrams are making much more sense, wait a minute, I'll be back if I don't understand something ;P

Ok, looking at the wikipedia NOT diagrams ( [http://en.wikipedia.org/wiki/Inverter_(logic_gate]("http://en.wikipedia.org/wiki/Inverter_%28logic_gate")) ) what is the difference between NMOS and PMOS? Wouldn't PMOS create a short-circuit if it inverted a zero current without extra measures? I don't see the benefit of this...

Also, the CMOS diagram seems like it's missing a diode between the inverted transistor and Q, otherwise wouldn't the current flow there as well?

There are a lot of different types of transistors.  All of those that you listed are MOSFETS, or Metal Oxide Semicondutor Field Emitting Transistor.  I think that it will be much easier for you to understand the gates if you only focus on a basic NPN, which is what I drew in the Not Gate diagram, and PNP transistors.  With both of these, the center letter tells you what triggers the transistor.  With an NPN transistor, it uses a positive (P) trigger and closes negative (N) contacts.  The opposite is true of the PNP.

---

### Post by J V on 2010-08-07
The OR diagram seems similar to the NOT diagram in that it is earthed (Correct?) - Shouldn't this mean the output is low? Or that the output on NOT was always high?

Or does the positioning of the resistor have something to do with it?

I'll ignore the NOT diagrams on wikipedia for now but I'm sure to go there later...

---

### Post by jroa on 2010-08-07
And Gate

Next is the And Gate.  It will look very similar to the OR Gate.  However, notice that the diodes are reversed and the resistor is connected to V+ this time instead of ground.

If either of the two inputs are low, then the output will be low as well.  The only way for the output to be high is for both inputs to be high or, for this circuit, if both inputs are disconnected, the output will be high as well.

So, if A is low and B is low, OUT is low.  If A is high and B is low, OUT is low.  IF A is low and B is high, OUT is low.  And, if A is high and B is high, OUT will be high.

I am going to cook some breakfast.  I will post more later.

[IMG]http://i739.photobucket.com/albums/xx38/jorroa5990/AndGate-1.jpg[/IMG]

---

### Post by jroa on 2010-08-07
> **J V said:**
> The OR diagram seems similar to the NOT diagram in that it is earthed (Correct?) - Shouldn't this mean the output is low? Or that the output on NOT was always high?

Or does the positioning of the resistor have something to do with it?

I'll ignore the NOT diagrams on wikipedia for now but I'm sure to go there later...

The resistor is placed where it is because of its ability to cause a voltage drop.  When current flows through a resistor, one side of the resistor has a higher voltage level than the other.  When voltage is not flowing through the resistor, then both sides will have the same voltage level.

So, if you have a complete path for current to flow to ground through the resistor, then one side of the resistor will be high and the other side low.  When there is not a complete path, then both sides of the resistor will be either high or low, depending on how the resistor is connected.

In the OR diagram, when either of the inputs is high, current will flow through the resistor and the top of the resistor will be high.  When neither of the inputs are high, then both sides of the resistor will be the same level.  In this case, both sides will be low.

In the AND diagram, the diodes provide a path to ground.  If either one is low, then current will flow through the resistor and the side connected to V+ will be high and the side connected to the diodes will be low.  If neither diode provides a path to ground, then no current will flow through the resistor and both sides will be high.

---

### Post by J V on 2010-08-07
Ok, I understand the OR diagram (Parallel splits amps not voltage I presume?)

Your NOT diagram seems wrong: If A is true then the the ground AND the output will be high, if A is false then only the output is...

And the AND diagram, why are the diodes backwards? What does this affect? Shouldn't they instead use transistors? If there is any input the diodes will stop it, and either way out is high...

---

### Post by jroa on 2010-08-07
> **J V said:**
> The OR diagram seems similar to the NOT diagram in that it is earthed (Correct?) - Shouldn't this mean the output is low? Or that the output on NOT was always high?

Or does the positioning of the resistor have something to do with it?

I'll ignore the NOT diagrams on wikipedia for now but I'm sure to go there later...

Ok, I am done with breakfast.  This might help you to understand a little better.

In A, there is no complete circuit to ground.  The resistor is connected to V+ and is pulling the output up to 5V.

B is the same as A except there is a complete path to ground now and there is a voltage drop across the resistor of 5V.  The output is on the negative side of the resistor and now has a voltage of 0V.

In C, once again there is not a complete path to ground.  This time, the circuit is open going to V+.  The resistor is pulling the output down to 0V.

D is the same as C, except that there is now a complete path and so the output is now at 5V.

I hope this clears it up a little for you.  

[IMG]http://i739.photobucket.com/albums/xx38/jorroa5990/Outputexamples-1.jpg[/IMG]

---

### Post by jroa on 2010-08-07
> **J V said:**
> Ok, I understand the OR diagram (Parallel splits amps not voltage I presume?)

Your NOT diagram seems wrong: If A is true then the the ground AND the output will be high, if A is false then only the output is...

And the AND diagram, why are the diodes backwards? What does this affect? Shouldn't they instead use transistors? If there is any input the diodes will stop it, and either way out is high...

We could have used transistors for either the And or Or circuits.  I choose to use diodes because the circuit is much less complex.

In the Not diagrams, the ground will never be high.  Only the output changes state.  A only has an output, no input.  It will always be high.  There is no true or false levels for the A diagram.

With the And diagrams, the diodes are backwards because this time the inputs are supplying the ground path while the resistor is supplying the path to the voltage source.

Think of the output as just a voltmeter connection.  It will read either 5V or 0V, but is not actually part of the circuit.  In real circuits, this is not completely true, but I think it will help you to understand the basic gates.

---

### Post by J V on 2010-08-07
I meant the input, not A, sorry...

Even if "NOT D" output "Isn't part of the circuit" - shouldn't it be low due to the resistor before it?

With AND, how does this work? If Input A or Input B are powered all it does is stop the circuit rather than start it yes? Or is this a NAND circuit? I would see how it works as a NAND circuit...

---

### Post by jroa on 2010-08-07
> **J V said:**
> I meant the input, not A, sorry...

Even if "NOT D" output "Isn't part of the circuit" - shouldn't it be low due to the resistor before it?

With AND, how does this work? If Input A or Input B are powered all it does is stop the circuit rather than start it yes? Or is this a NAND circuit? I would see how it works as a NAND circuit...

For diagram D on the NOT Gate circuits I drew, it will be low when the transistor is on.  When it is on, it is like the B on post #17 and will have a low output.  When the transistor is off, it is like A in post #17 and output will be high.

The AND Gate is a little hard to understand.  Remember, there are two kinds of input signals, high and low (ground).  If both inputs are high, then the diodes are reverse biased (off) and do not conduct and the resistor pulls the output high.  If either of the outputs are low, then the corresponding diode will conduct and basically act like a switch that connects to ground.  The output is directly tied to this part of the circuit and will therefore become low too.  

I can draw an AND circuit with transistors instead of diodes.  This might help you to understand a little better.  I have to run to the store, but I will draw it as soon as I get back.

---

### Post by J V on 2010-08-07
So the diodes in the AND gate are grounded?

Speaking of the NOT gate, is the timing mechanism very complicated there? If it was instantaneous the transistor wouldn't be able to complete the circuit before the wrong result was passed on. Also, if the ground is not connected, doesn't it mean no current can flow at all? Wouldn't that mean there has to be an earth somewhere after the output?

---

### Post by jroa on 2010-08-07
> **J V said:**
> So the diodes in the AND gate are grounded?

Speaking of the NOT gate, is the timing mechanism very complicated there? If it was instantaneous the transistor wouldn't be able to complete the circuit before the wrong result was passed on. Also, if the ground is not connected, doesn't it mean no current can flow at all? Wouldn't that mean there has to be an earth somewhere after the output?

The diodes are connected to ground when the inputs are low and this provides a path for current to go to ground.  When the inputs are high, nothing is connected to ground in the not circuit D.  

Transistors are not instantaneous, but the are very, very fast.  Transistors can switch from high to low millions of times per second with out breaking a sweat.

For your question about when the ground is not connected, the output is a logical high or logical low.  There does not need to be any current flowing for the output to be high or low.  When something else is connected to the output, a small amount of current will flow, but even when nothing is connected, the output can still be high or low with out any current flowing through it.

---

### Post by J V on 2010-08-07
"When the inputs are high, nothing is connected to ground in the not circuit D.  "
Sorry, I don't quite follow, are we talking about the NOT gate diagram or the AND?

"Transistors can switch from high to low millions of times per second with out breaking a sweat."
Transistors may be fast but there has to be some form of timing in there to make sure the transistor hits before the next gate assumes it was passed a false, or do they work faster than the speed of electricity?

"When something else is connected to the output, a small amount of  current will flow, but even when nothing is connected, the output can  still be high or low with out any current flowing through it."
Only in theory right? It would only flow if something is connected (Like the output)

---

### Post by Zill on 2010-08-07
J V:  As a retired electronics engineer I am finding this thread of *some* interest.  Unfortunately, I must agree with the sentiments expressed by QLee in post #2 that this discussion really belongs in a different forum.

While Ubuntu, and software in general, does totally depend on electronic logic circuits, IMHO software discussions do not normally go to electronic component level.

If the OP does wish to know more about logic circuits then I strongly suggest signing up for an electronics course.

---

### Post by jroa on 2010-08-07
Zill, you may be right that this belongs in another forum.  I guess it depends on how the Mods define General Help.  If it is General Help for Ubuntu, then you are right, the discussion needs to be moved to a different forum.  If it is General Help for Technical Questions, then I think the original question is valid.  After all, we have threads where you just have to add to a number until the mod resets it to zero and threads where people talk about what they like to put on the cereal, so I don't see why this would be offensive to people or really even be deemed to be outside of a General Help board.  But, like I said, it is up to the Mods to decide. 

J V, I was talking about the AND Gate. Sorry, with all of these diagrams, I am getting myself mixed up. In the AND diagram that I posted, when the inputs on the AND Gate are high, nothing is connected to ground.  The high inputs basically turn off the diodes and the output is pulled high by the resistor.  When either of the inputs on the AND Gate are low, the corresponding diode is turned on and that input creates a path to ground, so the output is low.

The speed of the transistor really does not matter, usually.  If the output is low, the extra microsecond that it takes for it to switch to high is almost nothing.  There are circuits where that could pose a problem, but I have never dealt with one.

For the question about something being connected to the output, current will only flow through the output when something is connected to it that provides a complete path.  However, you do not need current to have a voltage.  Here in the US, a wall receptacle has 110V whether something is connected to it or not.  So, yes, the output can be either high or low, regardless of whether something else is connected to the output or not or whether or not current is flowing.

---

### Post by J V on 2010-08-08
Thanks jroa, I'll close this now and see how I do... I was always puzzled by the nature of electricity's flow...

---

