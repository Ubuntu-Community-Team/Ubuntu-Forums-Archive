---
title: "Server/Desktop newbs."
date: 2011-02-24
forum: General Help
---

### Post by xpstyle36 on 2011-02-24
Hi guys, first of all, i'm not sure if this is in the right place but im sure there will be someone here that can help me :)

Basically I am 17 years of age and I am in a I.T Apprentiship and am trying something new. I was always a fan of Ubuntu and i run it wherever i can, and if i had the knowledge i would have the whole company running it, server and client, as this would save alot of money and i could get rid of the damn killing effect that Windows seems to have on PC's, it just slows them down :(

Anyway, i have an old server here, and i mean it is DAMN old, like it has a pentium3 and is about 10 years old, but unfortunately that is all i have at my disposal to do my little project. I know you are all going to tell me that i should not have a GUI installed on a server because it compromises the security of the Server, but there is no way on earth that i am going to be able to set-up the server without one, as i am not at all skilled enough with the CL to go without a GUI. I have installed Ubuntu Sever and then i did a sudo apt-get install ubuntu-desktop and i now have a GUI, BUT because there is no GPU in this old piece of **** the GUI is so so slow, and i know this is because it is designed for a desktop machine with a GPU, all i wanted to know is, is there a GUI i can install that is really light weight and what tools do i need to install to make this a File Server and allow windows clients to grab files from it. Samba i have and i can most likely figure it out on my own, but i do need some help getting a GUI that doesn't lag like a biznetch :)

Thanks for any help in advanced.

Dane.

---

### Post by zenwalker on 2011-02-24
LXDE, XFCE, Fluxbox are light weight DEs for the linux distros.

Also, you need to customize the server distro to suite your machine. I can suggest you zenwalk since your machine is such an old one. Zenwalk is designed to work on very old machine. Check my signature for the link.

P.S: I am not advertising Zenwalk here. Just for you to try beside ubuntu. Then you can opt for yourself which one is best.

---

### Post by sanderd17 on 2011-02-24
you should have installed the lubuntu-desktop instead of ubuntu-desktop. Lubuntu is a light environment which might work on that system.

---

### Post by xpstyle36 on 2011-02-24
> **zenwalker said:**
> LXDE, XFCE, Fluxbox are light weight DEs for the linux distros.

Also, you need to customize the server distro to suite your machine. I can suggest you zenwalk since your machine is such an old one. Zenwalk is designed to work on very old machine. Check my signature for the link.

P.S: I am not advertising Zenwalk here. Just for you to try beside ubuntu. Then you can opt for yourself which one is best.

Hey! Thanks for the super fast response, i will grab a copy of Zenwalk and install it, i'm guessing it is a Distro not a DE.

Edit: Being stupid and not checking the website before making that comment! Wait, I dont have to buy it do i? And what kind of tools will i need to make this work as a NAS(Network Attached Storage) box.

---

### Post by zenwalker on 2011-02-24
> **xpstyle36 said:**
> Hey! Thanks for the super fast response, i will grab a copy of Zenwalk and install it, i'm guessing it is a Distro not a DE.

Edit: Being stupid and not checking the website before making that comment!

Youll know when you visit its home page.

---

### Post by xpstyle36 on 2011-02-24
> **zenwalker said:**
> Youll know when you visit its home page.

Got it :D Only have to pay if i want a CD, ok :) 

What about the tools, what will i need to grab? And is it Debian based?

Thanks Dane.

---

### Post by xpstyle36 on 2011-02-24
> **sanderd17 said:**
> you should have installed the lubuntu-desktop instead of ubuntu-desktop. Lubuntu is a light environment which might work on that system.

Thanks for that, I will give that a go too. 

Thanks, Dane.

---

### Post by zenwalker on 2011-02-24
Its slackware based. I suggest you to take a moment of your time please and read about it at the home page. 

Tools depends on what type you choose. If you choose server edition, it all comes up with it. Also for help you can take a look at wiki.zenwalk.org

---

### Post by xpstyle36 on 2011-02-24
> **zenwalker said:**
> Its slackware based. I suggest you to take a moment of your time please and read about it at the home page. 

Tools depends on what type you choose. If you choose server edition, it all comes up with it. Also for help you can take a look at wiki.zenwalk.org

I am reading about it now :)

But i can see the 5 types of Zenwalk but there is no Server Edition on that list.

---

### Post by zenwalker on 2011-02-24
This should tell you some thing ? [http://www.zenwalk.org/modules/tinycontent/index.php?id=32](http://www.zenwalk.org/modules/tinycontent/index.php?id=32)

---

### Post by xpstyle36 on 2011-02-24
> **zenwalker said:**
> This should tell you some thing ? [http://www.zenwalk.org/modules/tinycontent/index.php?id=32](http://www.zenwalk.org/modules/tinycontent/index.php?id=32)

But i want a GUI. I cannot do this without any X features. I am not good enough with the Command Line.

Thanks.
Dane.

---

### Post by zenwalker on 2011-02-24
Just install that and then when you log into the system, do netpkg xfce xorg
Youll get all the GUI. But please rem, your loading up your server.
This should also help you [http://wiki.zenwalk.org/index.php?title=Install_a_minimal_GUI_on_top_of_Zenwalk_Core](http://wiki.zenwalk.org/index.php?title=Install_a_minimal_GUI_on_top_of_Zenwalk_Core)

---

### Post by zenwalker on 2011-02-24
Btw any more info needed about zenwalk, please read zenwalk wiki or go to zenwalk forums. Lets not discuss that here.

---

### Post by xpstyle36 on 2011-02-24
> **zenwalker said:**
> Btw any more info needed about zenwalk, please read zenwalk wiki or go to zenwalk forums. Lets not discuss that here.

Oh thanks, i was trying to use Ubuntu, but I will have a look at Zenwalk, i know my depth with Debian and think I will try and find an solution within ubuntu first. But thankyou for all your help, it is much appreciated.

---

