---
title: "requirementz"
date: 2006-02-07
forum: General Help
---

### Post by mattyboi88 on 2006-02-07
Guyz, how do u fink ubuntu 5.10 wud perform on a dell pwr edge 2200 wif x2 PII 333mhz processa'z n 256ram.

thx guyz

---

### Post by byen on 2006-02-07
with that processor speed... I would suggest using Ubuntu with  XFCE, Fluxbox or ICewm instead of Gnome or Kde desktop. Also... you might want to look into lighter distributions such as Damn small linux or puppy linux...
goodluck!

---

### Post by madmetal on 2006-02-07
256 memory is fine but the cpu is weak so try XFCE with ubuntu.
also have a look at ubuntulite.

---

### Post by az on 2006-02-07
It will be slow, but it will work fine.

Do you mean two 333mhz processors?  You will install with the 386 kernel, but you should install the linux-686-smp package after that to get a kernel that is optimised for pentium and will run both processors.

It should run pretty well with that.

You talk funny.

---

### Post by mattyboi88 on 2006-02-07
Yeh, It'z got two processa'z in her... what's a 386 and 686 kernel; computers are not my specialty... also, what is xfce ubuntu... sorry guyz..

btw, the reason i type funny iz coz i lyk typing lyk it, it lookz hot :p I can type quite well using the full mechanics of english... :D

---

### Post by Protex on 2006-02-07
Well as per your question regarding Xfce ubuntu.

It's basically a version of Ubuntu that runs a lighter desktop enviroment. You can get it by doing a 'server' install of Ubuntu, and then running "apt-get install xubuntu-desktop".

As per the kernel question, I'm sure someone will be able to answer better than I, but the 386, 686, k7 etc, are PC architectures. K7 is native to the AMD K7 Processor and so on and so forth. As for SMP, that is a kernel that will allow Linux to use both the processors in your machine.

---

### Post by seakiwi on 2006-02-07
[QUOTE=mattyboi88]Yeh, It'z got two processa'z in her... what's a 386 and 686 kernel; computers are not my specialty... also, what is xfce ubuntu... sorry guyz..

*btw, the reason i type funny iz coz i lyk typing lyk it, it lookz hot :p I can type quite well using the full mechanics of english... :D*[/QUOTE]


You think so? I guess if you're aged about 10 it might look pretty neat but if you're looking for some serious help here, I suggest you switch back to the "full mechanics of English". The novelty of having to translate your "hot" little private language in order to help you, will soon wear off I suspect. 

Just a little bit of friendly advice - up to you whether you take it or not.

---

### Post by az on 2006-02-08
[QUOTE=seakiwi]You think so? I guess if you're aged about 10 it might look pretty neat but if you're looking for some serious help here, I suggest you switch back to the "full mechanics of English". The novelty of having to translate your "hot" little private language in order to help you, will soon wear off I suspect. 

Just a little bit of friendly advice - up to you whether you take it or not.[/QUOTE]


Pull your finger out and have a little fun.  I think the point was made.  Let's be nice!

As for the architechtures, for your processors (pentium) you will be happy running the 686-smp kernel.  Only one kernel is available on the install cd - the 386 one.  It runs on everything.  In your case, it will boot and install using only one of your processors.  To get a performance boost (like using special pentium functionality and the ability to use both processors) use the 686-smp kernel.

---

