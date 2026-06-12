---
title: "How To Install Deluge from &quot;deluge-1.2.0_rc1.tar.bz2&quot; downloaded file."
date: 2009-12-17
forum: General Help
---

### Post by Moinul Abrar on 2009-12-17
Hello Friends,

I need to install ** torrent files down-loader** [COLOR=Magenta]Deluge-1.2.0_rc1[/COLOR][COLOR=Black] on my Ubuntu 9.10 Desktop PC.[/COLOR]

I'v downloaded a [COLOR=Magenta]deluge-1.2.0_rc1.tar.bz2[COLOR=Black] [/COLOR][/COLOR] file from internet. 

How can I build-up installation file from [COLOR=Magenta]deluge-1.2.0_rc1.tar.bz2 [COLOR=Black]?

Please, help me.

With best regards,

Moinul Abrar
Chittagong, Bangladesh,
[email]md.moinul@gmail.com[/email]
17 December, 2009
[/COLOR][/COLOR] [COLOR=Black]

[/COLOR]

---

### Post by Sin@Sin-Sacrifice on 2009-12-17
That would be compiling from source and if you've never done it before then I would do some research first. You can install deluge using ```
sudo apt-get install deluge
``` and then you won't have to worry about compiling.

---

### Post by Moinul Abrar on 2009-12-17
Hello Friend, 

Thank you for your  help.

I want to know, how can I  build-up installation file from downloaded [COLOR=Magenta]deluge-1.2.0_rc1.tar.bz2 [COLOR=Black]file. 

Please, help me.

With best regards.

Moinul Abrar
[/COLOR][/COLOR]

---

### Post by MelDJ on 2009-12-17
get the .deb or add the reposotory from [http://dev.deluge-torrent.org/wiki/Download](http://dev.deluge-torrent.org/wiki/Download)

---

### Post by falconindy on 2009-12-17
```
tar xvjf deluge-1.2.0_rc1.tar.bz2
cd deluge*
python setup.py build
python setup.py install
```
Really though, you're better off using the [deluge PPA]("https://launchpad.net/~deluge-team/+archive/ppa").

---

### Post by Moinul Abrar on 2009-12-17
Hello falconindy
Thank u for your help.

My downloaded file is [COLOR=Magenta]deluge-1.2.0_rc4.tar.bz2 .

[COLOR=Black] I create a [/COLOR][/COLOR]folder on desktop, named it **deluge** and saved [COLOR=Magenta]deluge-1.2.0_rc4.tar.bz2 [COLOR=Black]into that folder. Is it correct?

What is the meaning of [COLOR=Magenta]cd deluge* [COLOR=Black]and [COLOR=Magenta]*              

[COLOR=Black]In terminal, when I past the following code, then given an error message:
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Magenta]tar xvjf deluge-1.2.0_rc4.tar.bz2
cd deluge*
python setup.py build
python setup.py install

[COLOR=Black]Please reply.
With best regards,
Moinul Abrar
[EMAIL="mdmoinul@gmail.com"]mdmoinul@gmail.com[/EMAIL]
[/COLOR][/COLOR]
[COLOR=Magenta][COLOR=Black][COLOR=Magenta][COLOR=Black][COLOR=Magenta][COLOR=Black]
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

