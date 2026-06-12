---
title: "Printer Installation"
date: 2011-08-10
forum: General Help
---

### Post by neba on 2011-08-10
I am trying to install a printer (Lexmark s405) There are no drivers to be automatically installed. The company has a .dev driver. I was going through the installation and I accidentally closed out of the wizard. now when I try to re-install it I get this message

The installer has detected previously installed components.

-- lexmark-inkjet-legacy
-- lexmark-wsu-legacy

Please remove all installed components and run the installer again.

it also gives me this command to execute 'rm -rf /root/lua_M9UK2v'
I have done that, but I still get the same message. I have tried to locate the files in the terminal, but nothing will come up. Any help will be appreciated,
Thank you,
Neba

---

### Post by Darkened35 on 2011-08-10
Try running:
```
sudo apt-get --purge remove lexmark-inkjet-legacy
sudo apt-get --purge remove lexmark-wsu-legacy 
```
Report back.

---

### Post by neba on 2011-08-10
Thank you for your reply, I when I put the command in this was the output 'E: Unable to locate package lexmark-inkjet-legacy'
This came up on both of them.
thank you 
Neba

---

### Post by neba on 2011-08-11
bump

---

### Post by neba on 2011-08-12
I got it working! yay. I was only using the terminal and that was not working. I decided to use systematic package manager. uninstalled all Laxmark packages, then re-installed it. Hope this helps someone else in the future.
Neba

---

### Post by gatorhater73 on 2011-11-07
Holy CRAP, thank you for this! My printer was driving me crazy... this was a huge help!

---

### Post by themacoz on 2011-11-12
YES!! The Synaptic Package Manager advice rocked for removal of lexmark-wsu-legacy

Specially since there are two packages that show up as needing removal.

When I had used an older post to do:

sudo apt-get remove --purge lexmark-inkjet-legacy

Then ...

sudo apt-get remove --purge lexmark-wsu-legacy

Did not work ... could not find the package.

Thanks for posting advice.

---

