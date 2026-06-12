---
title: "How to get GeForce GT 555M working?"
date: 2012-06-10
forum: General Help
---

### Post by CC268 on 2012-06-10
I have an Alienware M14x with GeForce GT 555M graphics and am currently running Ubuntu 12.04 LTS and was wondering what is the best way to download the drivers for this card and to get it running properly (if it already isn't)?

---

### Post by Cavsfan on 2012-06-10
You should just be able to go the dash in Unity and enter "driver" It should bring up Additional Drivers.
I chose the 2nd one down the latest which is 295.49.
Install that and reboot and you should be good to go.
I have a Geforce 9800 GT and it works great on that driver.

---

### Post by CC268 on 2012-06-10
> **Cavsfan said:**
> You should just be able to go the dash in Unity and enter "driver" It should bring up Additional Drivers.
I chose the 2nd one down the latest which is 295.49.
Install that and reboot and you should be good to go.
I have a Geforce 9800 GT and it works great on that driver.

When I search for additional drivers nothing pops up

---

### Post by m_duck on 2012-06-10
Does it have dual graphics cards? I.e. an Intel one for normal use, and the NVidia jobby when something more hardcore is required? If that's the case, follow [the Bumblebee article](https://wiki.ubuntu.com/Bumblebee) to get them both working.

With mine (Dell XPS 15z) the "Hardware Drivers" program didn't find anything, which I assume is because as far as it is concerned, it is running of the Intel chip and the NVidia one is not important.

If you do not have dual graphics, I'm not sure.

EDIT: I should say that aside from being a different laptop, mine also has a GT 525M so your mileage may vary.

---

### Post by CC268 on 2012-06-10
> **m_duck said:**
> Does it have dual graphics cards? I.e. an Intel one for normal use, and the NVidia jobby when something more hardcore is required? If that's the case, follow [the Bumblebee article](https://wiki.ubuntu.com/Bumblebee) to get them both working.

With mine (Dell XPS 15z) the "Hardware Drivers" program didn't find anything, which I assume is because as far as it is concerned, it is running of the Intel chip and the NVidia one is not important.

If you do not have dual graphics, I'm not sure.

EDIT: I should say that aside from being a different laptop, mine also has a GT 525M so your mileage may vary.

Yes exactly it has Intel Graphics and the Nvidia card as well...I heard Bumblebee was no longer updated...I will check it out though...I guess I need to get something for Ubuntu that is similar to Speccy for Windows so I can post all my hardware and specs

---

### Post by m_duck on 2012-06-11
As far as I am aware, Bumblebee is the most actively updated Optimus-related project. It's confusing as it has split a couple of times (see "I'm confused about so many projects (MrMEEE/Bumblebee, Ironhide, TBP/Bumblebee). Which one should I install?", [here](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ)).

Bumblebee has worked brilliantly for me when I have used it. It isn't as seamless as in Windows (i.e. it won't automatically run things on the NVidia card) but that also gives you more freedom (though I am aware you can change what Windows runs on a given card).

Once set up, it allows the running of programs on the NVidia card with:```
optirun <program name>
```

---

### Post by idoitprone on 2012-06-11
> **m_duck said:**
> As far as I am aware, Bumblebee is the most actively updated Optimus-related project. It's confusing as it has split a couple of times (see "I'm confused about so many projects (MrMEEE/Bumblebee, Ironhide, TBP/Bumblebee). Which one should I install?", [here]("https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ")).

Bumblebee has worked brilliantly for me when I have used it. It isn't as seamless as in Windows (i.e. it won't automatically run things on the NVidia card) but that also gives you more freedom (though I am aware you can change what Windows runs on a given card).

Once set up, it allows the running of programs on the NVidia card with:```
optirun <program name>
```

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

you should do it the ubuntu way
OP follow the direction in the wiki 

and dont forget to install bbswitch after you intstall bumblebee
bbswitch is the install that will turn off ur card, not bumblebee

```
sudo apt-get install bbswitch
```while your at it you can make the computer turn off the card at boot

```
sudo bash -c 'echo options bbswitch load_state=0 > /etc/modprobe.d/bbswitch.conf'
```

---

### Post by m_duck on 2012-06-11
> **idoitprone said:**
> [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

you should do it the ubuntu way
OP follow the direction in the wiki 

I mentioned the wiki article in my first reply. I was merely mentioning the Bumblebee site as a source to understand the confusion between the different projects.

I'm fairly sure bbswitch is pulled in as a dependency when you install bumblebee from that PPA? Feel free to correct me if I am wrong though.

---

### Post by idoitprone on 2012-06-11
> **m_duck said:**
> I mentioned the wiki article in my first reply. I was merely mentioning the Bumblebee site as a source to understand the confusion between the different projects.

I'm fairly sure bbswitch is pulled in as a dependency when you install bumblebee from that PPA? Feel free to correct me if I am wrong though.


bbswitch and bumble should not depend on each other. If it does, then that developer did something wrong

---

