---
title: "Help with installing pianobar"
date: 2010-10-02
forum: General Help
---

### Post by nkav on 2010-10-02
Hello,

I am somewhat new to Ubuntu and am having trouble making and installing pianobar. Here is the output it is giving me. 

```
nilesh@ubuntu:/usr/local/src/pianobar-0+git20100420.3072c5a$ make
[ 50%] Built target ezxml
[ 50%] Built target waitress
[ 50%] Built target piano
Linking C executable pianobar
CMakeFiles/pianobar.dir/main.o: In function `main':
main.c:(.text+0x86): undefined reference to `ao_initialize'
main.c:(.text+0xd05): undefined reference to `ao_shutdown'
CMakeFiles/pianobar.dir/player.o: In function `BarPlayerAACCb':
player.c:(.text+0x3d7): undefined reference to `ao_play'
player.c:(.text+0x710): undefined reference to `ao_default_driver_id'
player.c:(.text+0x78a): undefined reference to `ao_open_live'
CMakeFiles/pianobar.dir/player.o: In function `BarPlayerMp3Cb':
player.c:(.text+0xfc9): undefined reference to `ao_default_driver_id'
player.c:(.text+0x1025): undefined reference to `ao_open_live'
player.c:(.text+0x1103): undefined reference to `ao_play'
CMakeFiles/pianobar.dir/player.o: In function `BarPlayerThread':
player.c:(.text+0x1443): undefined reference to `ao_close'
collect2: ld returned 1 exit status
make[2]: *** [src/pianobar] Error 1
make[1]: *** [src/CMakeFiles/pianobar.dir/all] Error 2
make: *** [all] Error 2
```


Help is sincerely appreciated. Thanks!

---

### Post by lykeion on 2010-10-02
It would make it easier if you'd explain/give links to pianobar. You can't expect everyone to know what this is.
I googled it and I guess you mean this: [http://6xq.net/html/00/17.html](http://6xq.net/html/00/17.html)

It would also help if you'd mention your Ubuntu version. I'm guessing you use Lucid (in Maverick pianobar is in the repositories).

You could manually download and install it from the Maverick repositories. You'll also need two two required libraries. 
Here are the links to the packages (choose i386 if you don't have a clue):
[LIST]
[*][libao-common]("http://packages.ubuntu.com/maverick/libao-common")
[*][libao4]("http://packages.ubuntu.com/maverick/libao4")
[*][pianobar]("http://packages.ubuntu.com/maverick/pianobar")
[/LIST]
After download just doubleclick to install and do it this order: libao-common > libao4 > pianobar

---

