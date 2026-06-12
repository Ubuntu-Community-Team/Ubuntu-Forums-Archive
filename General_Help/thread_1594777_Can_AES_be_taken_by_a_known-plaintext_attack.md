---
title: "Can AES be taken by a known-plaintext attack?"
date: 2010-10-12
forum: General Help
---

### Post by J V on 2010-10-12
Can AES be taken by a known plaintext attack? (Can you take a file, encrypt it, then get the key by reversing the encrypted file by the plaintext?)

---

### Post by Nostalos on 2010-10-12
I am no crypto analyst, but I would probably say "that depends".   But to my knowledge there are not any.   And I think even if there was, it would depend on how AES was implemented as well and for what purpose.  i.e.  CBC Mode is great for SSL streams, but tend to leak some info when using for disk encryption mode. At least that is my personal understanding.

---

### Post by J V on 2010-10-12
Well I meant in ecryptfs the home folder encryption in ubuntu: It uses block encryption, but what I really want to know is would it be possible to reverse the key...

I never bothered with the AES mathematics and I'm too lazy to do so now, but if it can be attacked within a reasonable time frame it could wreak havoc on ubuntu security...

---

### Post by Nostalos on 2010-10-12
In a reasonable time?  Unlikely.

---

### Post by J V on 2010-10-12
Well in theory at least all symmetrical key encryption should be reversible...

---

### Post by Nostalos on 2010-10-12
LOL.  Of course it's reversable ;)  if not it would be a hash

---

### Post by J V on 2010-10-12
But without the key I mean, if I know the cyphertext and the plaintext I should be able to mathematically deduce the key no?

---

### Post by Captain Giraffe on 2010-10-12
The plausability of this is discussed in
[http://en.wikipedia.org/wiki/EFF_DES_cracker](http://en.wikipedia.org/wiki/EFF_DES_cracker)  

also good luck with the plaintext.

---

### Post by J V on 2010-10-13
Giraffe: DES is not AES, and brute force is not a KPA...

---

### Post by Nostalos on 2010-10-13
Well, then lets look at it from another direction then.  Rijndael was adopted as AES (Advanced Encryption Standard) by the US Government and is approved by the NSA for top secret information. 

While still in the realm of possibility I suppose, not very likely.  If something as simple as you suggest where as easily done as you hope.  Rijndael would have been replaced as AES by now just as DES and 3DES have been.  Also due to IV and CBC,  you won't be able to just blatantly find the key to a specific piece of clear text as each block gets encrypted based on a hash from the block before it.  At best you will get part of key (still unlikely).   Shortest path is to brute force the key which relies on prime factorization. And is incredibly slow.  But anyway...

But if you have the CPU and brain cycles to burn on the attempt.  More power to you my friend and the best of luck.

---

### Post by J V on 2010-10-13
Oh... I thought it was possible and that was the norm... nvm then :)

---

### Post by rewolff on 2011-12-10
Old thread I know.... 
> **J V said:**
> But without the key I mean, if I know the cyphertext and the plaintext I should be able to mathematically deduce the key no?
Yes. Absolutely. Even if you don't know the exact plaintext, but just know that the plaintext is ascii: 

If we assume that the plaintext is an ascii file, and we have a cyphertext, decrypt it with key 00...0000, we get a bunch of gibberish, as about 60/256 of the characters are printable, we have a .023^16 chance of getting all ascii characters. Chances are we'll have a few nonprintable characters and we continue with the key 00.....0001 and so on. This is called brute-forcing. Every cypher has this "weakness". Every cypher attempts to make this impractical. 

Every time we get a decrypted text that might be just ascii, we can step to the next cypher-text and try to decrypt that. If that works, we have our key (with a very, very high probability), if it doesn't we were just lucky (or unlucky) and happened to stumble upon a freak key that just happened to result in all ascii characters. 

If the source is not plain ascii, things can get a little easier or more difficult to determine if you've found a hit. Things for example get easier if the encrypted file is say an executable or a gzip that has a "magic number" in the beginning. 

Now, this is all theoretical. There are at least 2^128 keys to try. That's rather a lot. 

Modern chips (affordable for consumers: I found one in an USB harddisk enclosure!) can encrypt about 16 million blocks per second (2^24). Let us assume (unrealistically) that someone would be able to do 1 million times better: 16 trillion encryptions per second (2^44). 

Then we would still need about 2^84 seconds (128-44). This comes to 600 thousand billion years. This should translate to "not in my lifetime, don't worry about it".... 

If we take into account "Moore's law", we'll be able to break 10 more bits every 20 years. So after about 8*20 years, we would be able to break AES-128, assuming a budget of millions in about 16 years.... Still "not in my lifetime". 

But AES comes in three variants, 128, 192 or 256 bits. It would be prudent to switch to using 256 bit keys sometime in the next century.

Now, some cryptographers have found attacks that might break AES in on the order of 2^100 operations. Even these are so impractical that they cannot show that it actually works because that would take more computer-time than all computers in the world combined running for the life of the universe....

---

### Post by haqking on 2011-12-10
[http://www.theregister.co.uk/2011/08/19/aes_crypto_attack/](http://www.theregister.co.uk/2011/08/19/aes_crypto_attack/)

---

### Post by Iowan on 2011-12-11
Thread closed.
From Code of Conduct:
> # If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

