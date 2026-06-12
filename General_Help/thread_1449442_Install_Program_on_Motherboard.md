---
title: "Install Program on Motherboard"
date: 2010-04-07
forum: General Help
---

### Post by fiveironfrnzy08 on 2010-04-07
Hello everyone!

I have a question, but first...

Some background:
There is a piece of software called LoJack that is a theft security program for laptops. When a laptop is stolen, it is marked as such with the company, and then if that laptop goes online after it is marked stolen, the company gets an ip address from it and tracks it down from there. The software is installed on the motherboard though, not the hard drive. This is so that the thief can erase the hard drive, but the laptop will still have LoJack installed anyway.

My question:
How does one go about installing a program on a motherboard? Would it be possible to create a batch file or program to install on my own motherboard?

Thanks!

---

### Post by foxmulder881 on 2010-04-07
I can't see how that is technically possible.

---

### Post by 2hot6ft2 on 2010-04-07
I think they mean it's done in the BIOS.
Might take a look at [http://preyproject.com/](http://preyproject.com/)
Similar except it's on the hard drive and it's free.
I have it setup in windows and no password for windows, that way if it gets stolen they will be looking around in windows (there's nothing there really) while I get their pics. and IP information.
They can't get in my encrypted storage partition (truecrypt) and most don't know how to get into ubuntu (being windows users).

---

### Post by bigsmitty64 on 2010-04-07
[http://www.absolute.com/products/lojackforlaptops/technology](http://www.absolute.com/products/lojackforlaptops/technology)

---

### Post by 2hot6ft2 on 2010-04-07
> **bigsmitty64 said:**
> [http://www.absolute.com/products/lojackforlaptops/technology](http://www.absolute.com/products/lojackforlaptops/technology)
Like I said in the BIOS
> Software is the Computrace Agent, **a small software client that is embedded into the BIOS** firmware of most computers at the factory.  Or you can easily install yourself.

---

### Post by 2hot6ft2 on 2010-04-07
> **fiveironfrnzy08 said:**
> 
My question:
How does one go about installing a program on a motherboard? Would it be possible to create a batch file or program to install on my own motherboard?

Since it's in the BIOS you would have to flash the BIOS which can brick (break, as in turn it into a brick) your computer. All they would have to do is flash the BIOS right over it.

---

### Post by SoFl W on 2010-04-07
Post removed by author
[COLOR=PaleTurquoise][/COLOR]

---

### Post by foxmulder881 on 2010-04-07
Flashing the bios with an unofficial security feature... doesn't sound like something I'd like to attempt. I think I'd take my chances on the laptop being flogged.

---

### Post by fiveironfrnzy08 on 2010-04-07
Thanks everyone for your responses!

@2hot6ft2 - Interesting program, Prey, I'll keep that in mind. I'm really not too familiar with flashing the bios or what that does/means. Any insight for me?

@SoFl W - That sounds interesting, what more can you tell me about how to set something like that up? I'm interested in writing my own program and installing in the bios. I have a server running at my house, how would I configure that to be contacted?

---

### Post by 2hot6ft2 on 2010-04-07
> **fiveironfrnzy08 said:**
> Thanks everyone for your responses!

@2hot6ft2 - Interesting program, Prey, I'll keep that in mind. I'm really not too familiar with flashing the bios or what that does/means. Any insight for me?

When your computer first starts and you see the manufacturers logo you can click on a key (which varies by manufacturer) to enter the BIOS. It's displayed at the bottom of the screen and could be the Esc, F8, F10 or another key.
This will explain it better than I can [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
But without it your computer will cease to function at all.

Yes, I know some have had one run without a BIOS to prove it could be done, but that's beyond the scope of this thread and I'm not going to go there. So if some of you can't resist then go for it....:P

EDIT: Flashing the BIOS overwrites it kind of like installing a new OS over an existing one. But it must be the right BIOS for the hardware configuration.

---

### Post by -humanaut- on 2010-04-07
If it's installed in the bios couldn't you just Jump it and reset it?

---

