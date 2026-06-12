---
title: "Time to brute force password"
date: 2010-06-28
forum: General Help
---

### Post by J V on 2010-06-28
Is there a formula for how long it takes to brute force a password?

Something like: "AES: 1000000 per Ghz per Second"

Perhaps AES: "20 cycles per attempt" (20/Ghz/Second = 53687091 per second)

Anything like that?

---

### Post by Bachstelze on 2010-06-28
No, "GHz" is irrelevant here. If you just try all the passwords, there is no computational work involved, so a 100 MHz processor should take roughly the same time as a 3 GHz one.

*EDIT:* Actually, what kind of "password" are you talking about? AES is a cipher, are you talking about keys?

---

### Post by dino99 on 2010-06-28
wrong place for hacking :mad:

---

### Post by MooPi on 2010-06-28
User password ? If so why? Easy enough to change if you have access to the machine.

---

### Post by MooPi on 2010-06-28
deleted

---

### Post by endotherm on 2010-06-28
keep in mind, bruteforcing is no longer the method of choice for breaking a cipher or password. usually attacking the password hash with dictionaries and  rainbow tables is the preferred methodology these days. 

I seem to recall l0phtcrack used to display the number of tries per second. my P3-600MHZ took the same 4 days to unhash my password as my p4-2.6GHZ HT. I have heard that the newer versions will use GPU though, which can provide a much bigger boost due to the number of threads it can run at once.

---

### Post by kalistona on 2010-06-28
there are not an answer but a rule :
it is safe as long as it is not ! it means that with a big computer and time ....

brute force is useless, because like you wrote [COLOR=Blue]AES[/COLOR] [it is unbreakable if 256 (very strong)] is a good example.
brute force is old (dictionnaries, etc...) and algorhytm is better : here is like you wrote.

see AES, wpa, wep break from algorhytm...someone says in one minut it is working from tables per cycle if  i remember well.

---

### Post by J V on 2010-06-28
@Bach: Seriously? I mean seriously? It's all computation... Elaborate?

@Dino: I know for a fact from what I've been told about 128-bit  passwords than mine won't be crackable until the singularity turns the  whole universe into a computer (Bit OTT for my password eh?) but I wanna  know what qualifies as a "Secure" password... 10 characters full  spectrum seems to last for average of 2 years (At least, in 2004) but  what's it like now?

@Endo/Kali: Rainbow tables, Dictionaries, and, I think, social  engineering won't work on my password :)

---

### Post by Bachstelze on 2010-06-28
meh

---

### Post by Bachstelze on 2010-06-28
> **J V said:**
> @Bach: Seriously? I mean seriously? It's all computation...


See edit. ;)

---

### Post by Bachstelze on 2010-06-28
> **J V said:**
> @Bach: Seriously? I mean seriously? It's all computation...


See edit. ;)

---

### Post by J V on 2010-06-28
Ah, I mean the key, how long per Ghz would it take to brute force a key...

@Ubuntuforums: Stoned?

---

### Post by endotherm on 2010-06-28
> **J V said:**
> @Bach: Seriously? I mean seriously? It's all computation...

@Dino: I know for a fact from what I've been told about 128-bit passwords than mine won't be crackable until the singularity turns the whole universe into a computer (Bit OTT for my password eh?) but I wanna know what qualifies as a "Secure" password... 10 characters full spectrum seems to last for average of 2 years (At least, in 2004) but what's it like now?
BF is not actually a calculation, but a procedure. I don't need to calculate that b comes after a and that c comes after b.

the place where the math comes in, is that the total number of combinitatinos for any given key is S^L where S is the number of chars in the solution set (10 for numeric, 26 for lowercase alpha, 52 for alpha, 62 for alphanumeric, and 72+ for the extended char set) and L is the length of the password. 
you are guaranteed to find the password in less operations than S^L.

---

### Post by J V on 2010-06-28
Well yes endo, but I'm wondering how fast a computer can make attempts... A supercomputer can get through 2^56 possibilities much faster than a home PC...

By taking the algorithm for how fast a computer can brute force, and applying it to a supercomputer, I can see what the smallest reasonably secure password is...

@Endo: It's a procedure, but it has to test the value (By encrypting the hash/decrypting the data) once per cycle of the procedures loop

@Kalistona: Whut? Yes we know it works faster by hardware not software... as for "Cycle" I was (In the beginning) referring to CPU cycles. There is no "Check" by default, but I want to know how fast it goes so I can see what is optimal

---

### Post by kalistona on 2010-06-28
i have answered : it does not work form this idea (irrelevant yet writen !)
bruteforce is not working like that, it is depending on your machine ( and the others softs/help) not on the soft.
with a big machine, 14 # -password -surely few hundred years...
bruteforce has not an automatic 'check' per second or per cycle like a car/miles...

---

### Post by Bachstelze on 2010-06-28
> **J V said:**
> Ah, I mean the key, how long per Ghz would it take to brute force a key...

Well, for starters, no one is going to fully brute force your AES, because cryptanalysis techniques exist that will at least eliminate some of the work.

For brute force, well, it's easy. You have to test all possible keys, that is, try to decrypt a block with every key, until you find one that makes sense. It's all a matter of probability, an attacker could get the right key on first try.

Complicating the matter further is the fact that AES works on 128-bit blocks. Obviously, what you want to encrypt is larger than 128 bits, so a method is used to divide the message into 128-bit blocks and encrypting them. Several methods exist, and all of them leak some information about the message. You need to find out which method is used in your case, and include that in your calculations.

Then there are differences in implementation. One program might use a different implementation of the AES algorithm, that will change the number of CPU cycles required to perform a decryption.

So no, there is no canned formula that will work in all cases.

---

### Post by J V on 2010-06-28
Really? I thought the file was stored whole and only decrypted in parts of 128 on-the-fly?

I know it's all about probability, but the average (By default being half the possibilities, 2^128/2) stays the same... So how long does it take a computer with *insert stats here* to reach the average?

If I were to build a Linux OS with customized kernel, etc, designed to use the minimum cycles to run AES to brute force the password, and then ran it on the largest supercomputer/cluster/botnet the NSA have going for them, how long would it take? :P

---

### Post by Bachstelze on 2010-06-28
> **J V said:**
> Really? I thought the file was stored whole and only decrypted in parts of 128 on-the-fly

Oh God, no. If you just divide your file into 128-bit block, encrypt all those blocks one by one with the same key, and then construct the encrypted file by concatenating all the encrypted blocks, you leak A LOT of information about the file. The whole file structure is retained, for example (and every file that is not random data has some kind of structure).

Each block is encrypted with a different key, that can is computed using the previous key, some random initial data (sometimes called an IV, for Initialization Vector), and sometimes the previous block.

Of couse, all the methods perform only one AES encryption or decryption per block, but they differ in how much information they leak about the message (no, there is no method that doesn't leak any information).

> I know it's all about probability, but the average (By default being half the possibilities, 2^128/2) stays the same... So how long does it take a computer with *insert stats here* to reach the average?

If I were to build a Linux OS with customized kernel, etc, designed to use the minimum cycles to run AES to brute force the password, and then ran it on the largest supercomputer/cluster/botnet the NSA have going for them, how long would it take? :P

As I said, it's not that simple. You need to know a lot about the machine in order to know exactly how many CPU cycles encryption or decryption of a single block will consume. And it is mostly irrelevant anyway, *no one is going to bruteforce your AES*.

---

### Post by Joe of loath on 2010-06-28
As said above, bruteforce is irrelevant. Dictionary and clever sh*t are the preferred methods now. Just look at WEP, if you were to BF it it would take years, but you can do it in seconds on a pentium 2 if you capture enough packets, due to some very clever logic.

---

### Post by J V on 2010-06-28
"No one's going to need to perform thousands of calculations per second" - Inventor of the Computer
"No one's going to need to leave that many messages" - Inventor of the post-it
"No one's going to need to get to every file on the internet" - Inventor of Google

What a world it would be if it weren't for curiousity... Seriously, my passwords can't be cracked by anything but brute force, so whats the lowest length password I can use?

---

### Post by Bachstelze on 2010-06-28
> **J V said:**
> 
Seriously, my passwords can't be cracked by anything but brute force,

*sigh*

We told you precisely why they can, and why even if you assume brute force is used, there is no canned formula that gives the time it will take. Sorry for telling you the truth, and not what you wanted to hear.

---

### Post by J V on 2010-06-28
1: Salted, no rainbow tables
2: 94 character set random generated PW, no dictionary attack
3: If you are referring to an XSL attack, that was debunked in '07

But again, this has nothing to do with it... I'm just curious... Lets skip AES and say SHA-2... The default ubuntu login is SHA 256 with a salt... This would probably be the primary attack vector on a machine with a decent password (It's faster to run a hash than to decrypt a virtual partition yes?)

How long would it take to BF *that*?

---

### Post by Bachstelze on 2010-06-28
Exactly the same problem: two different CPUs with two different instruction sets can take a different number of clock cycles to compute one SHA-256 hash, so one will be faster than the other at the same frequency. Frequency is not the only parameter to take into account, you must also consider the implementation and the hardware it runs on.

---

### Post by J V on 2010-06-28
So depending on the CPU, even if it has the same clock speed, architecture, and operating system will run hashes at different speeds? Don't suppose theres an average or a range?

---

### Post by Bachstelze on 2010-06-28
> **J V said:**
> So depending on the CPU, even if it has the same clock speed, architecture, and operating system will run hashes at different speeds? Don't suppose theres an average or a range?

I said "with different instruction sets", the same CPU model running the same program should take roughly the same time, I don't think the OS matters much here.

So then, if you want to find out, you have two options: if you have access to a machine with the CPU you want to test, compile the program, run one computation, and find out how mny CPU cycles it took (I *think* valgrind can do that, ask in Programming Talk if you're interested). Otherwise, you have to use Google and find out if someone has data on it, the formula is:

t = n*2^128/f

where t is the time taken in seconds, n is the number of CPU cycles for one computation, and f is the frequency of your CPU. Of course replace 2^128 with whatever the number of combinations to be tried is. This won't be exact, since it assumes ALL CPU cycles are used for the computation, which is of course never the case, but it's probably the best you can get.

---

### Post by J V on 2010-06-28
Thanks... I'll just google for some speed results...

---

