---
title: "Help Running Apophysis v2.09 with WINE"
date: 2011-04-20
forum: General Help
---

### Post by dpitch40 on 2011-04-20
I became a fan of Apophysis before I got Ubuntu, and recently I decided to try to get it running on my Ubuntu laptop. I've been surprised by how difficult it is, since it's free software. I followed [this tutorial]("http://ubuntuforums.org/showthread.php?t=1013192&highlight=Apophysis") on getting Apophysis 2.09 running. And with WINE, it does work, but I notice that when it starts up, it completely monopolizes my CPU, even if I'm not doing anything in the program. This doesn't seem right and would kill my battery life if I tried to use it without being plugged in. If I run it with WINE on the command line, it spams thousands of the same error line:

```
fixme:iphlpapi:NotifyAddrChange (Handle (nil), overlapped (nil)): stub
```

and stopping it (with Ctrl+C) is unresponsive. I have a feeling that constantly processing this error, whatever it is, is causing the drain on my CPU. Can anyone tell me what this error message means and what I can do about it?

---

