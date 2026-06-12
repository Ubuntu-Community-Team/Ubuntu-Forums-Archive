---
title: "apt-get is stuck"
date: 2010-10-11
forum: General Help
---

### Post by Quackers on 2010-10-11
I was trying to install virtualbox with this command from the VB website 
sudo apt-get install virtualbox-3.2
it was running fine then it gave me an option to install a new version of a vbox file or keep the old one or press a key to show the differences between the two. I pressed that key and it showed the differences (a bit) and then I could not proceed with the install. I tried going back, forwards, esc, exit and everything I could think of. Nothing worked so I closed the terminal down. Now synaptic won't open and apt-get purge won't do anything. It says E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
to everything I try.
I think it's stuck - I messed it up :(
How can I get things back to normal? Any ideas would be good. I presume shutting down would be a bad thing :-)
Thanks

---

### Post by Quackers on 2010-10-11
And the answer is sudo killall apt-get
then sudo dpkg --configure -a
which then got me back to where the process stopped earlier. I could then enter the key to carry on and it finished installing. 
Google came in handy (I think it was page 24 :-) )

---

