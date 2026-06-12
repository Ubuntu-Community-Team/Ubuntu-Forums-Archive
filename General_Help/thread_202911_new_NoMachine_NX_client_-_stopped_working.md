---
title: "new NoMachine NX client - stopped working?"
date: 2006-06-24
forum: General Help
---

### Post by oofnik on 2006-06-24
Hello, I've been using freenx with my Ubuntu box for some time. Whenever I was somewhere and needed access I would download the client from NoMachine's website and it would work flawlessly. Just yesterday however, !M released a new version of their client, 2.0.0. When I try to connect to my box, it authenticates and everything, but the remote window never shows up - the program just disappears and that's it. ](*,) I have to ssh into my box and do a 'sudo nxserver --cleanup' to get it to work again, and only with the old version of the client (1.5.0). Has anybody gotten the new !M client to work with the freenx server?

Forgot to mention that the client is on Windows. Thanks for any help!!

---

### Post by archetypo on 2006-06-25
[QUOTE=oofnik]Hello, I've been using freenx with my Ubuntu box for some time. Whenever I was somewhere and needed access I would download the client from NoMachine's website and it would work flawlessly. Just yesterday however, !M released a new version of their client, 2.0.0. When I try to connect to my box, it authenticates and everything, but the remote window never shows up - the program just disappears and that's it. ](*,) I have to ssh into my box and do a 'sudo nxserver --cleanup' to get it to work again, and only with the old version of the client (1.5.0). Has anybody gotten the new !M client to work with the freenx server?

Forgot to mention that the client is on Windows. Thanks for any help!![/QUOTE]

Did you ever resolve this?

I am trying to connect from a Windows XP to Ubuntu.  The client authenticates, the sessions admin client tool shows a valid connection, there's a server side file.  It all looks fine, but NO GNOME WINDOW!  No problems in the logs.  Any ideas?

---

### Post by mannheim on 2006-06-25
[QUOTE=oofnik] Has anybody gotten the new !M client to work with the freenx server?
[/QUOTE]

The server (version 2.0) is free too, now, so you don't need to use the freenx version. The new server is working fine here with the new client. I uninstalled the frrenx debs (apt-get remove --purge) and wiped out the /usr/NX directory, then re-installed the debs from nomachine's web site ([see this other thread]("http://ubuntuforums.org/showthread.php?t=202394")).

I also had problems with the new client and the freenx version of the server.

---

### Post by oofnik on 2006-06-26
Thanks for the the other thread mannheim, I now have the new nx server installed. Unfortunately I'm still running into problems.. My client (now 2.0.0) will connect, authenticate, but then it dies at 'Negotiating link parameters', the connection fails and terminates. I tried stopping and starting the server, reinstalling, reconfiguring.. there must be something I'm missing here. Any ideas?

edit: Got it fixed by re-configuring the client to enable SSL encryption on all traffic. No speed increase from the freenx server but at least it works now with the 2.0.0 client.

---

### Post by mannheim on 2006-06-26
[QUOTE=oofnik]Thanks for the the other thread mannheim, I now have the new nx server installed. Unfortunately I'm still running into problems.. My client (now 2.0.0) will connect, authenticate, but then it dies at 'Negotiating link parameters', the connection fails and terminates. I tried stopping and starting the server, reinstalling, reconfiguring.. there must be something I'm missing here. Any ideas?[/QUOTE]

I don't know what to suggst except random things you may have tried already. In the NX Client dialog, have you checked "Enable SSL encryption of all traffic"?

It might also be a good idea to try wiping out (or moving out the way) the directory /home/<username>/.nx (where sessions info and cache seems to be stored). On Windows, the corresponding directory is \Documents and Settings\<username>\.nx".

Perhaps you could also try connecting to nomachine's demo server (they offer an account for testing), to see if the client is at least functional.

---

### Post by iduriduridur on 2006-06-27
the 2.0 version of nomachines client does not work with the ubuntu freenx latest download the 1.5 version it will work again. Google for nxclient 1.5 for windows zdnet had it. It works again for me. :p

---

### Post by archetypo on 2006-06-27
[QUOTE=iduriduridur]the 2.0 version of nomachines client does not work with the ubuntu freenx latest download the 1.5 version it will work again. Google for nxclient 1.5 for windows zdnet had it. It works again for me. :p[/QUOTE]

Yep!  That worked.  Thanks for taking the time to reply.  Any idea what's wrong and when 2.0 will work?

---

### Post by mannheim on 2006-06-28
[QUOTE=archetypo]Yep!  That worked.  Thanks for taking the time to reply.  Any idea what's wrong and when 2.0 will work?[/QUOTE]

According to nomachine's site, version 2.0 of the client is supposed to work with earlier versions of nxserver (see [here]("http://www.nomachine.com/ar/view.php?ar_id=AR06D00396") for example). But this problem getting the new 2.0 client to work with freenx seems to be common. Perhaps the problem stems from the difference between freenx and nomachine's own nxserver. (freenx is based on the same nx libraries as nomachine's version 1.4, but freenx implements nxserver as a bash script.)

Now that nomachine has made their nxerver 2.0 freely available (even in a restricted version), I wonder if freenx will be continued.

---

### Post by allnameswereout on 2006-06-28
Certainly hope FreeNX catches up. FreeNX is part of KDE integration project for wider adoption of the NX protocol. Also, FreeNX basically runs on all architectures and OSes. NX server does not, you are limited by what N!Machine ported their server software to.

I admit they have a pretty decent range of ports. It does not satisfy my needs though hence i'll happily keep FreeNX running on a Ubuntu DD/SPARC :)

However NX 2.0 solves a lot of issues ([1](http://www.nomachine.com/news-read.php?idnews=174)). For example, the session support in FreeNX is pretty broken. So NX 2.0 is basically better than FreeNX or NX 1.5.

---

### Post by mannheim on 2006-06-29
[QUOTE=allnameswereout]
I admit they have a pretty decent range of ports. It does not satisfy my needs though hence i'll happily keep FreeNX running on a Ubuntu DD/SPARC :)
[/QUOTE]

That's a good point -- I hadn't really realized that the **source** code for the nx libraries had been made available in this way.

There is also the issue that it seems to cost a minimum of $124.50 if you so much as want to inform nomachine of a bug.

---

### Post by Predseda3D on 2006-08-03
> **iduriduridur said:**
> the 2.0 version of nomachines client does not work with the ubuntu freenx latest download the 1.5 version it will work again. Google for nxclient 1.5 for windows zdnet had it. It works again for me. :p

Hi,


If somebody have problem with NX Clients versions 2.0.0 and FreeNX 0.4.x or 0.5.0, you can read wiki about this problem and solution here: 
[http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving]("http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving")
or here:
[http://wiki.debian.org/freenx]("http://wiki.debian.org/freenx")
or here:
[http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0]("http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0")

With this patchs apply, all working great, try it.

Hope that will help. 

Predseda

---

