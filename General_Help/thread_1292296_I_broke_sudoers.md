---
title: "I broke sudoers"
date: 2009-10-15
forum: General Help
---

### Post by Theory5 on 2009-10-15
err I have a little problem. When I was trying to make firestarter startup when Ubuntu started I ran into a problem. I used the command
Sudo chmod -R 775 /etc/sudoers 
and it kinda screwed up. I had used that command to unlock every file that had been locked that i needed access to. it worked all the other times.
Now with that sudoers file It is saying 
Code:
sudo: /etc/sudoers is mode 0775, should be 0440
Segmentation fault
and when I run 
Code:
Sudo chmod -R 440 /etc/sudoers
it still gives me that error. I didnt realize that sudoers file was so important. How do I fix it?
Anytime i try to sudo or su it brings up that error!

---

### Post by jeremyswalker on 2009-10-15
What were you trying to do with your sudoers file? It is suppose to be editted with visudo:
```
sudo visudo
```

---

### Post by sisco311 on 2009-10-15
Reboot in Recovery Mode and fix the permissions:
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

Always use visudo to edit the file:
[thread=1132821]HowTO: Sudoers Configuration[/thread]

```
sudo VISUAL=gedit visudo
```
replace gedit with your editor of choice.

---

### Post by Theory5 on 2009-10-16
really? thats weird because the firestarter tutorial mentioned NOTHING about visudo.
Thanks

---

### Post by bodhi.zazen on 2009-10-16
First, firestarter is old and has not been maintained.

The default application in Ubunt uis ufw, gufw if you wish to have a gui application.

Second, I am sorry , but the tutorial you are following is just wrong, you ar emis informed. You should not be running firestarter all the time.

Start fire starter, configure your firewall, and close firestarter. That's it. Your firewall will be configured when you boot, nothing more to do.

Do NOT use firestarter to monitor network traffic.

See :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

In terms of fixing your problem, again do not change ownership and permissions of system files !!!

Restore the defaults :

```
sudo chown root.root /etc/sudoers

sudo chmod 0440 /etc/sudoers
```

To run firestarter user

```
gksu firestarter
```

If it segfaults, you will need to file a bug report.

---

### Post by Theory5 on 2009-10-16
So what should I use to monitor network traffic? and are you saying I shouldnt use firestarter, I should use gufw? And i fixed the problem with sudoers

---

### Post by bodhi.zazen on 2009-10-16
> **Theory5 said:**
> So what should I use to monitor network traffic?\

What are you monitoring your traffic for exactly ?

Most people advise snort, but that is a bit of over kill for most desktop users.

---

### Post by sisco311 on 2009-10-16
> **bodhi.zazen said:**
> What are you monitoring your traffic for exactly ?


good question.  

> **Theory5 said:**
> So what should I use to monitor network traffic? and are you saying I shouldnt use firestarter, I should use gufw? And i fixed the problem with sudoers

why do you need a firewall?

what network services are you running?

---

### Post by Theory5 on 2009-10-16
I am actually trying to harden my distribution to learn how ubuntu functions. I prefer to learn by reading about it then actually doing it rather than just reading about it. I like to learn as much as i can, and I would like to see what is accessing my computer, because i am in a dorm and vnc and other programs from my school have been accessing ports. One of my hobbies is to see how much I can get away with, in this case its more denying connections from programs such as VNC and Samba.
 I need to recompile my kernel anyways to make my touchscreen work again, I might as well try grsecurity or something to harden my computer.

---

