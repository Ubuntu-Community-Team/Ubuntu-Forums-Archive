---
title: "No Results in Software Center"
date: 2012-02-15
forum: General Help
---

### Post by h4pless on 2012-02-15
I just got Ubuntu up and running yesterday after a lengthy installation process and now I seem to be having issues with the Ubuntu Software Center. Regardless of what I search for all that comes up is an unhappy face with no text. I have checked the software sources and and all the options on the "Ubuntu Software" and "Other Software" tabs are checked. I have also tried running "sudo apt-get update" from the terminal just to see if that would do anything but so far, no luck. 

The front page of the software center does load correctly but if I try to install anything from the front page, I get a "Internal Error" page that mentions "No network connection." The wifi connection is functioning properly as I am using it to post this question but the Software Center doesn't seem to be able to utilize it. I should also probably note that there are no results even when searching for a program that is already installed on the system and that the Update Manager has run without issue... I'm new to Linux and am very lost at the moment, any advice would be greatly appreciated. Thanks.

---

### Post by jerrrys on 2012-02-16
Try this:

Open a terminal

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

and enter:

sudo apt-get update

Will that produce any errors?  USW by chance work?

---

### Post by forrestcupp on 2012-02-16
> **jerrrys said:**
> Try this:

sudo apt-get update


He said he already did that and didn't have any luck.

Obviously, you're wireless is working if you're on the internet like you said. Have you tried installing an app with **sudo apt-get install** from the command line? If you can install things with the command line, then it is probably only a problem with the Ubuntu Software Center. If that's the case, you could try this from the terminal:
```
sudo dpkg-reconfigure software-center
```

If that doesn't work and you can install things from the command line, you could temporarily use Synaptic until you get it working. **sudo apt-get install synaptic**

---

### Post by jerrrys on 2012-02-16
crap, managed to miss that

---

