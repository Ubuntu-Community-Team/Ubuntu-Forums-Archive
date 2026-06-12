---
title: "Keyboard keep reverting back to US layout"
date: 2010-04-02
forum: General Help
---

### Post by Eddles on 2010-04-02
I've got an UK keyboard, and every time I boot up, Ubuntu keep reverting back to the US keyboard layout which is annoying me.  I open up keyboard preferences, the UK layout is already selected.  So I delete the US layout, click on "Apply System-wide" and it works.  Until I reboot and the US layout is back in there!

I suspect it's something to do with not having admin privileges to permanently save the changes - if this is the case, why it doesn't ask me for my password, or give me a chance to escalate my privileges or something?

Thanks for advice in advance!

---

### Post by dcstar on 2010-04-03
> **Eddles said:**
> I've got an UK keyboard, and every time I boot up, Ubuntu keep reverting back to the US keyboard layout which is annoying me.  I open up keyboard preferences, the UK layout is already selected.  So I delete the US layout, click on "Apply System-wide" and it works.  Until I reboot and the US layout is back in there!

I suspect it's something to do with not having admin privileges to permanently save the changes - if this is the case, why it doesn't ask me for my password, or give me a chance to escalate my privileges or something?

Thanks for advice in advance!

Do you have English-UK installed in your Languages?

---

### Post by Eddles on 2010-04-08
> **dcstar said:**
> Do you have English-UK installed in your Languages?

Yes - everything's set to English - UK already.  I have fixed the problem - I ran "sudo gnome-keyboard-properties" from terminal, deleted the US keyboard map, and clicked on "Apply System-wide" - this time it took longer - and it now worked from that point onwards, confirming my suspicions.  This is clearly a bug - if I click on "Apply System-wide" without running it from terminal, it should tell me that it didn't work or at least ask for a root password (depending on Ubuntu's policies).

---

