---
title: "My noob question about 64 bit Ubuntu"
date: 2010-06-08
forum: General Help
---

### Post by deep_purple on 2010-06-08
Hello everyone, I'm new to Linux and Ubuntu.
I have a question about the 64 bit version of Ubuntu.
I'm wondering if the 32 and 64 bit version has separated repos. Thus, when we type in terminal 'sudo aptitude install ubuntu-restricted-extras', the system can download it from the right place.

([http://packages.ubuntu.com/lucid/amd64/ubuntu-restricted-extras/download](http://packages.ubuntu.com/lucid/amd64/ubuntu-restricted-extras/download) for 64 bit system)

Looking forward to hearing from you soon.
Thanks :p

---

### Post by Smart Viking on 2010-06-08
I am unsure about different repos and stuff, but the experience is exactly the same, every program you would expect to be available is. :)

---

### Post by howefield on 2010-06-08
> **deep_purple said:**
> Thus, when we type in terminal 'sudo aptitude install ubuntu-restricted-extras', the system can download it from the right place.

You might be better installing the separate components of restricted extras as you will get 32 bit flash installed instead of 64 bit.

64 bit flash is still in beta, so you won't find it in the Ubuntu repository, hence 32 bit would be installed.

Most people seem to have a better experience with beta 64 flash rather than using 32 bit with the wrapper in 64 bit Ubuntu.

---

### Post by deep_purple on 2010-06-08
Thank you guys for your responses. So, when I type 'sudo aptitude install ubuntu-restricted-extras' in terminal, it will install 64 bit Java and other things but 32 bit Flash player right?

---

### Post by Sef on 2010-06-08
> Thank you guys  for your responses. So, when I type 'sudo aptitude install  ubuntu-restricted-extras' in terminal, it will install 64 bit Java and  other things but 32 bit Flash player right?

No, if they install Sun Java, then it will be 32-bit.  If you want a 64-bit java, then you have to download openjdk from the repositories.

---

### Post by deep_purple on 2010-06-08
ok. So is there any 64 bit version for codecs and stuff?

---

### Post by howefield on 2010-06-09
The codecs would come as 64 bit if you install ubuntu-restricted-extras. Only flash and java wouldn't.

Just as easy to install separately. 

For 64 bit flash, download the 64 bit prerelease from Adobes website

```
http://labs.adobe.com/downloads/flashplayer10_64bit.html
```

and extract to... 

```
usr/lib64/mozilla/plugins
```

Firefox and Chrome will pick it up from there, substitute mozilla with opera if you want to set up Opera with flash.

Sun java is in the partner repository, enable it in your Software Sources and install. If you want the open source java package instead of the Sun package, instead of enabling the partner repository, install openjdk.

Then install all the codecs you want.

---

### Post by Louisraritan on 2010-06-09
Cool thread and responses.  Thanks, it helped me out as well.

---

