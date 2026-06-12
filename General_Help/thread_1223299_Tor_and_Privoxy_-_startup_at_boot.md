---
title: "Tor and Privoxy - startup at boot"
date: 2009-07-26
forum: General Help
---

### Post by oakdeveloper on 2009-07-26
Hi All,

I have installed Tor and Privoxy from Synaptic. I find that they both start automatically when the system boots up. Where do I change this setting so that I could start them manually after boot up ?

Regards,
Babu

---

### Post by Captain Giraffe on 2009-07-26
-"I have installed Tor and Privoxy from Synaptic."

Synaptic? go to Tor site instead.

---

### Post by kerry_s on 2009-07-26
> **oakdeveloper said:**
> Hi All,

I have installed Tor and Privoxy from Synaptic. I find that they both start automatically when the system boots up. Where do I change this setting so that I could start them manually after boot up ?

Regards,
Babu

you should have under administration menu, that you can manage the startup programs.

---

### Post by oakdeveloper on 2009-07-26
> **kerry_s said:**
> you should have under administration menu, that you can manage the startup programs.

I could not find them in the Services section in the Administration menu.

---

### Post by grayn0de on 2009-07-26
System > Preferences > Startup Applications

---

### Post by kerry_s on 2009-07-26
> **oakdeveloper said:**
> I could not find them in the Services section in the Administration menu.

you could make the /etc/init.d/tor,privoxy non executable that would stop them. you just have to right click->permission, uncheck allow this program to run.

---

### Post by oakdeveloper on 2009-07-27
> **kerry_s said:**
> you could make the /etc/init.d/tor,privoxy non executable that would stop them. you just have to right click->permission, uncheck allow this program to run.

That's a good hack. I'm ok with the solution but I'm just curious if there is any better solution like dealing with the configuration files where I could select whether the service has to be started at boot.

---

### Post by kerry_s on 2009-07-27
hmm, another way to go about it is to use your /etc/rc.local
just put:

```
[B]/etc/init.d/tor stop &
/etc/init.d/privoxy stop &[/B]
```


also do you know about privoxy's web ui ? a couple of changes in the config file & you can toggle it on/off from the browser, it's off by default for security. 
you'll have to read up on it though, i changed from privoxy to bfilter, cause it's just a whole lot faster & easier, plus i'm only doing adblocking, so i don't remember the privoxy settings.

---

