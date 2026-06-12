---
title: "Novell Netware Support?"
date: 2005-02-07
forum: General Help
---

### Post by scubu on 2005-02-07
Hi, I was wondering if anyone has been able to connect to Novell Netware Servers with Ubuntu?

It's my understanding I would need ncpfs installed before installing the novell linux client (novelclient.sourceforge.net). When I do a search in Synaptic Package Manger  for ncpfs (with Universe enabled) I don't get any results.

Any help or advice would be greatly appreciated.

Scott

---

### Post by mojorising on 2005-02-10
Make sure you have the sources set in your /etc/apt/sources.list file. I have mine all enabled (except source locations) and I was able to get NCPFS with no problems. I am having trouble installing Novel but I guess that is another story. Try searching Synaptic package titles and descriptions with the term "netware" and see if it comes up -- that is how I found it. 

BTW: If anyone has any experience getting Novel going on Ubuntu, please let us know. 

This is the error I get:
hostname:/usr/local/bin# sh novelclient
/usr/local/bin/Novel: error while loading shared libraries: libqtintf-6.5-qt2.3.so: cannot open shared object file: No such file or directory

I tried to find /install that libqtintf-6.5-qt2.3.so but could not find it. 

Mike

---

### Post by WillCooke on 2005-02-10
I have it on good authority that Novell have (in beta) a proper Linux client.

I've yet to read anything about it....

{hold on, quick look on the Novell site}

...... aha!  \\:D/ 

[http://www.novell.com/products/clients/linux/quicklook.html](http://www.novell.com/products/clients/linux/quicklook.html) 


... so it does exist.

Oo, they have a ZENworks application as well!

You can apply for a beta here:

[http://www.novell.com/coolsolutions/feature/11487.html](http://www.novell.com/coolsolutions/feature/11487.html) 

I'm going to apply and see how I get on, I *should* get accepted.  I would be interested to get some contacts who will also be trying this thing.  I could be a biggy for us (at work).

Cheers,

Will

---

### Post by WillCooke on 2005-02-10
[QUOTE=mojorising]This is the error I get:
hostname:/usr/local/bin# sh novelclient
/usr/local/bin/Novel: error while loading shared libraries: libqtintf-6.5-qt2.3.so: cannot open shared object file: No such file or directory

I tried to find /install that libqtintf-6.5-qt2.3.so but could not find it. 
[/QUOTE]


Mike,

Have you seen this....

[http://novelclient.sourceforge.net/howto.html](http://novelclient.sourceforge.net/howto.html) 

If not, have a look at the section marked **Executables** .  It mentions making some links to that library.

If you have, sorry, no offence intended.

Cheers,

Will

---

