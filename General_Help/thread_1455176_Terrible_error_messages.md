---
title: "Terrible error messages"
date: 2010-04-15
forum: General Help
---

### Post by bkorb on 2010-04-15
```
# /etc/init.d/networking start
Rather than invoking init scripts through /etc/init.d,
use the service(8) utility, e.g. service networking start

Since the script you are attempting to invoke has been converted...
```
Translation:  I know what you want to do, but I am not
going to do it for you because I want you to ask me in a different way.

I've been bringing up networks with init scripts for 40 years; this new fangled thingey is not especially clever both due to history and due to the fact that not all the world is Ubuntu.  The script ought to be modified to say "there is a better way" and do it the better way for the next several years.  If other distributions pick it up, cool.  If not, then drop it.  Meanwhile:
```
# start networking
networking stop/waiting
```
What in blue blazes does that mean?  I know it is stopped.  That's why I started it.

---

### Post by nixclusive on 2010-04-15
This new fangled thing is called [_upstart_](http://upstart.ubuntu.com/), it is an event based init mechanism and most major distributions have picked up with this already. :) I agree the display messages should be more explanatory.

---

### Post by bkorb on 2010-04-15
So for the next half dozen years, /etc/init.d/whatever should just warn you and then do what you ask for -- certainly until more widely accepted.  I have to fiddle with too many different systems to really want to remember to say things one way on one distro and another way on another.  Gratuitous incompatibilities ought to be avoided.

---

### Post by QIII on 2010-04-15
Cryptic error messages sound fine to developers.  They often make no sense to users.  This should be avoided, and more explanatory messages should be provided.  

As to "standardizing" things across distros...

This is not a community where all things must be done the same way in all cases by all distributors.  That would limit freedom and innovation, which is what this is all about.

---

### Post by bkorb on 2010-04-15
Meanwhile, I am still stuck.  "initctl" (aka "start") is not a script, so I have to rely on it to tell me what is at issue.  It prints out "networking stop/waiting" and calls exit with EXIT_SUCCESS.  Even with -vvvvvvvvvvvvvv on the command line, there is no more information.  Consequently, I cannot just run it with "bash -x /etc/init.d/networking start" and watch it.  /var/log/messages doesn't have anything worthwhile either.  Something is broken and it won't tell me what is wrong.  Anyone know how to diagnose the problem?

---

### Post by QIII on 2010-04-15
The solution is cryptically hidden in the message you got, but obviously  not clear.

What happens when you issue

```
sudo service networking start
```

---

### Post by bkorb on 2010-04-15
The result is an exit code of zero (EXIT_SUCCESS)
and the message:  ```
networking stop/waiting
```
and no entries in /var/log/messages.  Whatever it was waiting for was satisfied when I did an "init 6".  I was trying to avoid rebooting so I could keep context.  Thanks anyway.

I've also worked my way through this to the point where I now know how to read /etc/init/*.conf files so I can play with "ifup" and "ifdown" directly.  thank you all for your feedback.  It helped me wend my way through this!

Regards - Bruce

---

