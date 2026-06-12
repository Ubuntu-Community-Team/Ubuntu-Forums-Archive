---
title: "Light weight linux destro"
date: 2012-03-19
forum: General Help
---

### Post by sagar_322 on 2012-03-19
Hi all, I want light weight linux distribution for eBox-3350MX unit. Its has 1.2GHz processor and 512mb of ram. I tried with Ubuntu in it but its slow in operation. I want to make divice as dedicated web application server which ll be running Postgre Sql, Java and Winstone Servlet Engine. Any help would be appriciated thanks in advance.

---

### Post by kc1di on 2012-03-19
I have a similar machine and it runs just fine on Lubuntu give it a try.

---

### Post by ajgreeny on 2012-03-19
If it's a server, do you really need a gui?  You could just install the ubuntu server edition.

---

### Post by sagar_322 on 2012-03-19
Yeah. But it makes the system very slow. I need which with bare minimum stuffs in it..

---

### Post by wojox on 2012-03-19
> **sagar_322 said:**
> Yeah. But it makes the system very slow. I need which with bare minimum stuffs in it..

You installed Ubuntu Server Edition and it's still slow?

---

### Post by serbforce on 2012-03-19
I'am using Xubuntu 11.10 atm, and im loving it. Very light weight.

---

### Post by kc1di on 2012-03-19
can't believe the server edition is that slow on that machine.

---

### Post by Paqman on 2012-03-19
> **sagar_322 said:**
> Yeah. But it makes the system very slow. I need which with bare minimum stuffs in it..

It doesn't get much lighter than the [minimal image]("https://help.ubuntu.com/community/Installation/MinimalCD"). Install a bare-bones command line system, then just fire up tasksel and install what you require.

---

### Post by sagar_322 on 2012-03-19
Yup it is slow.. Can anybody suggest anything other Ubuntu and slax..

---

### Post by philinux on 2012-03-19
> **sagar_322 said:**
> Yup it is slow.. Can anybody suggest anything other Ubuntu and slax..

[http://peppermintos.com/](http://peppermintos.com/)

---

### Post by 2F4U on 2012-03-19
> **sagar_322 said:**
> Yup it is slow.. Can anybody suggest anything other Ubuntu and slax..

Debian or Arch Linux with XFCE or LXDE or any other lightweight window manager.

---

### Post by kc1di on 2012-03-19
> **sagar_322 said:**
> Yup it is slow.. Can anybody suggest anything other Ubuntu and slax..

Puppy but it's not that secure
Vector Linux light

Dam small Linux

---

### Post by snowpine on 2012-03-19
Use **top** and figure out *why* it's slow, is my suggestion. :)

---

### Post by claracc on 2012-03-20
Try lubuntu 11.04 or 11.10, this machine has to "fly".

---

### Post by mastablasta on 2012-03-20
seriously? puppy linux for server? Or DSL? are you crazy? DSL even has old and unsecure (unpatched) kernel.
 
Ubuntu server (CLI instalation) requires:
&#8226;300 MHz x86 processor 
&#8226;128 MiB of system memory (RAM) 
&#8226;1 GB of disk space 
&#8226;Graphics card and monitor capable of 640x480 
&#8226;CD drive (optional)
 
now then, your computer is more than capable to handle it. the question is why are you installing desktop environment on a server? if you only need a GUI interface it would be much more efficient to use a window manager (for example icewm or openbox or one of the others available on the net).

---

### Post by mikewhatever on 2012-03-20
If the Ubuntu server edition is slow on that machine, there is either a major incompatibility, or something is wrong with the computer itself. That said, I strongly suspect that's not the case.

---

### Post by mraandtux on 2012-03-20
For recommended Lightweight distro, Ubuntu-based:Xubuntu, Lubuntu, Bodhi, Puppy; Slackware-based: Salix, Porteus, Zenwalk; And of course Tiny Core.

---

### Post by Paqman on 2012-03-20
> **mraandtux said:**
> For recommended Lightweight distro, Ubuntu-based:Xubuntu, Lubuntu, Bodhi, Puppy; Slackware-based: Salix, Porteus, Zenwalk; And of course Tiny Core.

Folks, the OP is trying to set up a *server*, suggesting alternative DEs isn't going to help.

Install a command line system and then add whatever server packages you require. If you want a GUI environment to administer your server, install [Webmin]("http://www.webmin.com/").

---

### Post by Subidubi32 on 2012-03-20
I heard that Puppy linux runs on older machines softly.. I used a bit Arch linux too, but its installation is a bit complicated.

---

### Post by Subidubi32 on 2012-03-20
* if you want to use GUI... otherwise its simple.

---

### Post by kc1di on 2012-03-20
> **mastablasta said:**
> seriously? puppy linux for server? Or DSL? are you crazy? DSL even has old and unsecure (unpatched) kernel.
 
Ubuntu server (CLI instalation) requires:
•300 MHz x86 processor 
•128 MiB of system memory (RAM) 
•1 GB of disk space 
•Graphics card and monitor capable of 640x480 
•CD drive (optional)
 
now then, your computer is more than capable to handle it. the question is why are you installing desktop environment on a server? if you only need a GUI interface it would be much more efficient to use a window manager (for example icewm or openbox or one of the others available on the net).

well when we suggested ubuntu server edition he said it was very slow.  And I was being a little sarcastic there.  
I have a very similar machine and lubuntu ubuntu server all run fine on it.  So don't know what slowing his down so much
Cheers!

---

### Post by kc1di on 2012-03-22
see on DistroWatch that Vector just released a new Light version that should work for you.  though still think ubuntu server edition should work well on your machine.

---

### Post by sagar_322 on 2012-03-22
I tried installing  lubuntu 11.10 on eBox-3350MX but I am getting error this kernel requires the following features not present on the cpu cmov 
Unable to boot - please use a kernel appropriate for your CPU.
 Any suggestions ...?

---

