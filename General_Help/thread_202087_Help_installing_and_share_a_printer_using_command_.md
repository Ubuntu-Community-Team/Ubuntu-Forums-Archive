---
title: "Help installing and share a printer using command line only"
date: 2006-06-22
forum: General Help
---

### Post by AndyCooll on 2006-06-22
I have five pc's on my home network (a very basic setup). All run Linux (Dapper) and they are protected from the outside world by my routers firewall. I then have a HP DeskJet 990cxi printer attached to my file server.

I have no problem setting the printer up using the gui. System-->Administration-->Printing. I then add the printer accepting the defaults (including connection: local printer, and hpijs (recommended) HPLIP 0.9.7). Finally I place a tick against "global settings-->Detect LAN printers". And that's it on the server. I then repeat the tick in the global settings procedure on the other pc's and 'hey presto' I have successfully set up a shared printer. And everything works fine.

Now however I'd like to do the above on the server using the command line since I'd like the file server to be a "server" only (i.e. no gui). And it's at this point that I realise my command line limitations. I've looked at various tutorials and just can't seem to figure them out. Indeed I wanted to do this the last last time I re-installed, but I ended up installing the Ubuntu desktop purely to enable me to set up the printing.

So ...please can someone explain to me the basic command lines I'd use (and what they mean) to set this printer up. Thanks

:cool:

---

### Post by AndyCooll on 2006-06-23
Anyone?

---

### Post by scanez on 2006-06-24
Try using the cups configuration at [http://localhost:631](http://localhost:631) with a text-based browser -- such as w3m, links, or lynx (whatever's installed).

---

### Post by AndyCooll on 2006-06-24
Thanks for your reply.

Although that might be a way, I was preferably seeking assistance to set the printer up using the command line. And then I'd like to know what the equivalent command line code is that enables it to be shared

Anyway, doesn't the printer need to be already configured/set up before you can use CUPS? Or can I do everything using CUPS. If so, I believe I can configure CUPS remotely so how would I do that?

:cool:

---

### Post by AndyCooll on 2006-06-25
Bump.

I'd really like some help on this guys. Is there really no-one on these forums who knows how to configure a printer using the command line?

---

### Post by scanez on 2006-06-25
CUPS itself will configure your printer, using that link I gave you before. I'm not sure how you would do it from the command line with just a single command, but using w3m to open [http://localhost:631](http://localhost:631) should still work fine. This doesn't need a GUI and will work in a console, even remotely.

One you open up [http://localhost:631](http://localhost:631) in w3m, go to Administration -> Add Printer and follow the instructions.

---

### Post by AndyCooll on 2006-06-25
Thanks for the follow up reply. Ok that sounds good, in which case I'll try the w3m and CUPS method next time.

:cool:

---

