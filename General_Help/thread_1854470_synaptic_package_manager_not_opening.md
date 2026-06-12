---
title: "synaptic package manager not opening"
date: 2011-10-04
forum: General Help
---

### Post by naikmanoj1991 on 2011-10-04
i m using ubuntu 11.10..when i try to launch the synaptic manager its not opening without showing any error...
after running  **gksudo synaptic** from a terminal
following output is displayed
[B]manoj@Manoj:~$ gksudo synaptic
  what():  vector::_M_range_check
 instance of 'std:: out_of_range'[/B]

what is this??

---

### Post by mikewhatever on 2011-10-04
Synaptic is not included in the default 11.10. Have you installed it manually?

---

### Post by ajsoulmate on 2011-10-04
> **mikewhatever said:**
> Synaptic is not included in the default 11.10. Have you installed it manually?

Not included? then how can I install programs if I don't want to use the terminal?

---

### Post by drs305 on 2011-10-04
EDIT: See Post #10 OR #22 for the solution for most users.


You can manually add it via command line (sudo apt-get install synaptic) or the Ubuntu Software Center. Make sure the 'universe' repository is enabled if you can't install it.

---

### Post by mikewhatever on 2011-10-04
Use the Software Center. I suppose you can also install Synaptic, if you haven't done so yet.

---

### Post by naikmanoj1991 on 2011-10-07
ya i was install it manually...

---

### Post by naikmanoj1991 on 2011-10-07
> **mikewhatever said:**
> Synaptic is not included in the default 11.10. Have you installed it manually?

ya i was install it manually.....

---

### Post by JoZ3 on 2011-10-11
> **naikmanoj1991 said:**
> i m using ubuntu 11.10..when i try to launch the synaptic manager its not opening without showing any error...
after running  **gksudo synaptic** from a terminal
following output is displayed
[B]manoj@Manoj:~$ gksudo synaptic
  what():  vector::_M_range_check
 instance of 'std:: out_of_range'[/B]

what is this??

Any solution for this error?

---

### Post by alessa_126 on 2011-10-14
I have the same exact error while trying to open synaptic on Ubuntu 11.10 I have a network user with administration privileges and Gnome 3 Desktop.

I have installed synaptic:
>sudo apt-get install synaptic
I have tried starting synaptic on both command line and in the menu panel but without success:
>gksudo synaptic
>sudo synaptic

I even tried to re-install synaptic:
>sudo apt-get remove --purge synaptic

When I switch to a local user with administrator privileges I have a different icon in the menu panel and I am able to start synaptic. I have no clue if the problem is related with privileges for displaying graphical applications for administration use. 

Ale

---

### Post by jasonwco on 2011-10-14
There is a bug for this at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219).

It appears that it's related to accessibility settings.  I was able to fix this problem on my system by opening Universal Access, enabling then disabling the screen reader, then opening Synaptic again.

---

### Post by leilton on 2011-10-14
> **mikewhatever said:**
> Synaptic is not included in the default 11.10. Have you installed it manually?

Am I allowed to add here that I have Ubuntu 10.2 and yes it includes Synaptic, or did until I got the message

:

Quick update, solved it by using repair broken package.
:oops:

---

### Post by pgn674 on 2011-10-15
> **jasonwco said:**
> I was able to fix this problem on my system by opening Universal Access, enabling then disabling the screen reader, then opening Synaptic again.I just upgraded to 11.10 from 11.04, and Synaptic broke for me like it did for the OP. This fixed it, thank you.

---

### Post by JoZ3 on 2011-10-15
> **jasonwco said:**
> There is a bug for this at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219).

It appears that it's related to accessibility settings.  I was able to fix this problem on my system by opening Universal Access, enabling then disabling the screen reader, then opening Synaptic again.

WOW thanks so much, work for me :)

---

### Post by manlypain on 2011-10-15
> **jasonwco said:**
> There is a bug for this at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219).

It appears that it's related to accessibility settings.  I was able to fix this problem on my system by opening Universal Access, enabling then disabling the screen reader, then opening Synaptic again.

This also fixed it for me.  Thanks a ton.  How did you figure that out?

---

### Post by beefiron on 2011-10-16
Just wanted to echo what the others said. This solution worked for me - much kudos.

---

### Post by alessa_126 on 2011-10-17
It worked for me,

Thanks Ale

---

### Post by ajsoulmate on 2011-10-17
&#1616;And it's work for me too :)
Thank you a lot ..

---

### Post by syed.rakib.al.hasan on 2011-10-19
> **jasonwco said:**
> I was able to fix this problem on my system by opening Universal Access, enabling then disabling the screen reader, then opening Synaptic again.

What fruits!!!!! this worked for me. Thank you.

---

### Post by strifesephiroth on 2011-10-20
It worked for me too, thanks! :biggrin:

---

### Post by waznot on 2011-10-27
Brilliant! How did you know to do that?  :P:P

---

### Post by jamil.farooq@hotmail.com on 2011-10-28
> **jasonwco said:**
> There is a bug for this at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219).

It appears that it's related to accessibility settings.  I was able to fix this problem on my system by opening Universal Access, enabling then disabling the screen reader, then opening Synaptic again.

wow man how did you knw tht ??? it works for me :D. but finds no connection :(

---

### Post by jasmines on 2011-11-04
Try:

```
gsettings set org.gnome.desktop.interface toolkit-accessibility false
```

It worked for me.

---

### Post by divajsz on 2011-11-07
synaptic
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Interrupted



the universal access stuff is already switched off, and it is just keeps crashing. Any other way to get synaptic work?

---

### Post by charo on 2011-11-07
> **jasonwco said:**
> There is a bug for this at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219).

It appears that it's related to accessibility settings.  I was able to fix this problem on my system by opening Universal Access, enabling then disabling the screen reader, then opening Synaptic again.

Yes, now I remember: I had this problem already with synaptic and switched it off via universal access. Now again the problem appaered I didn't remember how to solve it.
So thanks for the tip. It worked.

---

### Post by gifford on 2011-11-18
The opening then closing of the screen reader worked for me. I'm amazed! Thanks for the help!!

---

### Post by leeper69 on 2011-12-06
Hi I am using Ubuntu precise amd64 with Gnome,Gnome classic,KDE, and Ubuntu desktops. (after loading the Ubuntu cd I downloaded the full Gnome desktop and the full KDE desktop.) I have ben able to get synaptic to show up in Gnome classic by using the gksu synaptic command in the terminal, and then changing the command in my menu to gksu synaptic. but I was having problems with a broken install after using it. I used the following commands in the terminal to fix this. 
sudo apt-get update
sudo apt-get dist-upgrade -f
sudo apt-get clean
now synaptic is working fine.I also use the muon software center which works as well.

---

### Post by danielszabo1981 on 2012-03-07
> **jasmines said:**
> Try:

```
gsettings set org.gnome.desktop.interface toolkit-accessibility false
```

It worked for me.


This did it for me.  (Ubuntu 11.1) Thank you!

---

### Post by amont on 2012-04-03
Also worked for me. Thanks a lot. (I refer to #10 message)

---

### Post by Randymanme on 2012-05-11
> **jasonwco said:**
> There is a bug for this at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219).

It appears that it's related to accessibility settings.  I was able to fix this problem on my system by opening Universal Access, enabling then disabling the screen reader, then opening Synaptic again.

  I've had to revisit google > here several times; usually after enough time has passed for me to forget what I did last time.  Thank you.

---

### Post by patrickjagersten94 on 2012-10-09
hei :P 

i'm new in the ubuntu/linux world.. i'm having this crash problem to..

were should I but this code:     
gsettings set org.gnome.desktop.interface toolkit-accessibility false

---

