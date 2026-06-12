---
title: "How to remove a PPA and a SSH authentication question"
date: 2010-06-25
forum: General Help
---

### Post by t36 on 2010-06-25
Hi,

I recently tried installing a PPA and now I want to remove it, but I can't find any documentation on how to do that. I already went to Software Sources and remove the package from there and its authentication, but it still shows up in the Software Center albeit with less software.

Can anyone help me?

My second question is about SSH authentication. Each time I try to connect via the command line 'ssh [email]me@some.server.com[/email]' I get a graphical pop up asking for authentication, is it possible to change this to a command prompt?

Thanks in advance,

Minh

---

### Post by wilee-nilee on 2010-06-25
> **t36 said:**
> Hi,

I recently tried installing a PPA and now I want to remove it, but I can't find any documentation on how to do that. I already went to Software Sources and remove the package from there and its authentication, but it still shows up in the Software Center albeit with less software.

Can anyone help me?

My second question is about SSH authentication. Each time I try to connect via the command line 'ssh [email]me@some.server.com[/email]' I get a graphical pop up asking for authentication, is it possible to change this to a command prompt?

Thanks in advance,

Minh

I can't help you with the ssh, but don't use the software center use synaptic.

If you want to see if the ppa is still in the apt list run
```
sudo gedit /etc/apt/sources.list
```

This will open the list to be edited be careful.

I think you have removed the ppa and anything that is in the software center was always there or you haven't run ```
sudo apt-get update
``` to reset it.

---

