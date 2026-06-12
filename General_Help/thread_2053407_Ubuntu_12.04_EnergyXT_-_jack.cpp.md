---
title: "Ubuntu 12.04 EnergyXT - jack.cpp"
date: 2012-09-05
forum: General Help
---

### Post by guhya on 2012-09-05
Hi guys,

I'm having a problem with compiling jack.cpp for EnergyXT I get this message when I try:

jack.cpp: In function ‘int libaam(int, int, int)’:
jack.cpp:427:27: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
jack.cpp:443:20: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
jack.cpp:471:14: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
jack.cpp:496:20: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
jack.cpp:519:20: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
jack.cpp:530:21: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
jack.cpp: In member function ‘void CMIDIDev::enable(int)’:
jack.cpp:578:42: error: cast from ‘snd_rawmidi_t* {aka _snd_rawmidi*}’ to ‘int’ loses precision [-fpermissive]
jack.cpp: In constructor ‘CMIDIThread::CMIDIThread(int, int)’:
jack.cpp:608:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]

I use this command which is supposed to be correct:
sudo g++ -shared -lasound -ljack jack.cpp -o libaam.so

any clues why this doesn't work?


jack.cpp can be found here [http://www.energy-xt.com/index.php?id=1201](http://www.energy-xt.com/index.php?id=1201)

---

