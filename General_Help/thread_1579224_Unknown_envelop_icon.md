---
title: "Unknown envelop icon"
date: 2010-09-21
forum: General Help
---

### Post by COKEDUDE on 2010-09-21
Could anyone tell me what that envelop icon is that I circled and how to remove it? I have no clue where it came from, but I really don't like it and want it gone :). 
[IMG]http://lookpic.com/c1/i2/2757/BHJKX6i.jpeg[/IMG]

[http://lookpic.com/c1/i2/2757/BHJKX6i.jpeg](http://lookpic.com/c1/i2/2757/BHJKX6i.jpeg)

---

### Post by apmcd47 on 2010-09-21
I'm guessing it's a mail notifier applet to tell you when you have e-mail. What happens when you hover the pointer over it? What happens when you right-click it?

Andrew

---

### Post by COKEDUDE on 2010-09-21
> **apmcd47 said:**
> I'm guessing it's a mail notifier applet to tell you when you have e-mail. What happens when you hover the pointer over it? What happens when you right-click it?

Andrew

The usual pop up menu pops up. Yes I know there is remove from panel option, but that removes everything not just the envelop icon. I only want the envelop gone.

---

### Post by apmcd47 on 2010-09-21
> **COKEDUDE said:**
> The usual pop up menu pops up. Yes I know there is remove from panel option, but that removes everything not just the envelop icon. I only want the envelop gone.

Try left-click then? If the remove from panel option removes everything then it must be in a sub-panel such as a system tray. Sorry to be vague but I use KDE and you are obviously using another desktop.

Andrew

---

### Post by gandaran on 2010-09-21
> **COKEDUDE said:**
> The usual pop up menu pops up. Yes I know there is remove from panel option, but that removes everything not just the envelop icon. I only want the envelop gone.
uninstall *evolution-indicator* I think this removes just the envelope and still keep the rest indicator messages, or if you want to remove all messages and just keep the sound applet then uninstall *indicator-messages*
you may need to reboot to take effect.

---

### Post by COKEDUDE on 2010-09-22
> **gandaran said:**
> uninstall *evolution-indicator* I think this removes just the envelope and still keep the rest indicator messages, or if you want to remove all messages and just keep the sound applet then uninstall *indicator-messages*
you may need to reboot to take effect.

Removing indicator-messages and Evolution did the trick for me. Gotta make sure you don't remove python-evolution by accident. That causes a lot of problems.

---

