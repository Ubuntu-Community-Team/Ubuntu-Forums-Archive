---
title: "Flushing DNS Cache"
date: 2010-10-28
forum: General Help
---

### Post by dgoddard1 on 2010-10-28
I have been advised to flush the DNS cache to solve a problem I am having with certain websites.  To do this I was advised to see the web page[http://www.techiecorner.com/35/how-to-flush-dns-cache-in-linux-windows-mac/]("http://www.techiecorner.com/35/how-to-flush-dns-cache-in-linux-windows-mac/").  The instructions there tell me:
[B]To flush the DNS cache in Linux, restart the nscd daemon:-
- To restart the nscd daemon, type /etc/rc.d/init.d/nscd restart in your terminal
- Once you run the command your linux DNS cache will flush.[/B]
However when I try that in the Ubuntu terminal I get:
**bash: /etc/rc.d/init.d/nscd: No such file or directory**
And attempting to find file "nscd" anywhere else has been fruitless.
[B][U]
How does one flush the DNS cache in Ubuntu?[/U][/B]
Release 8.04 (Hardy)
Kernel 2.6.24-16-Generic
Gnome 2.22.1
Browser3.0b5

---

### Post by fooman on 2010-10-28
in the link you provided....scroll down and read the very first comment.  it says that the correct command for linux is:

```
sudo /etc/init.d/dns-clean start
```

i do not know what flushing the dns does,  so cannot comment on whether or not it works.

---

