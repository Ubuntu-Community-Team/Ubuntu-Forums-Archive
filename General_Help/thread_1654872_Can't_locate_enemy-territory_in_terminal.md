---
title: "Can't locate enemy-territory in terminal?"
date: 2010-12-29
forum: General Help
---

### Post by TheNerdAL on 2010-12-29
I have an issue trying to install True Combat: Elite.

I followed these steps: [http://ubuntuforums.org/showpost.php?p=10063534&postcount=4](http://ubuntuforums.org/showpost.php?p=10063534&postcount=4) 

But when I do the 4th step, I get this.

```
E: Unable to locate package enemy-territory

```

Can anyone help?

Thanks.

---

### Post by iball8888 on 2010-12-29
Is this any help to ya?

[http://www.playdeb.net/software/Enemy%20Territory](http://www.playdeb.net/software/Enemy%20Territory)

---

### Post by TheNerdAL on 2010-12-29
> **iball8888 said:**
> Is this any help to ya?

[http://www.playdeb.net/software/Enemy%20Territory](http://www.playdeb.net/software/Enemy%20Territory)

Doesn't work. 

[IMG]http://i.imgur.com/ux0FM.png[/IMG]

---

### Post by TheNerdAL on 2010-12-29
Some people helped me solve it on another site. 

Here it is just in case anyone needs it:

> It seems my problems were caused by old playdeb repositories that were disabled when I upgraded to 10.10.

The solution was to:

make sure ubuntu software center is closed and remove playdeb package via synaptic

Open up Synaptic (by going to System &#8594; Administration &#8594; Synaptic Package Manager)
Search for "playdeb" and select "mark for complete removal"
Apply the changes and close synaptic
Install the playdeb package again

update and install the game via the terminal.

sudo apt-get update
sudo apt-get install enemy-territory
I also removed all the old playdeb repositories from the software sources by opening the software center, going to Edit &#8594; Software-Sources &#8594; Other Software and removing the disabled entries.

Here's the link if you need it: [http://askubuntu.com/questions/19196/cant-locate-enemy-territory-in-terminal](http://askubuntu.com/questions/19196/cant-locate-enemy-territory-in-terminal)

---

