---
title: "Using ssh when the firewall only allows http"
date: 2009-12-05
forum: General Help
---

### Post by walvim on 2009-12-05
This will be a very short tip that i discovered by accident.
Suppose you are not at home and you are using a system that does not have a ssh-client or you are using a system behind a firewall that only allows http traffic to the internet.
Now if you want to ssh to your home system you will still be able to do it by using a webbased ssh client. This is a third system that acts as a middle man between you and the system with the ssh-server. Your local system speaks http with that third system, which in turn speaks ssh with the ssh server you want to reach.
If you have a extra server you can transform it into a webbased sshclient, with a program like "anyterm". You can find extra information on installing anyterm at [this site]("http://djpate.com/2009/10/30/how-to-install-anyterm-on-ubuntu-karmic-koala/"). 
If you don't have a extra server you can also just use one of the public webbased ssh clients, like [URL="http://electrica-ms.mures.rdsnet.ro/"]electrica
[/URL]

---

