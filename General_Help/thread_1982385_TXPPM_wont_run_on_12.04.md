---
title: "TXPPM wont run on 12.04"
date: 2012-05-18
forum: General Help
---

### Post by ddarsow on 2012-05-18
I use a cool little app called TXPPM which acts to convert the output of a RC Radio Transmitter so it can be used through the audio input to run a simulator.

Anyway, the app worked perfectly untill I installed 12.04 and now it will not launch. Trying to launch it from the dash does nothing at all. Trying to launch it from the executable file in the usr/share/txppm dir results in the following error:

Details: Failed to execute child process "/usr/bin/ppm2tx" (No such file or directory)

Unfortunately there seems to little or no support for it from the author. Does anyone else use it and perhaps have a solutions? I am suspecting that something needs to be changed to work with 12.04, but not sure what.

I know it is a long shot on the Ubuntu forums, but certainly I am not the only RC Helicopter guy on here!

---

### Post by ddarsow on 2012-05-25
anyone?

---

### Post by Mr Roboto on 2012-09-18
Did you ever figure this out? I'm trying too.

Compiling from scratch borks when trying to link to the static library provided.
If you install portaudio-dev (sudo apt-get install libportaudio-dev) you can try linking against that:

Edit Makefile and change it to:
```

#LIBPA	=lib/libportaudio-x86.a
#ifeq ($(shell uname -m),x86_64)
#	LIBPA =lib/libportaudio-x86_64.a
#endif
LIBPA=-lportaudio

```

But it won't compile as it gives the error:
```

cc -o ppm2tx ppm.o sys.o tui.o -lm -lpthread -lasound -lportaudio -O2
ppm.o: In function `init_audio':
ppm.c:(.text+0x31d): undefined reference to `Pa_GetDeviceCount'
ppm.o: In function `list_audio':
ppm.c:(.text+0x2c2): undefined reference to `Pa_GetDeviceCount'
collect2: ld returned 1 exit status
make: *** [ppm2tx] Error 1

```

It's better, but I can get no further.

---

### Post by markallinson on 2013-05-25
As far as I can see TXPPM [http://txppm.4dstabi.com/index.php](http://txppm.4dstabi.com/index.php) is no longer being developed or supported, which is a real shame as it is a very useful piece of software.

---

### Post by bazsound on 2013-07-02
ive just spent hours trying to get it working and just cant, it must be something simple. googling some of the errors seems to suggest that theres a missing dev file

but i cant figure out what is needed,

i even tried to find contact details for the dev but no deal

---

### Post by bazsound on 2013-07-03
Got a hold of the dev, if anyone still wants to use this he told me that he thinks he can fix it

---

### Post by Daniel_Lopez on 2014-03-10
I know this is a 9 month old post, But I hate unanswered questions.

You can build TXPPM for 12.10 and up using the directions here [http://txppm.4dstabi.com/generic.html](http://txppm.4dstabi.com/generic.html)

---

