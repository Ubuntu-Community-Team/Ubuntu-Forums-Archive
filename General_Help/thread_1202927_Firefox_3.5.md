---
title: "Firefox 3.5"
date: 2009-07-02
forum: General Help
---

### Post by Adavur on 2009-07-02
Well, not so long ago Mozilla released Firefox version 3.5.

I use Ubuntu 9.04 Jaunty, but I don't understand why I've not been asked to upgrade my Firefox (which is 3.0.11)!?

I can't press the "check for updates" button. Shouldn't it tell me it self? You know, I'd like to do update through the update manager instead of downloading a file and install a "new" Firefox version from Mozilla's homepage...

Mathias

---

### Post by synapsys on 2009-07-02
When the new firefox is compatible and secure within ubuntu, it will be added to the repo's. Be patient.

---

### Post by tyblogger5 on 2009-07-02
Firefox 3.5 has not been certified by the Ubuntu team yet.  But if you want to get it now, you can use the following command to get Firefox 3.5:

```
wget -O - http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2 | tar xj -C ~
```

This code is from [Lifehacker]("http://lifehacker.com/5306169/install-firefox-35-on-ubuntu-with-one-command"), check it out.;)

-tyblogger5

---

### Post by Adavur on 2009-07-02
Thx for very quick answers ;). It's not that I'm impatient, I just didn't understand. I will try the code. :)

But do you think it will be added before the Karmic Koala arrives?

---

### Post by maheshasolkar on 2009-07-02
> **tyblogger5 said:**
> Firefox 3.5 has not been certified by the Ubuntu team yet.  But if you want to get it now, you can use the following command to get Firefox 3.5:

```
wget -O - http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2 | tar xj -C ~
```

This code is from [Lifehacker]("http://lifehacker.com/5306169/install-firefox-35-on-ubuntu-with-one-command"), check it out.;)

-tyblogger5

Both Lifehacker and tyblogger5 failed to mention a tiny detail that may leave an inexperienced user wondering why Firefox 3.0.* starts even after installing Firefox 3.5 with the above command.

After you install Firefox with the above command, invoke it like this:

```
  % ~/firefox/firefox
```

The reference cited by Lifehacker is more complete:

  [http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/](http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/)

---

