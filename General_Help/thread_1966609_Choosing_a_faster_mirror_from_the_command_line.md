---
title: "Choosing a faster mirror from the command line"
date: 2012-04-27
forum: General Help
---

### Post by Anonymouslemming on 2012-04-27
Hi all,

I'm getting really slow package download speeds from my local mirror ([http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)).

I know that you can select faster mirrors using the GUI tools, but this is a slimmed-down server install with no graphical environment installed yet. 

Is there a command-line tool available in current versions of Ubuntu that selects a faster mirror ? 

I read some instructions at [http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line](http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line) about adding the following to the top of my sources.list file:

> 
deb mirror://mirrors.ubuntu.com/mirrors.txt precise main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-updates main restricted universe multiverse


However, even after adding these, my installs still select gb.archive.ubuntu.com as the mirror to use, and I'm still seeing speeds of 22k/s 

Any advice would be much appreciated!

---

### Post by plucky on 2012-04-27
> **Anonymouslemming said:**
> Hi all,

I'm getting really slow package download speeds from my local mirror ([http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)).

I know that you can select faster mirrors using the GUI tools, but this is a slimmed-down server install with no graphical environment installed yet. 

Is there a command-line tool available in current versions of Ubuntu that selects a faster mirror ? 

I read some instructions at [http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line](http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line) about adding the following to the top of my sources.list file:



However, even after adding these, my installs still select gb.archive.ubuntu.com as the mirror to use, and I'm still seeing speeds of 22k/s 

Any advice would be much appreciated!

The lines you added are not actual mirrors.

Be aware that 12.04 has just been released and a lot of the servers will be running slowly as lots of people will be downloading and installing the new version.

So changing the server might not help.It is always like this after a new release.

In the link you quoted there is a line to  update the Sources.list file 
> sed 's/us\.archive\.ubuntu\.com/mirror.math.ucdavis.edu/g' /etc/apt/sources.list

This changes all the lines in the sources.list file and uses the **us** server called **mirror.math.ucdavis.edu**.So you need to know the actual name of the server and in which country it is located.

You can find the names of the servers in **Software Sources** in the button called **Find Best Server**

Good Luck

---

### Post by Anonymouslemming on 2012-04-27
> **plucky said:**
> 

In the link you quoted there is a line to  update the Sources.list file

Yeah, that's now what I'm trying to achieve though - I'm trying to achieve the bit described at [http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror/37754#37754](http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror/37754#37754) , specifically

> apt-get now supports a 'mirror' method that will automatically select a good mirror based on your location. 
...
On the top in your /etc/apt/sources.list file should be all that is needed to make it automatically pick a mirror for you based on your geographical location.





> 
You can find the names of the servers in **Software Sources** in the button called **Find Best Server**

Good Luck

Thanks, but I don't have the GUI installed, so I can't use that. That's what I'm trying to get around...

---

### Post by plucky on 2012-04-27
See [Here](https://launchpad.net/ubuntu/+archivemirrors) for a list of mirrors.Select one an put that into the command.

Good Luck

---

### Post by Anonymouslemming on 2012-04-27
> **plucky said:**
> See [Here](https://launchpad.net/ubuntu/+archivemirrors) for a list of mirrors.Select one an put that into the command.

Good Luck


What command are you talking about here? 

I have a list of mirrors, but I'm trying to find the command-line functionality to update my sources.list with the fastest / most appropriate one.

---

### Post by wojox on 2012-04-27
[Net Select]("http://www.debianadmin.com/howto-select-fastest-mirror-in-debian.html#more-468") is broke?

---

### Post by Anonymouslemming on 2012-04-27
> **wojox said:**
> [Net Select]("http://www.debianadmin.com/howto-select-fastest-mirror-in-debian.html#more-468") is broke?

Can't find it to install it ...

apt-get install netselect-apt has no installation candidate

apt-cache search netselect returns nothing.

---

### Post by wojox on 2012-04-27
> **Anonymouslemming said:**
> Can't find it to install it ...

apt-get install netselect-apt has no installation candidate

apt-cache search netselect returns nothing.

sorry it's been a while. a couple years ago after using archs fastestmirror i was looking for a debian equiv. :P

servers and mirrors wil be slammed for the next week or so.

EDIT: I also just realized you linked to that. Plucky is right it's going to be slow for a week or so.

---

### Post by Anonymouslemming on 2012-04-27
> **wojox said:**
> 

servers and mirrors wil be slammed for the next week or so.

Yeah, I get that... but on a box I own in the US, I'm still seeing around 300K/s. 22K/s is unbearable :) 

tried using the US mirror from the UK box and it is better, but it seems wasteful :)

---

### Post by SeijiSensei on 2012-04-27
> **Anonymouslemming said:**
> tried using the US mirror from the UK box and it is better, but it seems wasteful :)

I've found mirrors at German universities to have pretty fast connections.  

[Ubuntu mirror list](https://launchpad.net/ubuntu/+archivemirrors)

---

