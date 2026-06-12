---
title: "Google Chrome"
date: 2012-03-11
forum: General Help
---

### Post by holytree on 2012-03-11
Hi I have a native install of ubuntu 11.10 

after downloading google chrome.deb package from the google website when i open it i get the following error

INTERNAL ERROR
The file '/home/harsha/downloads/google-chrome-stable_current(1).deb" could not be opened

please help as im sick of usin firefox... ::)   :(

Regards,
holytree

---

### Post by AlexDudko on 2012-03-11
> **holytree said:**
> Hi I have a native install of ubuntu 11.10 

after downloading google chrome.deb package from the google website when i open it i get the following error

INTERNAL ERROR
The file '/home/harsha/downloads/google-chrome-stable_current(1).deb" could not be opened

please help as im sick of usin firefox... ::)   :(

Regards,
holytree

Run
> sudo dpkg -i google-chrome-stable_current(1).deb

---

### Post by 2F4U on 2012-03-11
I guess it is better to install chrome using apt-get and dpkg:

[http://www.google.com/support/forum/p/Chrome/thread?tid=381d28fd49d3fc52](http://www.google.com/support/forum/p/Chrome/thread?tid=381d28fd49d3fc52)

---

### Post by raja.genupula on 2012-03-11
> **AlexDudko said:**
> Run

@OP after executing this command , have you got any errors ?

---

### Post by holytree on 2012-03-11
bash: syntax error near unexpected token `('


i got this error after typing the command

thanks for ur quick response..

regards
holytree

---

### Post by AlexDudko on 2012-03-11
> **holytree said:**
> 

INTERNAL ERROR
The file '/home/harsha/downloads/[COLOR="Red"]google-chrome-stable_current(1).deb[/COLOR]" could not be opened


> **holytree said:**
> bash: syntax error near unexpected token `('


i got this error after typing the command

thanks for ur quick response..

regards
holytree

Are you sure you've downloaded the proper file? It's name looks strange.
It should be either google-chrome-stable_current_i386.deb for 32-bit file system or google-chrome-stable_current_amd64.deb for the 64-bit one.
Try this link: [http://www.google.co.uk/chrome](http://www.google.co.uk/chrome)

---

### Post by raja.genupula on 2012-03-11
> **holytree said:**
> bash: syntax error near unexpected token `('


i got this error after typing the command

thanks for ur quick response..

regards
holytree

give us terminal code

---

### Post by malspa on 2012-03-11
> **holytree said:**
> The file '/home/harsha/downloads/google-chrome-stable_current(1).deb" could not be opened

Are there two Chrome .deb files in your Downloads directory?

Also, shouldn't that be "Downloads" instead of "downloads"?

---

### Post by malspa on 2012-03-11
Check this out: [http://www.computerandyou.net/2011/10/how-to-install-google-chrome-in-ubuntu-11-10/](http://www.computerandyou.net/2011/10/how-to-install-google-chrome-in-ubuntu-11-10/)

---

### Post by holytree on 2012-03-11
Yes there are two files...am trying ur suggestions

thanks,
holytree

---

### Post by holytree on 2012-03-11
Still get the same internal error....god... :(

---

### Post by malspa on 2012-03-11
If you are doing this from a terminal, do as raj suggested:

> **raja.genupula said:**
> give us terminal code

In other words, post here the exact commands you're using, and also the all of the output.

If you follow the steps at [http://www.computerandyou.net/2011/10/how-to-install-google-chrome-in-ubuntu-11-10/](http://www.computerandyou.net/2011/10/how-to-install-google-chrome-in-ubuntu-11-10/) then post here the exact steps you used and post exactly what messages you see.

Otherwise it's kinda difficult to help, at this point. Off the top of my head, I'm thinking maybe get rid of google-chrome-stable_current(1).deb and use only google-chrome-stable_current.deb.

---

### Post by holytree on 2012-03-22
solved thanks all the link above helped!!

---

