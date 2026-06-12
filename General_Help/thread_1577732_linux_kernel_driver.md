---
title: "linux kernel driver"
date: 2010-09-19
forum: General Help
---

### Post by ArbiterOfTruth on 2010-09-19
Good day,

I downloaded & installed VirtualBox from the home website. I configured it for a Windows XP installation & got to the part where it says it's off. However when I try to start it I get the following error:

[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/driver.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/driver.png)

Where can I download said driver & are there specific instructions for installing it? If there is a thread already dedicated to this topic & I have missed it, I apologize & would ask to be redirected to said thread.

Thanks in advance,
ArbiterOfTruth

---

### Post by Vaphell on 2010-09-19
look for dkms in synaptic

---

### Post by jocko on 2010-09-19
> **ArbiterOfTruth said:**
> Where can I download said driver & are there specific instructions for installing it?
You don't need to download those drivers, they should have been built for you automatically when you installed virtualbox.

Just do what the error message told you to, and you should be fine:
1. Make sure the package "dkms" is installed. Either search for it in synaptic, or run this command in a terminal:
```
sudo apt-get install dkms
```
2. Install the virtualbox kernel driver:
```
sudo /etc/init.d/vboxdrv setup
```
If it doesn't work, post the output you get in the terminal when you run the above command, it will contain information about the reason it failed.

---

### Post by ArbiterOfTruth on 2010-09-19
Good day,

When I used the 1st line shown, I got this:

[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/1st_line.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/1st_line.png)

When I used the 2nd, I got this:

[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/2nd_line.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/2nd_line.png)

I'm not sure where to go from here. Any assistance would be appreciated.


Thanks in advance,
ArbiterOfTruth

---

### Post by jocko on 2010-09-20
First update your package information and install any updates that are available, then try again. Run this in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ArbiterOfTruth on 2010-09-20
It worked! Thanks a lot! 

[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/windows_inside_ubuntu.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/windows_inside_ubuntu.png)

[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/windows_inside_ubuntu2.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/windows_inside_ubuntu2.png)

Hey is there an option to track the threads I start? This was in case someone else has the same problems I can just refer them to the thread.

Thanks again!

---

### Post by jocko on 2010-09-20
> **ArbiterOfTruth said:**
> Hey is there an option to track the threads I start? This was in case someone else has the same problems I can just refer them to the thread.

Thanks again!

Search-->"Find all your threads"

You're welcome!

---

