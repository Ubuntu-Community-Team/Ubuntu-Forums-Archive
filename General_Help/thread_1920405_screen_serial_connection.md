---
title: "screen serial connection"
date: 2012-02-04
forum: General Help
---

### Post by abdulva on 2012-02-04
Hello guys, I have a 68HC11 micro controller. I can connect to the Buffalo monitor on the board using screen /dev/ttyUSB0 9600. Screen works fine but I can't load the assembly file into the board. I used "LOAD T filename.s19" but the program freezes without loading.
Thanks,
Abdul

---

### Post by Khayyam on 2012-02-05
abdulva ...

It's been a long time since I touched one of these boards. Not ever having used screen for this purpose I'm not sure I can say it'll will play nice with it (flow control, xon/xoff, etc). You might think about using [minicom](https://help.ubuntu.com/community/Minicom) in its place.

In the past I've used Clifford Heath's [DB11](http://polyplex.org/electronics/db11.html), which impliments terminal emulation, loader, and debugger in one. Its c++ and so will require you have g++ insalled in order to compile it.

Not sure what "LOAD" is, its not a loader I've seen or heard of, but I could be that screen doesn' set up the serial connection in a way that LOAD expects.

Again, long time no do'ee .. but I imagine this is why it hangs.

HTH ...

---

