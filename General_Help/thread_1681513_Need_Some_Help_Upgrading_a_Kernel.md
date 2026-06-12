---
title: "Need Some Help Upgrading a Kernel"
date: 2011-02-04
forum: General Help
---

### Post by dh04000 on 2011-02-04
I saw this article on Phoronix: 

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_expanded&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_expanded&num=1)

And I was amazed by the improvement that the Open-Source Driver has made since Maverick!

I'm on Lucid currently, and I plan on staying on Lucid until 12.04. I usually upgrade on *.04 (I've used 8.04, 9.04, 10.04 thus far), but I want the gnome 3 and unity transition to blow over and become stable and awesome before I make the dive.

But this Open Source Ati improvement has me drooling! So.... I have to ask....(I'm a Ati x1400 user)

Is it possible to upgrade Lucid to Kernel 2.6.38? I know that there is certain X.Org requirements for the kernels..... does lucid make the requirement?

Thanks for the assistance, Ubuntu forums!  :)

---

### Post by dh04000 on 2011-02-04
Wait, does the OS Ati driver come within the kernel, or if there a binary I have to install?

---

### Post by dh04000 on 2011-02-04
Would either of these what I'm looking for?

[http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa](http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa)

[http://www.ubuntuupdates.org/packages/show/300888](http://www.ubuntuupdates.org/packages/show/300888)


Also, the newest kernels come with newer Gallium 3D drivers right?

Any post kernel update, Gallium driver installation instructions I need?

EDIT: Just found this: [http://www.phoronix.com/scan.php?page=news_item&px=ODE3Nw](http://www.phoronix.com/scan.php?page=news_item&px=ODE3Nw)

Will this get me the driver I seek?

---

### Post by dh04000 on 2011-02-04
Bump!

---

### Post by davidmohammed on 2011-02-04
some instructions [here]("http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa") how to install the lucid variant of the 2.6.38 kernel - just realised you found these already


just copy and paste the first stuff on that webpage into a terminal

---

### Post by dh04000 on 2011-02-04
Will installing a new kernel get me the driver I want?

I'm from the 'windows way of doing things" crowd. I'm used to binary file installation, I'll got no idea where gallium 3D drivers are found.

---

### Post by davidmohammed on 2011-02-04
and as the phoronix article said - to install the 3D driver - you'll need to install the [edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") 


i.e. 

sudo apt-add-repository ppa:xorg-edgers/ppa

... that is ppa : xorg-edgers/ppa but without the spaces

sudo apt-get update

sudo apt-get upgrade

Note the very big health warning - read the edgers link above and understand the stuff that can go wrong - as well as how you can use ppa-purge to rescue yourself.

---

### Post by dh04000 on 2011-02-04
> **davidmohammed said:**
> and as the phoronix article said - to install the 3D driver - you'll need to install the [edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") 


i.e. 

sudo apt-add-repository ppa:xorg-edgers/ppa

... that is ppa : xorg-edgers/ppa but without the spaces

sudo apt-get update

sudo apt-get upgrade

Note the very big health warning - read the edgers link above and understand the stuff that can go wrong - as well as how you can use ppa-purge to rescue yourself.



That sounds bad, I'll make sure to read it before installation, thanks for the help.  :)

---

