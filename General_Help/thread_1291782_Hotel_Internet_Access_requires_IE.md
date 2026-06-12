---
title: "Hotel Internet Access requires IE?"
date: 2009-10-15
forum: General Help
---

### Post by Jose Catre-Vandis on 2009-10-15
I regularly have to work away from home and stay in a particular hotel. They offer free wireless internet access, and provide a username and password to login through the gateway. This works fine through a Windows OS with IE. However trying to connect on Ubuntu with Firefox (and Firefox on Windows for that matter) does not bring up the login box and prevents access. I use WICD to manage wireless connections.

Any suggestions as to how I could connect through Xubuntu / Firefox?

---

### Post by |Mitch| on 2009-10-15
do you have flash block/no script enabled? cookie saving not allowed maybe?

---

### Post by P4man on 2009-10-15
hmmm.. can you connect to the wireless network? And if you, does firefox show up anything at all?

Worst case I can think off is that the AP uses some activeX component for god knows what reason, and you might be out of luck. But you could try installing IE in ubuntu:

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Note: firefox and google seem to think this is a bad website now? Ive used tatanka's ies4linux for years, I think this is some f* up, I still trust this man :) Perhaps firefox thinks installing IE is a bad idea, and to some extent i agree :p

---

### Post by BenAshton24 on 2009-10-15
You could modify your user agent string in "about:config" to make it think that your running IE7? I think you would want something along the lines of "MSIE 7.0; Windows NT 6.0;"

Hope this helps you,
Ben :D

---

### Post by wilee-nilee on 2009-10-15
You might try user agent switcher add-on in firefox.

---

### Post by jacksaff on 2009-10-15
Can you get on their network at all?
Most likely if you can get on their network then the first page firefox will open to will be their login page and after that you're all set. 
Use the wifi widget to check if you can connect to their network first.
I've just trawled through a whole bunch of hotels/coffee shops and many of them worked that way.

---

### Post by Jose Catre-Vandis on 2009-10-15
Thanks for all the replies:

1. No flash block or no script installed, so not that

2. Can connect to the network, but do not get the login page, so very possibly an activex issue, I'll have to check next time.

3. If not activex I'll try this (about:config edit)

4. I'll try agent:switcher too (get does same as 3?)

5. Yes can get to network but no login page, hence me thinks activex

---

