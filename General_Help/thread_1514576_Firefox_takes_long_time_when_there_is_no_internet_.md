---
title: "Firefox takes long time when there is no internet almost 2min"
date: 2010-06-21
forum: General Help
---

### Post by OOzypal on 2010-06-21
Hello,

Firefox take so long more that 2 min when started and there is no internet is available (i.e. Ethernet cable is unplugged). 

I think FF is looking for the connection. How can I make FF ignores this check. 

I need this because sometime I am away from my networks and I need FF for local testing for web development. 

I am using Ubuntu 10.4

Thank you

---

### Post by wojox on 2010-06-21
>  I need FF for local testing for web development.

So will you have access to the internet where you a internet where your going?

---

### Post by OtakuWrath on 2010-06-21
have you tried to Select File and then Work Offline?

---

### Post by OOzypal on 2010-06-21
@wojox
I always have internet in my office but sometimes I am outside in places where there is no internet.

@OtakuWrath

There problem when starting FF. If FF is already started working offline will not make a difference.

Thank you all

---

### Post by wojox on 2010-06-21
> How can I make FF ignores this check. 

Don't use Firefox when you're at home. or plug 
in the Ethernet cable. Follow my wen page and you will see Firefox optimization and troubleshooting thread

---

### Post by SoFl W on 2010-06-21
I am not sure I understand your problem.  Do you have "start with your home page" selected?
Edit-> Preferences -> General, under start up switch "when Firefox starts" to "Show a blank page"

Or start Firefox in offline mode.

I have been offline with my laptop when starting Firefox, it loaded fine, when I tried to serf I would get an error.

---

### Post by lovinglinux on 2010-08-05
You might have an issue with the network manager, because Firefox should detect that the network is offline. Try to set the preference **toolkit.networkmanager.disable** in **about[noparse]:[/noparse]config** to **false**.

I suppose you have some tabs open when you start Firefox. If that is the case, close all tabs before starting or use [BarTab]("https://addons.mozilla.org/en-US/firefox/addon/67651/") to prevent the content from being loaded until you need it.

---

### Post by What Rights on 2010-08-05
You could also set up Prelink and Preload for faster loading.

---

