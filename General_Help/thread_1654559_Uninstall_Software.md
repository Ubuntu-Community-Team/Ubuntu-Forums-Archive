---
title: "Uninstall Software"
date: 2010-12-28
forum: General Help
---

### Post by Metungkp on 2010-12-28
I went ahead and dumped Microsoft all together, so I'm really new to Linux.  No complaints, just a lot to learn and get used to.  First mistake, I downloaded Google Chrome, then I learned that I had to use Ubuntu Software Center and download Chromium.  Now, I need to remove Google Chrome and from what I researched I need to use Terminal.  Please tell me how I can remove Google Chrome using Terminal?

I might as well asked another... As I've stated I completely remove Windows 7 (personal reasons.  I just can no longer support.............).  A friend of mine who uses Ubuntu said I didn't have to back up my documents and that there will be a folder containing the docs once Ubuntu is up and running.  Did he lie to me?  Now, I have to recreate 3 days worth of work...

Thanks!
KP

---

### Post by Metungkp on 2010-12-28
When I was considering my switch to ubuntu the biggest thing that pushed me over to finally switch was that a lot of people mentioned the overwhelming assistance available and quick fast help...

Can a Newbie can some help please?  I just want to remove Google Chrome...

Thanks!
KP

---

### Post by andymorton on 2010-12-28
You should be able to remove it through the synaptic package manager. Type 'Chrome' in to the search box, click on it when it comes up, mark for complete removal and apply. You can find the package manager through System>Administration>Synaptic Package Manager. 

andy

---

### Post by Metungkp on 2010-12-28
> **andymorton said:**
> You should be able to remove it through the synaptic package manager. Type 'Chrome' in to the search box, click on it when it comes up, mark for complete removal and apply. You can find the package manager through System>Administration>Synaptic Package Manager. 

andy

Thanks! Andy.  I actually found a thread that explained how to do it and it was exactly how you are describing:popcorn: it.  It feels like you wrote that one up as well.

---

### Post by thomas144 on 2010-12-28
I agree with Andymorton. You should be able to remove Chromium via the method. If you want to use the Terminal, go to Applications > Accessories > Terminal. Type in **sudo apt-get purge chromium-browser** and hit Enter on your keyboard. You will be asked for your password, type it in and hit Enter.

Regardless of which method you use to remove Chromium, it's generally a good idea to run **sudo apt-get autoremove** in Terminal. What this does is removes all the unused dependencies on your system. In other words, it will remove all the other stuff that Chromium installed in order to run properly that is no longer needed.

P.S. Welcome to Ubuntu. It's a really nice OS. I'm sure you'll like it, and I hope you can get acquainted with it. One great advantage of Ubuntu is that we're here on the forums. Good luck!

---

### Post by andymorton on 2010-12-28
> **Metungkp said:**
> Thanks! Andy.  I actually found a thread that explained how to do it and it was exactly how you are describing:popcorn: it.  It feels like you wrote that one up as well.

You're welcome! I know it can seem a bit daunting when you first start using Linux but after the learning curve things which once seemed difficult and complicated really straight-forward. Welcome to the forums and to Ubuntu!. :D

andy

---

### Post by Metungkp on 2010-12-29
> **thomas144 said:**
> I agree with Andymorton. You should be able to remove Chromium via the method. If you want to use the Terminal, go to Applications > Accessories > Terminal. Type in **sudo apt-get purge chromium-browser** and hit Enter on your keyboard. You will be asked for your password, type it in and hit Enter.

Regardless of which method you use to remove Chromium, it's generally a good idea to run **sudo apt-get autoremove** in Terminal. What this does is removes all the unused dependencies on your system. In other words, it will remove all the other stuff that Chromium installed in order to run properly that is no longer needed.

P.S. Welcome to Ubuntu. It's a really nice OS. I'm sure you'll like it, and I hope you can get acquainted with it. One great advantage of Ubuntu is that we're here on the forums. Good luck!

I like it so far.  It feels hands on... I was actually removing google chrome, so do I type "sudo apt-get purge google chrome-browser"?

---

