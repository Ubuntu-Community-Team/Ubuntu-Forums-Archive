---
title: "Firefox 3 vs 4"
date: 2011-05-26
forum: General Help
---

### Post by bill-lancaster on 2011-05-26
I want to re-install Firefox v3 instead of v4.
I've downloaded v3 files but don't know what to do with them.
I'm using Ubuntu 11

Can anyone help?

---

### Post by lovinglinux on 2011-05-26
See my tutorial [http://www.webgapps.org/tutorials/firefox/general/installing-other-versions](http://www.webgapps.org/tutorials/firefox/general/installing-other-versions)

However, I recommend that you stay with FF 4.

If you could specify the reasons why you are downgrading, we could help you achieve a better experience with FF4.

---

### Post by bill-lancaster on 2011-05-26
I've had trouble using Adobe pdf functions with v4 and read that v4 isn't yet supported by Adobe.

Using v4 a pdf opened in a new tab would show a blank page

---

### Post by lovinglinux on 2011-05-26
I don't use Adobe reader, but  I just tested it and it works with Firefox 4.0.1 on 32bit and 64bit.

Try to clear you browser cache. If that doesn't help, then try a [clean profile]("http://www.webgapps.org/tutorials/firefox/general/profiles-and-backups").

Personally, I never liked Adobe Reader and it is a huge 129Mb download.

I use [gPDF]("https://addons.mozilla.org/en-US/firefox/addon/14814/").

You can also use Evince with mozplugger:

```
sudo apt-get install evince mozplugger
```

---

### Post by bill-lancaster on 2011-05-26
Thanks for the advice, have re-installed v4 and have have added gPDF (as an add-on)

Here is my problem.  If I look at my Vodafone bills there is a pdf button which should open the document in a new window, all I get is a blank document screen.

It don't think gPDF is being invoked.

Can you advise?

---

### Post by lovinglinux on 2011-05-26
> **bill-lancaster said:**
> Thanks for the advice, have re-installed v4 and have have added gPDF (as an add-on)

Here is my problem.  If I look at my Vodafone bills there is a pdf button which should open the document in a new window, all I get is a blank document screen.

It don't think gPDF is being invoked.

Can you advise?

Have you tried with a simple PDF link to test if the add-on is not working or if it as a problem with that particular button?

---

### Post by bill-lancaster on 2011-05-26
Don't know what I did - buts working now.

Fingers crossed

Thanks again

---

### Post by lovinglinux on 2011-05-26
> **bill-lancaster said:**
> Don't know what I did - buts working now.

Fingers crossed

Thanks again

You are welcome.

---

