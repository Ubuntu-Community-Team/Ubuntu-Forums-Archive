---
title: "How can I fix my usplash?"
date: 2011-03-07
forum: General Help
---

### Post by Juma92 on 2011-03-07
I was trying to change the ubuntu splash screen and found a guide that told me to uninstall usplash and install splashy. So in terminal I typed:

```
sudo apt-get autoremove usplash
```

then installed splashy, but after having some trouble with it I uninstalled splashy and reinstalled usplash by typing

```
sudo apt-get install usplash
```

The problem Im having is that the plymouth dependency is not getting installed because its not getting authenticated or something and gives me an error in console. Afterwards the Ubuntu software manager comes up and tells me to repair it but when I do it tells me it has failed because its not authenticated.

Anyways after restarting my laptop I am no longer able to boot into Ubuntu. After getting the Grub to load and choosing Ubuntu a message pops up saying my graphics are too low or something and gives me the ability to run ubuntu in low graphics mode or restarting x. Regardless of which option I choose it hangs on the Ubuntu splash screen and does nothing. If I choose recovery then through console only mode I am able to log into my ubuntu account, from which I was successfully able to remove usplash altogether but I can get it to install correctly with out the plymouth dependency authenticating properly.

Sorry for the long post, trying to be as detailed as possible. Any help would be appreciated. Im running Ubuntu 10.10

---

### Post by Juma92 on 2011-03-07
can anyone help me?

---

### Post by wojox on 2011-03-07
Get into a terminal or command prompt and run:

```
sudo update-initramfs -u
```

---

### Post by Juma92 on 2011-03-07
It didn't work, I logged into my Ubuntu account through recovery mode and did as you instructed but when I restarted my laptop and booted into the normal mode I got the same message: Ubuntu is running in low graphics mode.

I went back into recovery mode and chose the option to repair my packages and this came up:

[IMG]http://i.imgur.com/EAdQK.jpg[/IMG]

---

### Post by wojox on 2011-03-07
Did you commit to the fixing of broken packages?

---

### Post by Juma92 on 2011-03-07
Yes but that did nothing, after restarting and going into recovery mode the same thing came up...

Is there any way I can just boot from the LiveCD and reinstall that specific part?

---

### Post by Juma92 on 2011-03-09
Im still having trouble if anyone could help me out, it would be great.

---

### Post by lithopsian on 2011-03-09
Plymouth dependency?  I'd like to see that message.  usplash and plymouth don't go together.  Remove usplash again and see exactly what that message says.  Are you sure you had usplash before you started?

---

### Post by wojox on 2011-03-09
> **Juma92 said:**
> Im still having trouble if anyone could help me out, it would be great.

What errors does it give you know?

---

### Post by Juma92 on 2011-03-10
Ok so here is a step by step of everything that occurs and the errors reported:

Booting into Ubuntu normally I'm greeted with [COLOR="Red"][this.]("http://i.imgur.com/TpLZn.jpg")[/COLOR] After clicking ok I then get [this menu to choose from.]("http://i.imgur.com/x5w7F.jpg") If go under trouble shoot and I look at the [error log I can see this]("http://i.imgur.com/2Fvsi.jpg") (not sure if thats helpful). Back at the menu if I choose and of the other options Im greeted by [this]("http://i.imgur.com/KJGCJ.jpg") dialog box and it just returns me to the [Ubuntu splash screen]("http://i.imgur.com/efZb0.jpg") and hangs there forever. If I press [F1] [I see this.]("http://i.imgur.com/yi22B.jpg")

Now restarting the laptop and [loading grub]("http://i.imgur.com/3TCwt.jpg") I chose to enter into Ubuntu's recovery mode which brings me to [this.]("http://i.imgur.com/sEv87.jpg") At first I chose dpkg and let it fix my packages but that just gives me [this prompt]("http://i.imgur.com/plaiM.jpg") and upon agreeing Im given [another prompt]("http://i.imgur.com/qfe11.jpg") that leads to nowhere. Instead I get [a bunch of errors]("http://i.imgur.com/quFWF.jpg") and get sent back to the [recovery menu.]("http://i.imgur.com/sEv87.jpg") Back at the recovery menu I booted into Ubuntu console mode and [tried to reinstall usplash]("http://i.imgur.com/tXzrt.jpg") and that where I first see the [plymouth dependency error.]("http://i.imgur.com/sgv2y.jpg")

Ive posted pictures to everything Ive detailed in this, just mouse over the text to see them.

---

### Post by Juma92 on 2011-03-11
Please help me I havent been able to log into my Ubuntu for a few days now.

---

