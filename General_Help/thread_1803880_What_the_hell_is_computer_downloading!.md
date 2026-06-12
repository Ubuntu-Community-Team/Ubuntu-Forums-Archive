---
title: "What the hell is computer downloading!"
date: 2011-07-14
forum: General Help
---

### Post by I Am Legend on 2011-07-14
The download bar on my conky overlay (${downspeedgraph eth0}) seems to be maxed out constantly. This is when everything should be idle with no downloads happening in the background (at least non that I know about).

Are there any command line tools that can tell me what process is using my ethernet port?

---

### Post by idoitprone on 2011-07-14
iftop
I am not sure if that is what you want?

or
nethogs?

---

### Post by I Am Legend on 2011-07-16
iftop was useful, thanks.

I seem to have a constant 3.5 Mb download from a 169.254.*.* address for some reason. Could be part of the problem.

---

### Post by raja.genupula on 2011-07-16
i am very glad to have this . but i wanna run this as a application from panel . " iftop" . how can i add it to a panel  .   thanks in advance .

---

### Post by idoitprone on 2011-07-17
> **I Am Legend said:**
> iftop was useful, thanks.

I seem to have a constant 3.5 Mb download from a 169.254.*.* address for some reason. Could be part of the problem.

  well if you use nethogs, then you can isolate the problem program. Iftop and nethogs do different things

---

### Post by idoitprone on 2011-07-17
> **raja.genupula said:**
> i am very glad to have this . but i wanna run this as a application from panel . &quot; iftop&quot; . how can i add it to a panel  .   thanks in advance .

 i dont think so, since command line and applets are not the same, you can always have a yaukuate session to always monitor the internet or this applets which provide less info [http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html](http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html)

---

### Post by HiImTye on 2011-07-17
169.254. is a link-local address (meaning it is on your local network) - do you have network drives mounted on your computer (or network drives from your computer mounted on other ones)

---

### Post by akand074 on 2011-07-17
> **HiImTye said:**
> 169.254. is a link-local address (meaning it is on your local network) - do you have network drives mounted on your computer (or network drives from your computer mounted on other ones)

I was going to say. If you are on a network with share folders, if someone else in your house is sharing your folders it'll be downloading and uploading from computer to computer from within the network.

---

