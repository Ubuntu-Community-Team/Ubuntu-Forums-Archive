---
title: "Trying to install Aleph One/Marathon"
date: 2010-08-08
forum: General Help
---

### Post by Vanillalite on 2010-08-08
So I'm running 64 Ubuntu 10.04 though I doubt that matters here.

[I grabbed the files from here!]("http://source.bungie.org/index.php?title=Get_Marathon")

Now I extracted the Aleph Engine and the 3 scenarios each to their own directories. Now it seems the next step is to make a runable file for Aleph. I'm a terminal noob, but I've done this once or twice before. 

First I went...

```
./configure
```

Everything checked out since I read the read me before hand to download all the libs I needed. It even said configuration done now type make. So Next I went with...

```
Make
```

Now it *seemed* like it was working cause it was doing a ton of ****. Eventually that just ended but it never really told me it was done and everything was good like the last step? IDK I just said screw it and went ahead with step 3...

```
sudo make install
```

Again it appeared to do some stuff, and that was that. Yet I'm not seeing a file in my alephone directory to actually run now? I'm seriously confused as all get out here! Thanks in advance!

---

### Post by Doobie9 on 2010-08-18
I would like to add that I am running Mint 9 64 (should be the same as Lucid for this purpose), and have gone through the ./configure part of the process without a hangup. But after I've run make I get this string of errors: 

> make[4]: *** [network_microphone_sdl_alsa.o] Error 1
make[4]: Leaving directory `/home/phoebus/Downloads/Marathon/AlephOne-20100424/Source_Files/Network'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/phoebus/Downloads/Marathon/AlephOne-20100424/Source_Files/Network'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/phoebus/Downloads/Marathon/AlephOne-20100424/Source_Files'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/phoebus/Downloads/Marathon/AlephOne-20100424'
make: *** [all] Error 2


There is no apparent binary, and it seems as though the build has failed. Checkinstall exits with an error. Sorry I could not help; I hope I have added some useful information. Does it spit out the same crap for you?

I once built Aleph One on a 32 bit Ubuntu machine a little over a year ago without this problem.

---

### Post by iamanidiot123 on 2011-07-24
Kindly show the entire list of errors by copying farther up the list

---

