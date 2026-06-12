---
title: "virtual zeros and ones to real voltage levels"
date: 2010-12-22
forum: General Help
---

### Post by culkan82 on 2010-12-22
Hi guys.
I have a stupid question. :(
Where in the computer (which part of the computer) is responsible for converting zeros and ones (virtual - which is produced by software) to real voltage levels which are CPU understands?

I was looking for the answer and I have found that the driver for motherboard and some parts of kernel are responsible for it. But I still cannot understand how can something virtual produce something real?

Thanks in advance.

Branko

---

### Post by The Cog on 2010-12-22
That's actually quite a philosophical question. You might get quite a few conflicting answers on this. Personally, as both a hardware engineer and a programmer, I think I would say that no such conversion takes place. The hardware works purely on voltages / currents changing value. High/low voltage/current causes other bits of circuitry to switch on and off. These varying voltages and currents are all physical manifestations that can be measured with a meter or an oscilloscope etc. 

On the other hand, ones and zeros are conceptual things only. Along with letters and numbers, they are our interpretation of the physical state of the electronics. It's all a bit self-referential because computer hardware is designed to implement the logic concepts that we dream up, and then of course we can measure the hardware and can tell exactly what logical state the measured combination of voltages represents. But the correspondence between voltages and numbers is not natural, it is whatever we originally defined it to be.

For example, one could equally define a "high" voltage to be a one or a zero. The elctronics would be identical, but the same sequence of voltages switching may then have somewhat different logical meanings - a gate that only produces a high output when both inputs are high would be an OR gate rather than an AND gate. The numbers in CPU registers would have different meanings, and the CPU instructions would have different logical meanings even though the circuitry hadn't changed. Your computer you have in front of you now would behave identically because it's the same hardware, but the software and meanings would be subtly twisted, with loop counters counting up to 255 instead of counting down to 0 for instance. 

So really, the conversion from a voltage to a 0 or 1 is in your mind. To the computer, it's just voltages.

---

### Post by Slim Odds on 2010-12-22
Nice post TC

People really freak out when I try to explain to them that numbers do not actually exist in the physical world. But it's true.

---

### Post by culkan82 on 2010-12-23
Good explanations. You are absolutely right.  Ones and zeros are only our (human) representation of state of logic circuits (AND, OR, XOR, ...). Ones could have been 1.3V or 0.2V or something different. It entirely depends of technology which was used for making basic electronic components such as electronic transistors, diodes, resistors, capacitors and inductors.

But it was not my question. Maybe I was not clear enough. Probably because I am not good in English. Sorry guys.

I am going to try again. I will give you an example.
I am running Calculator (which is software). When I press 2 + 3 and then I hit button =, my Calculator says 5. So, when I have pressed button = something (which is not voltage/current) goes from Calculator through OS (Ubuntu in my case - my favorite :) ) to the CPU (which works only with voltage/current). CPU processing the date (in voltage/current form) and returns result to the OS/Calculator. Calculator gets result in form which is not voltage/current and shows me 5.

So, I am wondering who is responsible for converting something which is not voltage/current to the voltage/current in the computer?

The closest answer I have found here: [http://en.wikipedia.org/wiki/Hardware_abstraction_layer](http://en.wikipedia.org/wiki/Hardware_abstraction_layer)

Thanks.

---

### Post by tgalati4 on 2010-12-23
There are specialized chips in the motherboard that control voltage and monitor temperature.  You can search for your particular motherboard and find the chips then search the chips and find the documentation.

Typically, a binary value (ones and zeros) is written to a specific memory location and the voltage controller chip reads that value and sets the voltage accordingly.  Temperatures are monitored with thermisters (resisters that change with temperature) and those values are changed from analog (ohms) to digitial (temperature) with a look-up table and written in binary to another specific memory location.  The kernel module (lm-sensors) reads that value and decodes it to C or F so that your panel applets can read and display it.

It really is all magic.

---

### Post by The Cog on 2010-12-23
I just spent ages writing a really good post, basically expanding on my original post. I clicked preview and the **** forum then said I've timed out and must log in again - and lost my post. 

Basically, think of Babbages mechanical computer - it's just cogs pushing cogs - there are no numbers in the machine. A computer is just switches driving other switches - hundreds of millions of them. The whole OS and application is stored in the electronic switches and that influences the later behaviour of the machine when keyboard buttons make electrical changes. It's a very complex cascade of electronic signals triggering others. But it's voltages and electronics. The numbers are your interpretation of the voltage patterns and the resulting patterns of little lights on the screen.

P.S.
The appearance of being magic is all due to the almost incomprehensible complexity of the state of the electronics. "Sufficiently high technology..."

---

### Post by dcstar on 2010-12-24
> **culkan82 said:**
> 
.........
So, I am wondering who is responsible for converting something which is not voltage/current to the voltage/current in the computer?
.........

Anything that is called an "Interface".

A Keyboard is an Interface, as is a Mouse, Microphone, Telephone etc. etc. Other Interfaces convert things for subsequent Interfaces.

Spend 10 or 20 years learning about and using electronic hardware and you will get a better grasp of the whole concept.

---

### Post by TWK1a4 on 2010-12-24
As the The Cog and dcstar have touched on, a computer works only with voltages to represent what humans call ones and zeros.  It's a human concept to use ones and zeros to represent information, not an actual physical reality inside a computer.  The virtual part is YOU.  When you click a mouse, type on a keyboard, read information from a screen it is all form of 'electrical ones and zeros' (In a computer ~+5v and 0v).  Hitting a single character on a  key creates 8 bits (8 electrical 'ones' and 'zeros') that the CPU can understand.

     We could, for example, input data into a computer by using eight toggle switches to input each character, but we would spend hours typing a single message board post.  It's much easier for humans to use a keyboard, which you could consider as the 'converter' from 1/0's to voltages.  A better term would be interpreter.  The Keyboard 'interprets the hit of a key such as '3' as eight bits of '0000 0011' in ones and zeros.  When we press a key WE are converting the idea of virtual ones and zeros to voltages.  A computer monitor is a human-friendly way to read 'the ones and zeros' or voltages.  We could pull a Matrix and learn to interpret the signals that computers output in binary ones and zeros, but I don't think any human could look at an list of ones and zeros and decipher something like an Ubuntu logo or a graphical message board.

"Spend 10 or 20 years learning about and using electronic hardware and you will get a better grasp of the whole concept." - dcstar  I have spent 5 in the field and it still is only getting semi-clear...  It's an endless learning process.

I had a professor that liked to abstract the concept of ones and zeros with ridiculous examples.  He would say it's all the same no matter whether we use voltages, mechanical switches, ones/zeros, +5v/0v, True/False, Black/White, fat/skinny, old/young, Ford/Chevy.  We could have a box full of fat and skinny people computing our information!  I personally, always pictured a line of cars representing binary numbers...  Damn engineering, it ruined my perfectly innocent mind.   

     -TWeaK

---

### Post by culkan82 on 2010-12-24
Thanks guys a lot.

Best Regards,
Branko

---

### Post by The Cog on 2010-12-25
> We could, for example, input data into a computer by using eight toggle switches to input each character
Been there, done that, on PDP-11 and Nova-3. Except they had 16 switches, not 8. After a few dozen locations, it really starts to feel like a chore. Makes you really appreciate what an advance a punched card reader is. Those were the days...

---

