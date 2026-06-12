---
title: "Is it advisable to change the Distribution name?"
date: 2009-12-17
forum: General Help
---

### Post by gosalia on 2009-12-17
Look I know many people are going to go on about how Ubuntu is great and that I should not change it, and that I should give back to a community who gave me so much! Well here is what I have to say to them before I start anything - 

Ubuntu is awesome! I love Ubuntu, and so I have decided to spread my experience (as selfless as I hope I am) to all my friends next year. I plan on creating a variant (hardly known as a distribution) for my friends to suit their purposes. This variant patches up all Ubuntu's errors or the few bugs inside the distribution. It also has many customized features for my friends who will love to saw, "good-bye" to windows!

And so, I have decided to customize a lot of Ubuntu to say my Distribution's things. Such as, logo, themes, Internet, connections, kernel version, speed, data, source files etc. These were all essential for my customizations and improvements on Ubuntu 9.10.

Now I have faced the biggest hurdle I believe. I have found out the source file that will enable me to change the Operating System name (i.e Ubuntu). This file is located in etc

The files are called issue and lsb-release

If both of these files are changed to your customized name. But here comes my question - is it advisable to change the name? I mean I don't want any programs to stop working (well at least not programs that are important, insignificant programs don't matter).

So all I am asking is for someone to check it out on a safe computer or someone who has already done this to please tell me if it is safe and what I may be risking if I do so. Thank you all, and thank you Ubuntu community. Your feedback and your queries have made a budding technology wiz out of me. :KS

---

### Post by EricDrijv on 2009-12-18
Just install a test version inside a virtual box. Take it for a spin and see if everything works. :guitar:

---

### Post by 3rdalbum on 2009-12-18
Every distribution differs slightly in how the "front end" of the system interacts with the "back end". A different distribution might store files in a different location, for instance.

If you change the lsb-release data to read Fedora (for instance), some of your system administration programs will no longer work. If you change the lsb-release data to something that the programs won't recognise, they will bring up a dialog every time they start, asking you to choose what distribution you are using or the closest equivilant.

I tried changing it a while back when I was creating my Copland distro, but the inconvenience for the user caused me to change it back. Unless you can get your new distro name accepted upstream in Gnome, you shouldn't change it.

---

### Post by clicker4721 on 2009-12-18
I think I'll have to agree with EricDirjv--a virtual machine sounds like the best idea. [VirtaulBox OSE ]("http://virtualbox.org")is the most popular.

---

### Post by gosalia on 2009-12-18
> **clicker4721 said:**
> I think I'll have to agree with EricDirjv--a virtual machine sounds like the best idea. [VirtaulBox OSE ]("http://virtualbox.org")is the most popular.


Thank you everyone who responded. And thankyou for giving my advice from yoru past experience. I just have one question.

Can someone tell me the programs that will be affected if I change the distribution name to something else, and if it is possible, can I change the distribution details or discribtion? i.e in lbs can I change the things below Ubuntu? Please answer ASAP.

Thank you so much for your feedback and I am going to test it out soon...:KS

---

