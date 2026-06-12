---
title: "installing tgif"
date: 2012-09-30
forum: General Help
---

### Post by mayne on 2012-09-30
I have recently installed ubuntu 12.04 on a dell computer using a cd.

Using synaptic I installed the graphics package tgif

When I execute tgif (which I have successfully intalled
on other computers) I get the message:


mayne@desktop:~$ tgif
Fatal Error in OpenFont(): Cannot open the Default(Msg)Font '-*-courier-medium-r-normal-*-14-*-*-*-*-*-iso8859-1'.
Tgif aborted.


What should I do?

Thank you

David Mayne

---

### Post by drmrgd on 2012-10-01
Looks like you're  missing the font the program wants.  I'm not 100% sure, but I think Courier is in the MS TTF fonts package.  Try installing that to see if it fixes the problem:

```
sudo apt-get install ttf-mscorefonts-installer
```

During the installation you'll be presented with a EULA.  If you intend to accept the EULA (no reason not to!), you'll need to hit the Tab key to highlight the "yes" button, and then just press enter to accept.

Hope that helps!

---

### Post by daslinkard on 2012-10-01
Did DRMRGD's suggestion work for you?

---

### Post by mayne on 2012-10-02
DRMRGD

Sorry for the delay in answering ... I mislaid my password.

Your suggestion was probably right. From the web I saw I should

download latex-extra-utils (or something like this) which I did

and that solved the problem.

Thank you very much for making the effort to reply to my naive request.

David

---

### Post by daslinkard on 2012-10-02
> **mayne said:**
> DRMRGD

Sorry for the delay in answering ... I mislaid my password.

Your suggestion was probably right. From the web I saw I should

download latex-extra-utils (or something like this) which I did

and that solved the problem.

Thank you very much for making the effort to reply to my naive request.

David

Glad this is resolved....please mark this thread as solved!

---

### Post by drmrgd on 2012-10-02
> **mayne said:**
> DRMRGD

Sorry for the delay in answering ... I mislaid my password.

Your suggestion was probably right. From the web I saw I should

download latex-extra-utils (or something like this) which I did

and that solved the problem.

Thank you very much for making the effort to reply to my naive request.

David

No problem at all!  Glad to help!

---

### Post by manadi on 2012-11-10
What exactly was the solution to this? I am having same problem, I installed "ttf-mscorefonts-installer" and "texlive-latex-extra" packages but error remains.

---

### Post by manadi on 2012-11-11
It seems it needed a restart after installing those packages. Works now.

---

