---
title: "Where/how to file enhancemnt suggestion for Empathy?"
date: 2010-02-03
forum: General Help
---

### Post by AldenIsZen on 2010-02-03
I believe that Ubuntu's core mission directly relies on usability. What made Windows successful to begin with was that it was "easier" than DOS for the masses. Now do not get me wrong, I love learning new things. However, there are those that just will not, for whatever reason. IMHO, mostly scared to screwup and have no confidence in themselves. Perhaps as Ubuntu and Linux get "easier" people will step into the wild and free side as I have.

 Anyhow, I have an enhancement that I would like to get to the developers of Empathy. Since it is the default IM client for Ubuntu, I think it is important to have certain things easy or the default. In this case, making Empathy come on on startup and option to be hidden. This is the information age, and if you use messenger, you probably do not want to have to turn it on as much as you may occasionally turn it off. It may be a small thing, but it is important I feel for many reasons. Communication is key to any relationship, even for enemies! (Ha!) 

 So, anyone have any idea where exactly would be the best place to get this discussed? It appears that Empathy is not tracking bugs via Launchpad. I think there may be a section in Gnome since it is integrated, but is that the best place. Should I look toward Empathy themselves, or maybe even Ubuntu developers?

 Thanks for taking the time to read and any input!

 PS: if you are interested, here are the commands to do this yourself. (But I am looking to have it added as an option(s).)

Via a console enter in each line separately, you will need to confirm your password:
```
sudo cp /usr/share/applications/empathy.desktop /etc/xdg/autostart
sudo chmod a+r /etc/xdg/autostart/empathy.desktop

```If yould like to have Empathy on at startup, but also hidden until you launch it, navigate to System>Preferences>Startup Applications. Next select to "Empathy IM Client' and click edit. In the Co_m_mand field add -h at the end to change to: ```
empathy -h
```Source: [http://demmer.ipax.at/blog/ubuntu-autostart-for-empathy-im-client/](http://demmer.ipax.at/blog/ubuntu-autostart-for-empathy-im-client/)

PPS: Yes, I am looking to learn how to program, but I still need to know the best ways to approach situations such as this.

---

