---
title: "This is my first time with linux please help."
date: 2009-10-29
forum: General Help
---

### Post by gold5225 on 2009-10-29
I just installed ubuntu linux 8.10 and i am installing 9 as i type. I have been unable to connect to my wifi from my netbook that i installed linux. I also havent been able to install flash. 

So obviously these are pretty n00bish things to ask but i used to use just windows so any help would be appritiated. I tried google but i dont yet know how to use scripting or the terminal..

Im actually not sure what version of ubuntu it is i didnt mean to pick nome.

---

### Post by Giblet5 on 2009-10-29
8.10 may be a bad choice for a newer netbook, since it may not have device support for your hardware.

9.10 will probably work right away.

Once 9.10 is installed, if you click on the networks icon near the upper right corner, you should be able to see what wifi networks were detected. 

Select one to connect to it.

If you still have trouble, post back with your netbook model number.

---

### Post by gold5225 on 2009-10-29
oh alright thanks i will try that then.

---

### Post by JC Cheloven on 2009-10-29
There is no reason to install 8.10 by now. There are good chances that your wireless problems disappear if you install 9.04.

Today 9.10 is released, you could also bet for that one, although it's a bit risky to embrace a new release before some 2 or 3 weeks.

As for flash, simply install the adobe-flash-plugin from synaptic. That's it.

---

### Post by gold5225 on 2009-10-29
i had a old dvd from burning ubuntu on it last year and i didnt think to download a new iso.

---

### Post by P4man on 2009-10-29
> **gold5225 said:**
> I just installed ubuntu linux 8.10 and i am installing 9 as i type. I have been unable to connect to my wifi from my netbook that i installed linux. I also havent been able to install flash. 


Very often this question is asked because people havent figured out how to use the network manager. If you right click on the network manager icon (top right), do you see an option "enable wireless" ? If you do, then enable it if its not enabled, and then left click the same icon to chose an access point.

Its possible your wifi card is not recognized out of the box, but lets make sure thats actually the case before digging deeper.

If you tried 9.10 and your network card actually does not work, then open a terminal in applications > accessories > terminal. And type:

```
lspci
```
(that is LSPCi in lowercase)

Copy paste the output here so we know exactly which network card you have.

---

### Post by dhavalbbhatt on 2009-10-29
> **gold5225 said:**
> i had a old dvd from burning ubuntu on it last year and i didnt think to download a new iso.

Do you only have one computer from where you can download (and that computer would be your netbook, which you obviously can't use right now) - or do you have another machine from where you can download 9.10? If you do, I would suggest you download 9.10 for netbooks - Ubuntu 9.10 Netbook Remix - that is specifically designed for netbooks, instead of the desktop version of the OS.

---

