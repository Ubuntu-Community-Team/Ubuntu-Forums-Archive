---
title: "Pandora ONE Desktop App certificate validation error"
date: 2010-03-25
forum: General Help
---

### Post by opethfan89 on 2010-03-25
Hi all

I just recently installed Adobe AIR, and the Pandora ONE desktop app. Everything works fine, but everytime I boot up my computer I get the following message (see screenshot):

[screenshot here]("http://tinypic.com/r/m8e58n/5")

Any ideas? Its nothing but a minor annoyance, but I'd like to permanently accept that certificate, since it is a trusted (paid) program, and I'd like it to automatically work without issue.

Also, can someone tell me how to post thumbnailed photos, just to make things easier in the future?

*EDIT* Well, as it turns out, a quick google search for that error turned up [this forum]("http://satwaves.com/forum/viewtopic.php?p=83967"). Post #8 outlines instructions, but that did not work for me (it actually gave me an error that I couldn't even connect to Pandora!) So what I did was undo those changes, and simply click "view certificate" when that message came, and I followed the instructions and copied + pasted it into that the ~/.appdata/Adobe/AIR/Certs/curl-ca-bundle.crt file.

Hope this helps someone! I'm not sure why but I can't set the [SOLVED] tag?

---

### Post by cseibert on 2010-04-09
That file did not work for me. I had to edit the following file, instead.

/opt/Adobe AIR/Versions/1.0/Resources/curl-ca-bundle.crt

---

### Post by Flare88 on 2010-04-09
Just out of curiosity, what program are you using to interface with your guitar?

---

### Post by loope on 2010-04-13
dos2unix /opt/Adobe\ AIR/Versions/1.0/Resources/curl-ca-bundle.crt

Carriage returns!

---

### Post by opethfan89 on 2010-04-23
> **Flare88 said:**
> Just out of curiosity, what program are you using to interface with your guitar?
Do you mean connect my guitar to my computer? I'm not doing that atm, don't have the setup for it.

> **cseibert said:**
> That file did not work for me. I had to edit the following file, instead.

/opt/Adobe AIR/Versions/1.0/Resources/curl-ca-bundle.crt

Well glad to see you got it working, but at least this is a more permanent fix to the issue. I hope that Pandora releases an official fix, at LEAST for Ubuntu.

---

