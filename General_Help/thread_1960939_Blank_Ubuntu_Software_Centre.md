---
title: "Blank Ubuntu Software Centre"
date: 2012-04-18
forum: General Help
---

### Post by JasonLugg on 2012-04-18
Hi All

Yes I am a newbie...soooo sick on windows!

Anyhow, I have installed Ubuntu 12.04 and all seems well except when I launch the software centre I somply get a blank window open.....

I though I could select software t install and see installed software here?

What could I be doing wrong?


Thanks

---

### Post by tmaranets on 2012-04-18
It sometimes matters on what company computer you have. Ubuntu works with different company computers. Your blank Ubuntu Software Center is probably an error that you have to be patient with.

---

### Post by JasonLugg on 2012-04-18
I am currently using Ubuntu on an Acer Aspire One netbook with 2GB of RAM!

Sometime ago I did have Ubuntu installed but wanted to try Mint and it installed over Ubuntu. After finding Many::Issues with mint decided to go back to Ubuntu but seems there are problems!

---

### Post by raja.genupula on 2012-04-18
type ```
gksu software-center
``` in your terminal and let us know what you got , something like errors .

---

### Post by cortman on 2012-04-18
> **JasonLugg said:**
> I am currently using Ubuntu on an Acer Aspire One netbook with 2GB of RAM!

Sometime ago I did have Ubuntu installed but wanted to try Mint and it installed over Ubuntu. After finding Many::Issues with mint decided to go back to Ubuntu but seems there are problems!

+1 to Acer Aspire One netbooks, I have one myself.

You may just need to uninstall/reinstall the software center.
In a terminal:

```
sudo apt-get remove software-center
sudo apt-get install software center
```

Per the above example, you can also install/remove software from the command line, and there's a nifty GUI program for installation available as well, called Synaptic.

---

### Post by raja.genupula on 2012-04-18
> **cortman said:**
> +1 to Acer Aspire One netbooks, I have one myself.

You may just need to uninstall/reinstall the software center.
In a terminal:

```
sudo apt-get remove software-center
sudo apt-get install software center
```

Per the above example, you can also install/remove software from the command line, and there's a nifty GUI program for installation available as well, called Synaptic.

Hey cortman , how about this . one shot solution as you suggested 

```
sudo apt-get install --reinstall software-center
```

---

### Post by abrianb on 2012-04-22
My software center just stopped working on my thinkpad T-60. This is a long term install and this app worked until recently on this machine. I also lost the application function of the dash. here is the output of gksu software-center...

2012-04-22 08:07:05,995 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-04-22 08:07:06,125 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2012-04-22 08:07:12,262 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0

---

