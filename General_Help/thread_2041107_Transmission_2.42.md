---
title: "Transmission 2.42"
date: 2012-08-11
forum: General Help
---

### Post by MooFx on 2012-08-11
Hi there,

I just downloaded Transmission 2.42 because my tracker does not accept the newest version yet.
However, when I try to "make" I get the response:
```
make: *** No targets specified and no makefile found.  Stop.
```

"./configure" worked, but now I can't continue.
Any suggestions?

---

### Post by marlow59 on 2012-08-11
well, normally once you've run ./configure it did create a bunch of directories, if there is no makefile among them, then you have to look for it inside one of the directories(probably src/ or smth like that). I advise you to read the installation notice or documentation that you have probably downloaded with the source file, it will show you step by step what commands you have to run in what directories. Another point is, you can download prepackaged .deb files for previous versions of popular software like transmission.
 Hope it helps.

---

### Post by MooFx on 2012-08-11
There are 2 makefiles; Makefile_am and Makefile_in.
According to the documentation I should just run

> ./configure make make install

If I try to install Tranmission 2.42 with a .deb, I keep getting the latest Transmission version for some reason.

---

### Post by ads52 on 2012-08-12
Perhaps you could have a look at this Ubuntu Community Wiki page:

[https://help.ubuntu.com/community/CompilingTransmission](https://help.ubuntu.com/community/CompilingTransmission)

and simply change the download and compile section to:

```

cd $HOME/transmission_build && \
wget [COLOR=Red]**http://download-origin.transmissionbt.com/files/transmission-2.42.tar.bz2**[/COLOR] && \
tar xjvf[COLOR=Red]** transmission-2.42.tar.bz2**[/COLOR] && cd[COLOR=Red]** transmission-2.42**[/COLOR] && \
export PKG_CONFIG_PATH="$HOME/transmission_build/libevent/lib/pkgconfig" && \
./configure && make && \
sudo checkinstall --pakdir "$HOME/transmission_build" --backup=no --deldoc=yes \
  --fstrans=no --deldesc=yes --delspec=yes --default --pkgversion "[COLOR=Red]**2.42**[/COLOR]" && \
make clean

```

But you would then need to 'lock' this version in Synaptic to prevent repository updates.

---

### Post by MooFx on 2012-08-12
> **ads52 said:**
> Perhaps you could have a look at this Ubuntu Community Wiki page:

[https://help.ubuntu.com/community/CompilingTransmission](https://help.ubuntu.com/community/CompilingTransmission)

and simply change the download and compile section to:

```

cd $HOME/transmission_build && \
wget [COLOR=Red]**http://download-origin.transmissionbt.com/files/transmission-2.42.tar.bz2**[/COLOR] && \
tar xjvf[COLOR=Red]** transmission-2.42.tar.bz2**[/COLOR] && cd[COLOR=Red]** transmission-2.42**[/COLOR] && \
export PKG_CONFIG_PATH="$HOME/transmission_build/libevent/lib/pkgconfig" && \
./configure && make && \
sudo checkinstall --pakdir "$HOME/transmission_build" --backup=no --deldoc=yes \
  --fstrans=no --deldesc=yes --delspec=yes --default --pkgversion "[COLOR=Red]**2.42**[/COLOR]" && \
make clean

```

But you would then need to 'lock' this version in Synaptic to prevent repository updates.
Thanks alot! This worked without problems :)

---

### Post by ads52 on 2012-08-12
> **MooFx said:**
> Thanks alot! This worked without problems :)

Excellent news :).

---

### Post by MooFx on 2012-09-29
I tried this again. Did everything as before, I think.
But this time I keep getting the output: 

```
checking for OPENSSL... no
checking for OpenSSL... configure: error: Cannot locate ssl
```

However, when I try: dpkg -l | grep openssl
I get:
```
ii  openssl                                1.0.1-4ubuntu5.5                        Secure Socket Layer (SSL) binary and related cryptographic tools
ii  python-openssl                         0.12-1ubuntu2                           Python wrapper around the OpenSSL library

```

Help? :confused:

---

### Post by davebos on 2012-11-12
> **MooFx said:**
> I tried this again. Did everything as before, I think.
But this time I keep getting the output: 

```
checking for OPENSSL... no
checking for OpenSSL... configure: error: Cannot locate ssl
```

However, when I try: dpkg -l | grep openssl
I get:
```
ii  openssl                                1.0.1-4ubuntu5.5                        Secure Socket Layer (SSL) binary and related cryptographic tools
ii  python-openssl                         0.12-1ubuntu2                           Python wrapper around the OpenSSL library

```

Help? :confused:


Had the same problem in Ubuntu 12.10.  Try installing libssl-dev.

---

