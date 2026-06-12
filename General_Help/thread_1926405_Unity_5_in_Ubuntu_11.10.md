---
title: "Unity 5 in Ubuntu 11.10"
date: 2012-02-16
forum: General Help
---

### Post by Canaryguy on 2012-02-16
Hello,

I wanted to try the new version of Unity that is under development for Ubuntu 12.04 LTS. I visited the page [www.omgubuntu.co.uk](www.omgubuntu.co.uk) that explains how to install it. So, it seems that you have to do the following:

    sudo add-apt-repository ppa:unity-team/staging
    sudo apt-get update && sudo apt-get dist-upgrade

    restart computer

After doing that I didn't notice any change. Did I miss something?

---

### Post by Mark Phelps on 2012-02-16
Since this comes with 12.04, you might do better asking this in the Precise Development forum.  There may be some tweaking you have to do to get it working.

---

### Post by ppp102 on 2012-02-22
Hi,
I'm facing the same problem. I did what was told and I have still Unity 4.28. I used synaptic and it seams that there is no Unity 5 for Ubuntu 11.10. Did they change repository or something?

---

### Post by husnos on 2012-02-26
yes. i had the same problem. 

what i did is I installed synaptic after adding the new repository from terminal and searched for unity in synaptic. search results returned unity 4. then i looked into the repositories settings and changed it to distr = "precise". i updated synaptic and now unity 5 appears in the search results. so i closed synaptic and i am going to do dist upgrade

update:
be careful. after a dist upgrade. i can't log in. it brings me back to log in page again. ubuntu is not my main system on my laptop. so i am ok with that. i will try to solve it later when i have time.

---

### Post by Canaryguy on 2012-02-27
The first time I tried it I did it in Ubuntu but now I'm going to try to do it in Linux Mint and I'll have a look at the repositores as you said. Maybe I didn't see the option to change to Precise the last time. Let's see if it let's me log in after the system upgrade.

--
I tried it in Linux Mint but as it happened when I tried in Ubuntu I only could see Unity 4.28 I guess I'll have to wait until the final release of Precise Pangolin to see if version 5 is more stable than version 4. Unity is a good interface but it needs some bugs to be fixed and to improve its features.

---

### Post by philinux on 2012-02-27
> **Canaryguy said:**
> The first time I tried it I did it in Ubuntu but now I'm going to try to do it in Linux Mint and I'll have a look at the repositores as you said. Maybe I didn't see the option to change to Precise the last time. Let's see if it let's me log in after the system upgrade.

Please be aware that the staging ppa now has Unity 5.4 and is for testing in precise. It might break your 11.10 install.

If it breaks remove it. Scroll down for details.
[http://www.omgubuntu.co.uk/2012/01/how-to-install-unity-5-0-in-ubuntu-11-10/](http://www.omgubuntu.co.uk/2012/01/how-to-install-unity-5-0-in-ubuntu-11-10/)

---

