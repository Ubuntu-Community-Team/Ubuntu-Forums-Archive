---
title: "Problem adding PPA"
date: 2012-07-01
forum: General Help
---

### Post by em wai zee on 2012-07-01
Hi ... This probably a cliche question. But, here it goes ... I just installed a fresh Ubuntu 12.04 into my lappie. The problem I'm getting while trying to add new PPAs into my Software Centre. Here was one my example while trying adding a PPA!

> sudo add-apt-repository ppa:scopes-packagers/ppa

> Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (35, 'gnutls_handshake() failed: A TLS packet with unexpected length was received.')


Could anyone here lead me to a set of instructions that will solve this problem immediately! Thanks a lot! 

p.s; I've uploaded a screenshot of the problem!

---

### Post by em wai zee on 2012-07-02
Hi, it's me again ... I have new problem now, since I'd not add any PPAs to my Software Center. So, it has raised new problem when I tried to update my Ubuntu. Attached is a snapshot of the problem. Please anyone that could help me with this. Thanks!

---

### Post by cwsnyder on 2012-07-02
I don't want to assume anything here, but you do know that PPAs are version specific?  If the scopes-packagers PPA does not support Precise, adding the PPA can do all kinds of bad things when you next try to update your packages.

---

### Post by stinkeye on 2012-07-02
> **em wai zee said:**
> Hi, it's me again ... I have new problem now, since I'd not add any PPAs to my Software Center. So, it has raised new problem when I tried to update my Ubuntu. Attached is a snapshot of the problem. Please anyone that could help me with this. Thanks!

Because you have enabled the  **ppa:nilarimogard/webupd** at some stage 
to install something.

If those updates are unwanted and you don't want them to show up in update manager,
click on settings at the bottom left and
disable the ppa:nilarimogard/webupd

---

