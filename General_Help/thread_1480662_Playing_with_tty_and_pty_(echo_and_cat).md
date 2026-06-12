---
title: "Playing with tty and pty (echo and cat)"
date: 2010-05-11
forum: General Help
---

### Post by nicolasbol on 2010-05-11
I've read a bit about pseudo terminal but I still don't get it fully, I've found a really sweet article:

[http://tldp.org/HOWTO/Text-Terminal-HOWTO-7.html](http://tldp.org/HOWTO/Text-Terminal-HOWTO-7.html)

I thought the two end tty and pty were acting like a pipe so while testing, I opened two terminals:

terminal1: cat /dev/ptyq9
terminal2: echo "test" > /dev/ttyq9

And it worked, terminal 1 printed: "test".

But if the pipe is bi-directionnal ( as terminal were echoed back what user was typing), I was expecting to be able to go the other way around:

terminal1: cat /dev/ttyq9
terminal2: echo "test" > /dev/ptyq9


It does not work ! Echoing on pty just terminates the cat on pty. How is the "return" working them ?

---

### Post by bredman on 2010-05-11
The pipe supports bi-directional data, but you have to be careful how you connect to the pipe. tty is suitable for use by file-based applications, but pty should only be used by network applications.

The reason that you only see a one-way communication is because cat only receives data and echo only sends data. You would need more complex programs to transfer data bi-directionally.

---

