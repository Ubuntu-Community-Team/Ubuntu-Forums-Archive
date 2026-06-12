---
title: "Can I tell the type of memory I have in my machine without opening it up?"
date: 2010-05-12
forum: General Help
---

### Post by willz06jw on 2010-05-12
Hi and thanks for your help,

I need to buy some more RAM for my old PC.  I know there are Windows applications that can tell me the type of RAM I have installed.  I am running Ubuntu and I was wondering if there was an alternative that would tell me about the RAM I am using.

Any ideas?

Thanks again for the help,
Will

---

### Post by mike555 on 2010-05-12
you could go to ;    [http://www.4allmemory.com/index.cfm?pid=55&kwd=memory%20ram](http://www.4allmemory.com/index.cfm?pid=55&kwd=memory%20ram)   and put in info ...

---

### Post by john newbuntu on 2010-05-12
Open up a terminal(apps->acc->terminal) and Try:
sudo lshw -html > spec.htm
view the spec.htm file on your browser.  Try "man lshw" for other options.

---

### Post by r m h on 2010-05-12
Certainly, but you need to have a good idea of what you are currently using as a computer.

(1) [www.4allmemory.com](www.4allmemory.com)
(2) [www.upgradememory.com](www.upgradememory.com)
(3) [www.memory.com](www.memory.com)
(4) - (99) many other vendor sites
(100) STFI for your mainboard tech specs
(101) Open the computer case and pull one of your existing DIMMs, cross-reference with an internet search

---

### Post by r m h on 2010-05-12
> **john newbuntu said:**
> Open up a terminal(apps->acc->terminal) and Try:
sudo lshw -html > spec.htm
view the spec.htm file on your browser.  Try "man lshw" for other options.

Uhhhm, if the gentelman/lady is asking the OP question, I don't think something like a typical lshw output:
```
     *-memory
          description: System Memory
          physical id: 39
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:2
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:3
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:4
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber04
             vendor: Manufacturer04
             physical id: 4
             serial: SerNum04
             slot: DIMM4
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:5
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber05
             vendor: Manufacturer05
             physical id: 5
             serial: SerNum05
             slot: DIMM5
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)

```
would really be useful to tell the type of memory in his/her machine.

...just saying...

---

### Post by cascade9 on 2010-05-13
Yes, lshw wont tell you what type of memory is fitted.I dont know of any linux tools that will (if somebody else does, please post it! :) )

Probably the easiest way to find what memory is in your machine is to check your BIOS ;)

---

### Post by dandnsmith on 2010-05-13
I'm afraid that I've never seen a BIOS display that will show type of RAM installed. The best you can expect is quantity - you may not even get operating speed for the RAM or the number of slots and listing of empty/full.

I'd still have to go with knowing the manufacturer/model of the hardware (PC or motherboard), or using a Windows tool (my favourite is CPU-Z).

---

### Post by Rubi1200 on 2010-05-13
If I am not mistaken the following commands in the terminal should bring you further:

hwinfo

lspci

you may need to run them as root i.e.

sudo lspci

Hope this helps.

---

### Post by bumanie on 2010-05-13
If I do sudo lshw it shows DDR2 533 MHz (1.9ns) as below

bank:0
             description: SODIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 0x4D342037305432383634515A332D43453620
             vendor: 0xCE00000000000000
             physical id: 0
             serial: 0x836B6735
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)

Maybe try lshw as root - it has lots more details than lshw without root privileges.

---

### Post by cascade9 on 2010-05-13
> **dandnsmith said:**
> I'm afraid that I've never seen a BIOS display that will show type of RAM installed. The best you can expect is quantity - you may not even get operating speed for the RAM or the number of slots and listing of empty/full.

I'd still have to go with knowing the manufacturer/model of the hardware (PC or motherboard), or using a Windows tool (my favourite is CPU-Z).

I've seen BIOSes that show the RAM type, eg- 

[IMG]http://images.anandtech.com/reviews/motherboards/2008/asus-rampage-formula/BIOS_extreme_tweaker.jpg[/IMG]

That wasnt what I meant though, I meant that its easier to just get the manufacturer/model from the BIOS bootscreen, then go from there.

To be honest, for me its a lot easier to just peel the side of the case and check with eyballs than to bother with software. Not everybody is happy to do that though. 

> **bumanie said:**
> If I do sudo lshw it shows DDR2 533 MHz (1.9ns) as below

bank:0
             description: SODIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 0x4D342037305432383634515A332D43453620
             vendor: 0xCE00000000000000
             physical id: 0
             serial: 0x836B6735
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)

Maybe try lshw as root - it has lots more details than lshw without root privileges.

I'd run lshw and seen the warning msg "this program should be run as superuser" but never bothered actually doing it. 

Heh, thanks ;)

---

### Post by willz06jw on 2010-05-18
Great.  sudo lshw worked perfectly for me.  

Thanks again,
Will
:popcorn:

---

