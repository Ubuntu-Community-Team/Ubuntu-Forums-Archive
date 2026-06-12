---
title: "Intel HD 3000 Minecraft lag spikes every second?"
date: 2011-08-17
forum: General Help
---

### Post by kyconny on 2011-08-17
I wasn't sure weather to post here or on the minecraft forums.

OS: Ubuntu 11.04 x86
CPU: Intel core i5 sandy bridge 2410M
GPU: Intel HD 3000 (Integrated)
RAM: 8 gigs ddr3

So I got my new laptop a few days ago,
loaded up ubuntu.

After starting up minecraft to connect to my server I realised that the fps was going from 50 to 1 and back to 50 again **EVERY SECOND** so obviously this isn't normal.
After a quick google search every one on windows seems to have no problem. There are no results for linux.

So could anyone please help me? If you do I will give you up to the value of 100 minecraft diamonds in cookies :)

Edit: Yes I know why the **** are you using a x86 os on a computer with 8 gigs of ram? At the time of installation all I had was no internet access and a live cd from LUD with ubuntu on it

---

### Post by kyconny on 2011-08-17
bump

---

### Post by akand074 on 2011-08-17
> **kyconny said:**
> Edit: Yes I know why the **** are you using a x86 os on a computer with 8 gigs of ram? At the time of installation all I had was no internet access and a live cd from LUD with ubuntu on it

I don't know the answer as I've never played the game, and hardly to never really play PC games. But I am so distraught by the fact that you are running a 32 bit version of Ubuntu on a sandy bridge CPU and 8GB of RAM that I am at a loss for words. Do you have internet connection now. Please download, burn, and install the 64 bit version. Perhaps your problems will all be solved then? :D

Though do you have your proprietary drivers installed? I'm not sure how good the Intel HD cards' linux support is. And there is also sandy bridge issues I hear, those could be related. Is your desktop effects on? I've heard of issues with gaming going away after turning them off.

---

### Post by kyconny on 2011-08-18
visual effects - on
hmm maybe your right.
BUT I have lost my flash drive -.-
Downloading 64 bit iso now anywayz
I just kept the 32 bit seen as I didn't really need more than 2.5 gigs of RAM Will update if it fixes

---

### Post by kyconny on 2011-09-06
Not to bring up a old thread or anything but... Still getting the problem :(. I think it might be java not using the full 1760M of shared graphics memory. Any way I could assign it?

---

### Post by kyconny on 2011-09-08
WOOOHOOO I got a error message!
After trying to allocate more ram as I thought doing this might allow the graphics card to use more I used the command
javaw -Xmx14336m -Xms7168m -jar minecraft.jar
(Yes I know its excessive but it was a test)
And in the terminal I noticed every time I got a lag spike UpdateThread still working in unpause()!!!
showed up.
This seems suitable for the minecraft forums or notches twitter.
A case of notchs bad coding :)

---

