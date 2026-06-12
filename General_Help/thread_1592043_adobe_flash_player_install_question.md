---
title: "adobe flash player install question"
date: 2010-10-10
forum: General Help
---

### Post by warakawa on 2010-10-10
I'm trying to download adobe flash player 10 in order to watch youtube, however there are five different version to download and I have no idea what is the difference between them. 

YUM for Linux
.tar.gz for Linux
.rpm for Linux
.deb for Ubuntu 8.04+
APT for Ubuntu 9.04+

what are the difference and what is the best one to download for firefox 3.6 on ubuntu 10.10 64bit. 

Thanks.

---

### Post by rolodoom on 2010-10-10
As far as I know, ther was a 64 bits flash player, but they get it off-line, and they say that will be back in near future.

I'm using Ubuntu 10.04 LTS 64 bits, and I installed flash player using the top right icon that appears whn you enter into a flash enable site. So, once clicked, I choose the Adobe option, not gnash, and it's working, once in a while it blocks, but actually is usable.

---

### Post by oopsie on 2010-10-10
It's easiest to just install it from the package manager.

---

### Post by warakawa on 2010-10-10
Yeah, Thanks.

---

### Post by formaldehyde_spoon on 2010-10-10
There is a new 64 bit Flash out from Adobe: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Install:
1. Download the .tar.gz file for 64 bit Linux from that page. 
2. Right click on the file, 'Extract here'.
3. Move the .so file to "~/.mozilla/plugins" (may need to show hidden files in View menu)

Done!  Start Firefox...

*Don't* install Flash from the repositories; it's 32 bit and for many people it doesn't work well with 64 bit Ubuntu.

---

