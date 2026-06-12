---
title: "If-* scripts. Difference between pre-up and up"
date: 2011-08-26
forum: General Help
---

### Post by xzerth on 2011-08-26
Hello.

I've read this document [https://wiki.ubuntu.com/OnNetworkConnectionRunScript](https://wiki.ubuntu.com/OnNetworkConnectionRunScript) and prepared my own scripts and put them into folders that I need.

But I can't understand when if-up or if-pre-up scripts are executed relative to /etc/network/interfaces file. I thought that if-up script executed at first and then /etc/network/interfaces file.
But it seems that it's not quiet correct.

And why should I need to use up /etc/network/if-up.d/script (or post-up, pre-up etc) command in /etc/network/interfaces? The scripts that listed in /etc/network/if-*.d/ folders will executed when time will come, isn't it?

And what time is it?:) I really can't realize it from that document..

Please give me a document where I can find an information about the difference between up and pre-up, post-up,down, etc.. commands which calles if-* scripts. Or something like that.

I'm using ubuntu server 10.04.2

Thank you!

---

