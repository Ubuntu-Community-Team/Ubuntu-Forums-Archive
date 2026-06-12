---
title: "Moving Ubuntu to a new machine"
date: 2012-01-31
forum: General Help
---

### Post by thomo2710 on 2012-01-31
Hi all,

I have my unbuntu 11.04 machine running and it has Nagios/Curl/Apache/MYSQL and a few other progs on it.

I need to try something that will potentially kill my Ubuntu machine and Nagios and i dont want to be rebuilding it as it takes too long.

So i have a spare machine that i would like to copy my Ubuntu over to but i need it all but identical to the current live machine.

Only issue is it will be moving to new hardware!

Anybody any idea if this is possible? 

I found an article on here that outlines it
[http://ubuntuforums.org/showthread.php?t=525660](http://ubuntuforums.org/showthread.php?t=525660)

But does just copying the folders over actually move the programs accross aswell or will i have to install all the apps again?

Cheers

---

### Post by Matt__ on 2012-01-31
Make a system image or a custom live dvd using Reamstersys. You can use it command line or via its rather minimal GUI. 

[Info on Ubuntu version here]("http://www.geekconnection.org/remastersys/ubuntu.html")

 [download Rematersys]("http://www.geekconnection.org/remastersys/repository/ubuntu/").

---

### Post by Cheesemill on 2012-01-31
The quickest way would be to use Clonezilla and just image the drive to the new machine.

Job done.

---

### Post by thomo2710 on 2012-01-31
@Matt - thanks ill look at that now - my system on a live CD would be the most handyest thing i think ill ever use!

@cheesemill - thanks for the suggestion but i have already tried with Norton Ghost and it does not boot on the other machine, i suspect due to the ahrdware differences. Clonezilla will do the same as Ghost no?

---

### Post by Cheesemill on 2012-01-31
Hardware differences shouldn't be a problem, I have successfully moved an installed system between computers on several occasions without any difficulties.

Unlike Windows which sets up a fixed hardware profile when you first  install it, the Linux kernel automatically probes for hardware on each  boot.

Obviously you cant boot a 64 bit install on 32 bit hardware, but apart from that there should be no problems.

If you are moving from Nvidia graphics to ATI or vice versa just make sure you uninstall the restricted drivers first.

---

### Post by thomo2710 on 2012-01-31
maybe it was just Ghost didnt write the ext file system properly then?

When I booted machine the following came up

blinking curser for approx 1 mintue

then

BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

---

### Post by thomo2710 on 2012-01-31
> **Matt__ said:**
> Make a system image or a custom live dvd using Reamstersys. You can use it command line or via its rather minimal GUI. 

[Info on Ubuntu version here]("http://www.geekconnection.org/remastersys/ubuntu.html")

 [download Rematersys]("http://www.geekconnection.org/remastersys/repository/ubuntu/").

OMG this is the best thing i have ever seen!

Thankyou so much Matt, my ubuntu install is now on 2 seperate machines side by side next to me and i can break them until my heart is content!

---

