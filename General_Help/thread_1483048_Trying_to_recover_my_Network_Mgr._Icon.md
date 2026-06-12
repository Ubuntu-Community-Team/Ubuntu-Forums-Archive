---
title: "Trying to recover my Network Mgr. Icon"
date: 2010-05-14
forum: General Help
---

### Post by MildlyInsane on 2010-05-14
How do I get my Network Manager icon back onto the desktop? I totally dorked out and removed it. Not sure why. I'm back on my Vista desktop now because I can't connect to the Internet on my new OS. I installed Ubuntu 10.04 LTS, (Gnome desktop). I'm totally new to the world of Linux/Ubuntu, free software, etc. and I'm also only about 18.5% geek, so please help me, someone! Thanks.

---

### Post by nothingspecial on 2010-05-14
If you have simply removed it from your panel then press Alt F2 and type ```
nm-applet
```

If you have removed network manager all together then get a wired connection and type
```

sudo ifconfig eth0 up
sudo dhclient
sudo apt-get update && sudo apt-get install network-manager
```

---

### Post by MildlyInsane on 2010-05-14
Thanks, nothing special! As anxious as I am to try your suggestions, I'm falling asleep and will have to try in the morning. I'll get back with you after I've tried it. 

(Nice zen name).

---

### Post by MildlyInsane on 2010-05-14
After excitedly installing my brand new Ubuntu OS, I was exploring the top panel and accidently removed my Network Manager Icon. As simple as it was to remove it, it has been extremely difficult to get back and I'm still as lost as ever. I tried the first suggestion by user "nothingspecial" and I get a dialog window that was not helping me however much I tried. I can't understand why it was so easy to mistakenly remove the icon and how extraordinarily hard it is to retrieve it. I'm a complete newbie and am already very frustrated.

---

### Post by spiky001 on 2010-05-14
Have you tried adding nottification applet to panel?

---

### Post by MildlyInsane on 2010-05-14
Yes Ive tried that in the only way I know how and thats by opening the add notification panel and it does not list the network manager at all.

---

### Post by demuxer on 2010-05-20
hello, I had the same problem with Karmic just days ago, and with nm-applet was recovered.

but now in Lucid I cant remove that icon jus to try to solve your problem, really I cant hide/remove that new icon (white wall ethernet port and blue cable) but the notification area doesnt include the network manager

---

### Post by Nunu on 2010-05-22
I created a launcher with command gksu nm-applet. restores the icon and adds some security as you can't connect to the Internet / wifi network without the icon unless you know how to use terminal... in SA not so many people know LINUX :)

---

