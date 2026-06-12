---
title: "Please help me install library"
date: 2009-11-22
forum: General Help
---

### Post by liglio on 2009-11-22
Hello,I`m trying to install libsndfile-1.0.20.tar 
I login as root and do this
1.tar zxvf libsndfile-1.0.20.tar
2.cd libsndfile...
3../configure
4.make
5.make install
6.cd
  
 but when make install I get some errors like this : make: Warning: File `.deps/xi.Plo' has modification time 5.4e+03 s in the future
make: warning:  Clock skew detected.  Your build may be incomplete.
make: Warning: File `.deps/write_read_test.Po' has modification time 4.5e+03 s in the future
make: warning:  Clock skew detected.  Your build may be incomplete.


make[1]: Warning: File `.deps/sndfilehandle.Po' has modification time 4.4e+03 s in the future
  CXX   sndfilehandle.o
/root/libsndfile-1.0.20/shave: line 75: g++: command not found
make[1]: *** [sndfilehandle.o] Error 127
make: *** [install-recursive] Error 1
 
and this,anyone help me please?

---

### Post by ibuclaw on 2009-11-22
What is wrong with the one that is already in the repositories?

```
sudo apt-get install libsndfile1
```
Or if you require developer header/files for it:
```
sudo apt-get install libsndfile1-dev
```
Regards
Iain

---

### Post by liglio on 2009-11-22
I try to compile another file called dab.c but I can`t because i get this errors : root@boris-desktop:~# gcc dab.c -o dab
dab.c:26:20: error: common.h: No such file or directory
dab.c:27:21: error: toolame.h: No such file or directory
dab.c:28:34: error: toolame_global_flags.h: No such file or directory
dab.c:29:17: error: dab.h: No such file or directory
dab.c:33: error: expected ‘)’ before ‘*’ token
dab.c: In function ‘dab_crc_update’:
dab.c:86: error: ‘CRC8_POLYNOMIAL’ undeclared (first use in this function)
dab.c:86: error: (Each undeclared identifier is reported only once
dab.c:86: error: for each function it appears in.)
root@boris-desktop:~# 


and I think the problem is in libsndfile PLEASE HELP ME

---

### Post by ibuclaw on 2009-11-22
How did you get dab.c?

It looks like there should be several headers with that source file, but it doesn't know where they are.

> 
dab.c:26:20: error: common.h: No such file or directory
dab.c:27:21: error: toolame.h: No such file or directory
dab.c:28:34: error: toolame_global_flags.h: No such file or directory
dab.c:29:17: error: dab.h: No such file or directory


None of the above listed files will be in libsndfile-dev.


Also, why on earth are you compiling as root? :|

---

### Post by liglio on 2009-11-22
because when I tried compiling as user : no permissions or something like that,that`s why I logged in as root,so what`s the problem,and how can I fix it? can you helo me,I`m new to ubuntu and to the forum at all,sorry for disturbing you ...

---

### Post by ibuclaw on 2009-11-22
> **liglio said:**
> because when I tried compiling as user : no permissions or something like that,that`s why I logged in as root,so what`s the problem,and how can I fix it? can you helo me,I`m new to ubuntu and to the forum at all,sorry for disturbing you ...

Well, where did you get dab.c from?

Where did you download the file/archive?

That would be a clue as to how to properly compile it.

Regards
Iain

---

### Post by liglio on 2009-11-22
privite or?

---

### Post by ibuclaw on 2009-11-22
[QUOTE=liglio]I get dab.c from a friend of mine,and downloaded libsndfile from its official download site.[/QUOTE]

Is this the file? [http://www.altsci.com/concepts/dab.html](http://www.altsci.com/concepts/dab.html)

If so, run:
```
sudo apt-get install libsndfile1-dev
```
in a terminal, then run:
```
gcc dab.c -o dab -lsndfile
```
To compile dab.c

Regards
Iain

---

### Post by liglio on 2009-11-22
root@boris-desktop:~# sudo apt-get install libsndfile1 -dev
E: Command line option 'e' [from -dev] is not known.
root@boris-desktop:~# 


what about this my friend?  :(

---

### Post by liglio on 2009-11-22
the first problem is installing libsndfile and the second dab.c :) I`ll be so gratefull if you help me solving this problem and .... : )

---

### Post by ibuclaw on 2009-11-22
[QUOTE=liglio]root@boris-desktop:~# gcc dab.c -o dab -lsndfile
root@boris-desktop:~# dab -f audio
The program 'dab' is currently not installed.  You can install it by typing:
apt-get install bsdgames
dab: command not found
root@boris-desktop:~# 


1.libsndfile
2.compilation
3.installation of dab ? 
root@boris-desktop:~# gcc dab.c -o dab -lsndfile
root@boris-desktop:~# dab -f audio
The program 'dab' is currently not installed.  You can install it by typing:
apt-get install bsdgames
dab: command not found
root@boris-desktop:~# 


please step by step....[/QUOTE]

OK, so you've managed to successfully compile dab.c :)

To run it, since it isn't installed, you need to include ./ to tell the shell to run the file in your current directory use:
```
./dab -f audio
```

If you wish to install it:
```
sudo install dab /usr/local/bin
```
And **then** you can run it as:
```
dab -f audio
```

Regards
Iain

---

### Post by liglio on 2009-11-22
root@boris-desktop:~# sudo install dab /usr/local/bin
root@boris-desktop:~# sudo install dab /usr/local/bin
root@boris-desktop:~# sudo install dab /usr/local/bin
root@boris-desktop:~# dab -f wave.wav
dab - Decode Aiken Biphase
Version 0.6
Copyright (c) 2004-2005  Joseph Battaglia <redbird@2600.com>

*** Opening wave.wav
*** Input file format:
    Frames: 286676
    Sample Rate: 22050
    Channels: 1
    Format: 0x00010005
    Sections: 1
    Seekable: 1
*** Silence threshold: 9753 (30% of max)
*** Parsing 286676 samples
Found 4509 peaks
11111111111111111111111111111111111111111111111111111111111
root@boris-desktop:~# 


thats what I get,It is not enough,not working properly.... 
hmmm ? what about libsndfile...is it installed,be m0re specific pplease

---

### Post by liglio on 2009-11-22
*** Opening /dev/dsp
*** setting audio device parameters:
      Format: AFMT_S16_LE
      Channels: 1
      Sample rate: 192000

(nautilus:31863): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:32023): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed


THIS IS STDOUT FILE,this is the result of wave.wav ? what does it meand? something`s wrong with my soundcard? why it does not decode?

---

### Post by ibuclaw on 2009-11-22
> **liglio said:**
> root@boris-desktop:~# sudo install dab /usr/local/bin
root@boris-desktop:~# sudo install dab /usr/local/bin
root@boris-desktop:~# sudo install dab /usr/local/bin
root@boris-desktop:~# dab -f wave.wav
dab - Decode Aiken Biphase
Version 0.6
Copyright (c) 2004-2005  Joseph Battaglia <redbird@2600.com>

*** Opening wave.wav
*** Input file format:
    Frames: 286676
    Sample Rate: 22050
    Channels: 1
    Format: 0x00010005
    Sections: 1
    Seekable: 1
*** Silence threshold: 9753 (30% of max)
*** Parsing 286676 samples
Found 4509 peaks
11111111111111111111111111111111111111111111111111111111111
root@boris-desktop:~# 


thats what I get,It is not enough,not working properly.... 
hmmm ? what about libsndfile...is it installed,be m0re specific pplease

Just tried it myself, and that is exactly what I get too.
So I must assume that it is working perfectly to design.

Yes, libsndfile is installed, else it wouldn't have compiled in the first place.


When you say "decode", explain what you mean?
Having a look at the source code, this looks like a "decode analyser" that measures silence and peaks in a soundcard/file.

---

### Post by markling on 2012-05-25
> **ibuclaw said:**
> 
Also, why on earth are you compiling as root? :|

From...
[http://tldp.org/HOWTO/Software-Building-HOWTO-3.html](http://tldp.org/HOWTO/Software-Building-HOWTO-3.html)

"Using make as an ordinary user without root privileges will likely result in write access denied error messages because you lack write permission to system directories...Installing the freshly built binaries into the appropriate system directories is usually a matter of running make install as root."

---

### Post by howefield on 2012-05-25
Please open a new thread rather than digging up old ones, you may reference this thread if needs be.

---

