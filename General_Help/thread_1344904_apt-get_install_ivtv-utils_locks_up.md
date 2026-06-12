---
title: "apt-get install ivtv-utils locks up"
date: 2009-12-03
forum: General Help
---

### Post by scriptless on 2009-12-03
OS: Ubuntu 9.10 64 bit - german language.
When trying to install ivtv-utils via ssh I get a block graphics screen with a message about selecting my email settings and an 'ok' to press to go further. However the 'ok' cannot be pressed and the ssh session can only be exited by killing the terminal window.

From Client:  
> ssh -X me@server
> apt-get install ivtv-utils
> J  (for yes, install - german version of ubuntu)
Block graphics screen with the title 'Postfix Configuration' appears about email server settings and cannot be exited.

Has anyone had problems using apt-get install over ssh ? This is the first time I have seen such a behaviour or is it special to ivtv-utils ?
removing -X makes no difference, I tried without.

---

