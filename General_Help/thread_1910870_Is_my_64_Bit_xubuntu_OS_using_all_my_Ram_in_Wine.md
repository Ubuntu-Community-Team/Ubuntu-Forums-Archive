---
title: "Is my 64 Bit xubuntu OS using all my Ram in Wine?"
date: 2012-01-17
forum: General Help
---

### Post by Adrianogee on 2012-01-17
32 Bit OS's are maxed out at 3gigs.. If I have 6 gigs of Ram on my 64 Bit OS..
Is my ram being used?

I am running a 32 Bit Starcraft 2 in wine, on a 64 Bit OS. I tried using PlayOnLinux and 
reinstalled 64 bit SC2 64...It ran 20 frames slower, with a lot of sound issues..
 Should I keep trying different 64 bit wine versions?

I figured 64 bit would be better, because I have more than 3 gigs of Ram..
If my ram is being utilized I will keep using 32 bit wine.. Be kind I am a Noob..

XUBUNTU 11.10

---

### Post by Vaphell on 2012-01-17
go with the 32bit version of sc2. Most windows programs in existence are 32bit and that's what's wine guys concentrated on. I'd guess that 64bit paths are untested, bugged and unoptimized.
Besides your 64bit system uses all your ram, your SC2 may be limited to 3G or whatever but i doubt it requires that much. Remember that an awful lot of people have 32 bit windows and leaving them in the cold would be very unwise.
You can always check how much memory SC2 eats in windows and see if it's close to 32-bit related limits or not.

[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)
> 2.4. Does Wine run on 64-bit?

Yes. Normally, installation should be the same as with 32-bit: simply install the Wine package for your distribution. Check the Downloads page. If you need to build Wine from source, see WineOn64bit.

Note that Wine for 64-bit actually runs in 32-bit mode. This is necessary, as virtually all Windows applications are 32-bit. **Support for 64-bit Windows applications is currently experimental (see Wine64)**.

    Wine is currently offered in 32-bit. 16-bit and 32-bit Windows applications work with it. It runs on both 32-bit and 64-bit Linux/Unix installations.
    Wine is also experimentally offered in 64-bit. 32-bit and 64-bit Windows applications (should) work with it. It runs only on 64-bit Linux installations. 

---

### Post by Adrianogee on 2012-01-17
Thanks for the advice. I am going to stay with 32 bit.
Even if I had it running right, it runs slower,..

Maybe I will revisit the 64 bit version later when they
support it more. I read that link, and Googled my question,
before I posted it.. No one is for sure it its locked at 3 gigs...

I got some free Duo Cores at work and I was testing different
set ups.. Some of them have 6 gigs, most only 4..

I am happy with my 64 bit OS's running 32 Bit wine, just was
wondering about the Ram..

---

### Post by Adrianogee on 2012-01-19
I just tried Wine 64 Version 1.3.37. Frame rate, sound and playability are awesome.
I guess its only a matter of time before they perfect 64 bit Wine...

---

