---
title: "Unable to see captchas"
date: 2011-09-10
forum: General Help
---

### Post by ntesla123 on 2011-09-10
I am trying to register at places like e.g. [http://www.filesonic.com/user/free-signup](http://www.filesonic.com/user/free-signup), but I can't see the human verification captchas.

I have tried firefox, opera and chrome, and I think this is very strange.

---

### Post by haqking on 2011-09-10
> **ntesla123 said:**
> I am trying to register at places like e.g. [http://www.filesonic.com/user/free-signup](http://www.filesonic.com/user/free-signup), but I can't see the human verification captchas.

I have tried firefox, opera and chrome, and I think this is very strange.


I think they use javascript.  Do you have this enabled, and also do you use adbblock or noscript.

if so disable your add-ons and re-enable them one by one until you find out which one is  casuing the problem.

cheers

---

### Post by ntesla123 on 2011-09-10
Javascript is enabled and I don't have addons.

Can there be something else that is causing this?

---

### Post by snip3r8 on 2011-09-10
Try 

```

sudo apt-get install java-common
sudo apt-get install java-wrappers

```

---

### Post by haqking on 2011-09-10
> **ntesla123 said:**
> Javascript is enabled and I don't have addons.

Can there be something else that is causing this?


mmm are you just seeing whitespace ? can you right click on the placeholder and choose show image, or choose to allow images from the source.

I presume images are enabled ?

And also running noscript is a good idea, as it is easy to visit webpages and have scripts run unknowingly ;-)

Possibly firewall related but i doubt it, i know my buddy had issues with symantec in his windows build preventing them.

---

### Post by Duncan Williams on 2011-09-10
some captchas use `flash'


for extensions users.
I need to click once in the captcha space to initialise the flash as I am using an extension `flashblock'

---

### Post by ngupta11 on 2012-01-08
i have a same problem , not displaying captcha when registering for ubuntu one , solve my problem

---

