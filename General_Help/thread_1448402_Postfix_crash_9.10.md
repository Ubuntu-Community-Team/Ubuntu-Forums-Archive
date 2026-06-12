---
title: "Postfix crash 9.10"
date: 2010-04-06
forum: General Help
---

### Post by deznuts05 on 2010-04-06
I'm trying to install postfix on a copy of 9.10 .

sudo apt-get install postfix (press enter)

I get asked a (Y/N). I chose Y; then I'm brought to a "Postfix Configuration" screen that tells me about No configuration: .... Internet Site:... and at the end its says <Ok>

Here's the kicker I have use of the arrows but that's it. 

How do I get out of this screen?

---

### Post by deznuts05 on 2010-04-07
Please let me know if I'm unclear in any way. I'd like to complete my install of Nagios on this machine.

Once again, I'm able to download and begin the install process of the postfix however I'm halted on the "Postfix Configuration" screen and lose the ability to accept/make changes.

Thank you for any help possible.

---

### Post by gmargo on 2010-04-07
You should be able to use the tab key to skip fields to the <ok> and then hit return.

---

### Post by deznuts05 on 2010-04-07
BINGO!

what I swear, that tab-key!!!! thank you so much

---

### Post by dcstar on 2010-04-07
> **deznuts05 said:**
> BINGO!

what I swear, that tab-key!!!! thank you so much

```
sudo dpkg-reconfigure debconf
```

---

