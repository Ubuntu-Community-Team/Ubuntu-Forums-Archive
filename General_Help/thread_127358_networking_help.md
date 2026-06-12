---
title: "networking help"
date: 2006-02-08
forum: General Help
---

### Post by hdaddy on 2006-02-08
i want to send files to my mac to my linux and from linux to my mac i cant seam to do that

---

### Post by el3ktro on 2006-02-09
Honestly, you REALLY have to be a little more precise in what you want to do, what you've tried already ... nobody can & will help you when you ask this way. Not meant to be rude, but you didn't give ANY info about your computers, your network, what you exactly want to do etc.

Tom

---

### Post by bountonw on 2006-02-09
I think Tom is saying,

1. What model of Mac (one of the new intel insides?)
2. What version of Mac OS
3. What model of computer your linux is on x86, ppc?
4. What distro of linux are you using?
5. What kind of networking connection are you planning?

I am a newbie and have been using yahoo answers some.  There you ask one question and answer two.  Unfortunatly I don't know enough to help answer much and have flooded this forum with questions.  I am hoping that I learn enough so that I can be of better assistance to others.

---

### Post by AndyCooll on 2006-02-09
Samba will handle all that.

Ideally you'll need to make sure both computers are on the same domain and that your accounts and passwords are the same.

Then on the Linux box install Samba and smbfs (there are a number of HOWTO threads on these forums explaining all the ins and outs) and set up your shares. I'm at work at the moment so not viewing my Linux box, but IIRC under administration there is "Share Folders" option.

Of course you'll also need to setup your shared folders on the MAC pc.

Here are a couple of threads to start you off:
[How to share files using Samba]("http://www.ubuntuforums.org/showthread.php?t=76647")
[Unofficial Ubuntu guide]("http://www.ubuntuguide.org/")

:cool:

---

