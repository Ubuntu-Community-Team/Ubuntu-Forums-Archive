---
title: "tty1 (or tty2 ..6) output on another (putty) device?"
date: 2010-10-09
forum: General Help
---

### Post by Cool Javelin on 2010-10-09
I have an Ubuntu server (10.04.1) and I want to have a custom piece of home automation software running.

I would like this to start automatically when it boots, I think I can handle that.

From the keyboard, I can press ALT-F1, ALT-F2, etc to switch to several tty devices. That's all good.

I would like the software to start on a specific tty channel (pretend tty4.)

Later, I would like to putty in and monitor tty4. See the output, and have the keyboard interact with my software.

I have used VNC on a different machine, but I don't have, nor do I want X installed on the server.

Please help me decide which options would be easiest.

Option 1, Be able to use putty to hijack (or duplicate) one of the already open tty channels. This might be the best (the most transparent), but I don't know how to tell putty to do this.

Option2, putty in and somehow tell my software (I am writing custom) to redirect it's output and input to the putty channel rather then tty4. This will need to happen dynamically as the software cannot be interrupted with it's information gathering.

Option 3, use VNC in a text mode to take over tty4, Is this possible? how do I do that?

Option 4, Maybe write an independent program (download one that already exists?) that will take tty4 output and duplicate it to a putty channel (keyboard input too.)

I have been using putty to remote in, but I don't know a lot about it. I know I can open several putty connections and log in with the same name and they are independent. I don't know what the channels are called.

Thanks for your help,

Mark.

---

### Post by solar george on 2010-10-09
Sounds like your best option would be to start the program in screen [http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/) which would allow you to share the text terminal between several sessions or you could take a look at [linuxvnc]("apt://linuxvnc") which claims to be able to export a text terminal to vnc (I've not tried this).

I would suggest your best option would be to use screen as it can be run straight over ssh and will most probably be lower bandwidth than linuxvnc.

---

