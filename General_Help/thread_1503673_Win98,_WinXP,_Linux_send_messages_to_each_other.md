---
title: "Win98, WinXP, Linux send messages to each other?"
date: 2010-06-07
forum: General Help
---

### Post by Cool Javelin on 2010-06-07
Can someone explain to me, or if it's even possible, for a Windoz computer to send a message to Linux (or vice versa) and have the receiver act on that message?

For example. I have a DOS program running on a win computer that monitors some hardware connected to the parallel port, and heyu home automation running on the Linux. I would like heyu to turn on a light triggered by an event on win.

Can I send a message, via the OS, from win and run a script on Linux? Can I do that from Linux to Win?

Once upon a time there was a messaging system called WinPop (circa Win3.1, and Win95) I assume the functionality still exists even if those archaic programs don't.

Currently, I make Windoz create a file on Linux, then the Linux box checks for that file once a minute using cron. This works, but I would prefer a cleaner solution.

Thanks, Mark.

---

### Post by john newbuntu on 2010-06-07
You should be able to use a program like puTTY on windows to talk over ssh to linux.  The network swiss army knife, netcat is another utility that can be used.  cygwin is yet another.

---

### Post by Jose Catre-Vandis on 2010-06-07
You can use Linpopup on Ubuntu with netsend on your Windows boxes

---

### Post by Cool Javelin on 2010-06-08
Wow, I have taken the next step toward total world dominance. I have installed PuTTY on my Wondoz boxes, and openssh-server on xubuntu, and I can open a terminal window and log on to Linux. Thanks John.

Now, how do I get a DOS program that I write to send a message to Linux and get Linux to run a script depending on that message?

Ideally, I would like to send a message like 'xubuntu, run script so-and-so and report back to me it's exit status'

I am still looking into the other suggestions, netcat, cygwin, Linpopup.

 Thanks. Mark.

---

### Post by john newbuntu on 2010-06-08
Check if plink.exe is a part of the putty package.  Its been a while since I did this.  If not, you might have to download it.  You would then create a simple text file in win(a DOS script using notepad) called say, runlnx.bat that invokes plink.exe.

Here's an example of what might go into the .bat file:
C:\<path to plink.exe>\plink.exe -ssh -P 65432 user@server echo "hi there"
This uses port 65432 on the linux box on serverand runs the echo command using user's login.

Here's some more stuff on plink:
[http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter7.html#7.2.2](http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter7.html#7.2.2)

---

