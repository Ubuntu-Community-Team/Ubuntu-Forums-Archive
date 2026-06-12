---
title: "firewalls--how do I tell/fix?"
date: 2006-03-25
forum: General Help
---

### Post by LadyDoor on 2006-03-25
Ok, so *this* time I'm just wondering whether a) there's a way to tell if I've got a firewall up, and b) whether port 49153 UDP is open? Also, if such a way does exist, how would I go about opening said port if it were closed?

Thanks, and kudos for all helpful people!
--Door

---

### Post by trent dillman on 2006-03-25
```
sudo apt-get install firestarter
```

then just run it using sudo

```
sudo firestarter
```

Any particular reason for the port question? Seems awfully specific...

---

### Post by LadyDoor on 2006-03-25
The thing is, I'm trying to use Azureus and it popped up a warning claiming that I have some kind of screwy firewall or something blocking that and it was all like "make sure it's open or we'll take your firstborn child" and I was all like "oh no!"*

But the problem seems to be that I've got an overfunctional one, not an underfunctional one...so why install firestarter, if I may ask?

--Door

*I'm paraphrasing just a little bit here.

---

### Post by trent dillman on 2006-03-25
Ah...well, did you open the ports in your router (if you have one)?

---

### Post by LadyDoor on 2006-03-25
I don't *think* I have a router...I'm a college student and using the college-provided interweb straight from an ethernet cord (I think) hooked into the wall, which is how they have it set up all over campus...so if I don't have one, what do I do?

---

### Post by trent dillman on 2006-03-25
Aw snap, p2p on a college line. Sounds to me like it's firewalled. You might be SOL. :(

---

### Post by LadyDoor on 2006-03-25
Oh well. Thanks. For the record though, I really *am* nerdy, because I'm not even trying to use it for illegal purposes...I'm trying for some useful education-type stuff that I'll just go get somewhere else by some method I actually understand.

Thanks for your help!

--Door

---

### Post by Herman on 2006-03-25
Just for the record, we do have an excellent firewall already set up and running silently in the background but most people are unaware of its existence because it doesn't annoy the heck out of us like those found on some other operating systems. It's called iptables, here are some links:
[Iptables - LinuxQuestions.org Wiki]("http://wiki.linuxquestions.org/wiki/Iptables")
[Welcome to JustLinux: Wanna learn Linux?]("http://www.justlinux.com/nhf/Security/IPtables_Basics.html")
[Iptables Tutorial 1.1.19 - Firewall]("http://www.faqs.org/docs/iptables/")
[Iptables Tutorial 1.2.0]("http://iptables-tutorial.frozentux.net/iptables-tutorial.html")
[Netfilter/iptables - Wikipedia, the free encyclopedia]("http://en.wikipedia.org/wiki/Iptables")
I do realise they take some studying to take all that in, I'm only beginning with it myself, and prefer not to tamper with mine until I'm more confident. At least we should be aware that iptables exist.
Try a firewall test at[ https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")   [COLOR=#000000][FONT=Arial]or[/FONT][/COLOR][http://scan.sygatetech.com]("http://scan.sygatetech.com/")
Regards, :D  Herman

---

### Post by Mustard on 2006-03-25
One last addition to the information given by others.  To see if firestarter is running try this command..

```
sudo /etc/init.d/firestarter status
```

This will give output like this..

```
mustard@slave:~$ sudo /etc/init.d/firestarter status
Password:
Firestarter is running...

```

---

### Post by LadyDoor on 2006-03-25
Cool, thanks!

--Door

---

