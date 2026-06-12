---
title: "Open encryted pgp files"
date: 2006-06-14
forum: General Help
---

### Post by JohanSwe on 2006-06-14
I installed the encryption progam Seahorse in synaptic. I created keys in the program and now I can encrypt files from the the right click menu in nautilus. The files created are in the pgp format but Ubuntu don't now how to open these files. 

How do I open (and decrypt) pgp files? :confused:

---

### Post by JohanSwe on 2006-06-14
Ah, I renamed the file from pgp to gpg and now I can decrypt it. I think that seahorse are suppose to handel pgp files but it didn't work for me. Strange.

---

### Post by sadam on 2006-06-16
[QUOTE=JohanSwe]Ah, I renamed the file from pgp to gpg and now I can decrypt it. I think that seahorse are suppose to handel pgp files but it didn't work for me. Strange.[/QUOTE]

What version of seahorse do you have installed?

Adam

---

### Post by hugmenot on 2006-06-16
Confirmed, go ahead and file a bug. Seahorse should be associated with .pgp files as well.

---

### Post by sadam on 2006-06-16
[QUOTE=hugmenot]Confirmed, go ahead and file a bug. Seahorse should be associated with .pgp files as well.[/QUOTE]

There already is one (from another thread): [https://launchpad.net/distros/ubuntu/+source/seahorse/+bug/42869](https://launchpad.net/distros/ubuntu/+source/seahorse/+bug/42869)

Note: I'm a developer and this works for me in HEAD with Slackware 10.2 and Dropline GNOME 2.14.2.  Also, if it isn't in GNOME Bugzilla, seahorse devs usually will not know about it.

---

### Post by JohanSwe on 2006-06-17
I don't think the link to the bug works. And I couldn't found it at launchpad. Please paste a new link. 

I found where to post bugs for seahorse at bugzilla. What should I describe the bug like?
[http://bugzilla.gnome.org/buglist.cgi?query=product%3Aseahorse+](http://bugzilla.gnome.org/buglist.cgi?query=product%3Aseahorse+)

Also I would like to now what you mean by "works for me in HEAD"?

---

### Post by sadam on 2006-06-17
[QUOTE=JohanSwe]I don't think the link to the bug works. And I couldn't found it at launchpad. Please paste a new link. 
[/QUOTE]

[https://launchpad.net/distros/ubuntu/+source/seahorse/+bug/42869](https://launchpad.net/distros/ubuntu/+source/seahorse/+bug/42869)

> 
I found where to post bugs for seahorse at bugzilla. What should I describe the bug like?
[http://bugzilla.gnome.org/buglist.cgi?query=product%3Aseahorse+](http://bugzilla.gnome.org/buglist.cgi?query=product%3Aseahorse+)


File new bugs for Seahorse at [http://bugzilla.gnome.org/simple-bug-guide.cgi](http://bugzilla.gnome.org/simple-bug-guide.cgi).

> 
Also I would like to now what you mean by "works for me in HEAD"?

Because you didn't tell me what version you are using (as asked for above), I tested your "bug report" with CVS HEAD.  HEAD represents the latest version of the code.  I right clicked on a file and encrypted it to myself, a *.pgp file was created, I double clicked on the pgp file and successfully decrypted it.

---

### Post by JohanSwe on 2006-06-18
Thanks

The name of the package is 0.8.1-0ubuntu4 and the Seahorse version is 0.8.1

How can I describe this bug when fileing it. This is new to me but I'd like to learn.

---

### Post by sadam on 2006-06-18
[QUOTE=JohanSwe]
The name of the package is 0.8.1-0ubuntu4 and the Seahorse version is 0.8.1

How can I describe this bug when fileing it. This is new to me but I'd like to learn.[/QUOTE]

The best way to file a bug is to very carefully describe the steps needed to reproduce the bug.  If it's a "crasher" include a useful stack trace.  Make sure the version of seahorse, version of GNOME are correct as well as notating the distribution with version the bug occurs on.

---

### Post by JohanSwe on 2006-06-18
Thank you sadam.

---

