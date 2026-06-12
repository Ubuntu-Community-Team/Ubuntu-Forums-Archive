---
title: "Firewall for Ubuntu"
date: 2009-09-13
forum: General Help
---

### Post by sopadeajo on 2009-09-13
Is there a firewall not too hard to use recommended for Ubuntu?

---

### Post by mikewhatever on 2009-09-13
Yes, gufw is a GUI for iptables.

---

### Post by sopadeajo on 2009-09-13
Ok mikewhatever, i have bookmarked the page, but in a glance i have understood what they say. I am not complaining, since i agree with Linux and free and open software philosophy and do not like window$ at all. Just new to Ubuntu.
I supoose then that it is considered that:
1) a firewall is not necessary with Linux cause a) nobody will hack you b) Linux cannot be hacked
2) the structure of Linux is so completely different from windows that a firewall is a nonsense
3) firewalls in Linux are completely different from firewalls in windows
I would like to know which of 1a) 1b)  2) or 3) is true

---

### Post by pythonscript on 2009-09-13
*Antivirus *software is normally not necessary in Linux (at least not for the security of your own system). However, a firewall is certainly necessary, especially if you use ssh or something similar. What you're thinking of is a GUI for a firewall, not a firewall itself. Ubuntu includes a firewall by default called iptables, which by default closes all ports. All you're thinking of is a GUI for configuring this. Really, you don't need a GUI; if you're only running a basic Linux system, let Ubuntu take care of this for you. 
1a) wrong
1b) wrong
2)yes, the structure is different, but a firewall is still necessary (see above for a *firewall*, not a *GUI*)
3)not sure, but I would assume the coding is different because of the differences in structure, but in terms of controlling how network traffic moves through ports, the theory is almost identical.

---

### Post by sopadeajo on 2009-09-13
ok, Pythonscript, thanks for your good answers,I have understood more about firewall tasks in Linux. You are right i was thinking in a GUI (and i have downloaded gufw) but i was not thinking in beautiful bright colors; and more than this, i was thinking in a third party software but am glad to find it all within Ubuntu.
I'ill read on iptables and begin learning to use them in a GUI mode or not.

---

### Post by spcwingo on 2009-09-13
> **mikewhatever said:**
> Yes, gufw is a GUI for iptables.

GUFW is a GUI for UFW, not iptables.

---

### Post by mikewhatever on 2009-09-13
> **sopadeajo said:**
> ok, Pythonscript, thanks for your good answers,I have understood more about firewall tasks in Linux. You are right i was thinking in a GUI (and i have downloaded gufw) but i was not thinking in beautiful bright colors; and more than this, i was thinking in a third party software but am glad to find it all within Ubuntu.
I'ill read on iptables and begin learning to use them in a GUI mode or not.

IPtables is kind of complicated, and I am not even sure you need learning it. I think it's important to understand what a firewall is in the first place. Also take a look at the security sticky: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by katakaio on 2009-09-13
Hi sopadeajo - by far, my favorite has been [Firestarter]("http://www.fs-security.com/"). It's simple to learn how to use and very powerful. I found it to be the best introduction to configuring a firewall in Ubuntu. You can get it by running **sudo apt-get install firestarter** from the terminal. Hope you like it!

---

### Post by sopadeajo on 2009-09-14
Thanks Katakaio: i am learning to use it and liking it very much. A very good user-interactive firewall and not hard to use.

---

### Post by katakaio on 2009-09-14
Glad to help! One thing I should have mentioned is that Firestarter isn't a firewall [I]per se[I]. It's a pretty way to configure the security settings that are at the heart of Ubuntu - things like your IP tables, port forwarding, etc. This is one reason why Ubuntu is so much more secure that other operating systems - the security isn't a program you install, it's the operating system itself!

I hope you enjoy Firestarter. Don't forget to mark the thread solved if you're satisfied. You can do this via the *Thread Tools* link near the upper right of the original post.

---

