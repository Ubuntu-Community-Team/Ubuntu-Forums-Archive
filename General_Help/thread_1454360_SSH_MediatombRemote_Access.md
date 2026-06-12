---
title: "SSH Mediatomb/Remote Access"
date: 2010-04-14
forum: General Help
---

### Post by imbty on 2010-04-14
So I'm testing out Ubuntu 8.04 for my home server (it'll be Ubuntu Server Edition once I buy new parts).

I plan to use Mediatomb so I can stream to the PS3.

Now, my main laptop is a Mac. I can turn on Mediatomb on Ubuntu using my Mac's Terminal. However, once I turn that off, Mediatomb shuts down.

What I'd like to do is be able to tell my Ubuntu to turn on Mediatomb using my Mac, quit Mac's Terminal, and have Ubuntu still running Mediatomb.

Kinda like Remote Access. I can use remote access through screen sharing to do this, but since using terminal will be faster, it'd rather do that, and I'd also like to be able to do this via internet (i've heard doing this through SSH is more secure).

PS: Anyone know if I can use SSH to tell my Ubuntu to download a torrent? Thanks

---

### Post by impact on 2010-04-14
If I understand this correctly, you want to SSH into your Ubuntu machine and then run Mediatomb/whatever... then break the connection without killing the program? You can use screen/byobu for that.


Take a look at this:

[http://blog.smartlogicsolutions.com/2010/01/22/ubuntu-byobu-landscape/](http://blog.smartlogicsolutions.com/2010/01/22/ubuntu-byobu-landscape/)

short version:

1) connect to your machine via ssh
2) launch byobu
3) do whatever you want
4) use F6 to detach yourself from the session and break the connection

5) connect to your machine again
6) type "screen -r" to reattach yourself to the previous session

---

### Post by imbty on 2010-04-14
That's correct. I want to SSH into Ubuntu macine and open/run Mediatomb, break connection without killing Mediatomb

Unfortunately, I can't seem to install Byobu atm. I've tried apt-get, and I've also tried installing the .tar.gz but i've failed both, specially the latter.

---

### Post by imbty on 2010-04-14
That's right. I wan't to SSH into Ubuntu machine, open/run Mediatomb,close connection without killing Mediatomb.

I've tried apt-get for Byobu, but package can't be found. I've failed trying to install .tar.gz.

---

### Post by impact on 2010-04-14
I am using 9.10, which is probably the reason why I could find byobu in the repositories.

You could use plain "screen" instead, byobu is just an extension of that. Try searching for that. Unfortunately the screen controls are a bit more complicated, you need to use Ctrl-A D to detach yourself from your session. 

See this [http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/](http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/)

---

### Post by buntunoob on 2010-04-19
mediatomb -d
starts it as a daemon

---

