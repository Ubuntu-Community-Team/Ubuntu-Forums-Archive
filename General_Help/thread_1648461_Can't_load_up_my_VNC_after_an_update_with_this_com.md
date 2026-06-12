---
title: "Can't load up my VNC after an update with this command"
date: 2010-12-18
forum: General Help
---

### Post by chilldy on 2010-12-18
I was told to use this command for an update. It took about an hour. After it was done I restarted and now I can't start my VNC server. -Using a VPS btw. Normally on a fresh boot it uses around 15mb of ram a little less now it's stuck at 2mb - 4mb. When I try to start the VNC it goes to about 9mb which is supposed to go around 350 to 400mb.

> apt-get install python-software-properties -y; cd /etc/apt; rm sources.list; wget [https://allgamer.net/files/sources.list;](https://allgamer.net/files/sources.list;) gpg --keyserver pgpkeys.mit.edu --recv-key C90F9CB90E1FAD0C && gpg --export --armor C90F9CB90E1FAD0C | sudo apt-key add -; apt-get update -y; apt-get install zip screen htop -y; apt-get upgrade -y; apt-get install libmono-corlib2.0-cil libmono-system-runtime2.0-cil libmono-system-web2.0-cil libmono-windowsbase3.0-cil libgdiplus -y; apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts -y

---

### Post by chilldy on 2010-12-18
bump

---

### Post by chilldy on 2010-12-18
Anyone at all? This is becoming a pain and I really need the server back up.

---

### Post by chilldy on 2010-12-19
Bump

---

### Post by HermanAB on 2010-12-19
Hmm, updates are probably the main cause of problems in Linux systems.  It looks like you installed schtuff from some random web sites and now you are wondering why it doesn't work anymore?

Re-install using official repositories only and then don't fix it if it ain't broke...

---

### Post by chilldy on 2010-12-19
> **HermanAB said:**
> Hmm, updates are probably the main cause of problems in Linux systems.  It looks like you installed schtuff from some random web sites and now you are wondering why it doesn't work anymore?

Re-install using official repositories only and then don't fix it if it ain't broke...

How do I re-install from official repositories? I'm not sure where to start with that.

---

