---
title: "error message that public key is not available"
date: 2010-05-17
forum: General Help
---

### Post by RedRat on 2010-05-17
OK I get the following when I am in synaptic and have it reload:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D725E4885719E347

I recall that there is a command line to over come this but cannot remember what it is. I tried a search here in the forum for "public key" but it returns stuff that is not germane to this problem. Any suggestions out there how to do this.

---

### Post by drs305 on 2010-05-17
Here's one way:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9BDB3D89CE49EC21 D725E4885719E347
```

An efficient way of searching is to use a bit more of the exact error message in Google or in the forum's own search box.

---

### Post by sisco311 on 2010-05-17
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5719E347
sudo apt-get update
```

---

### Post by colorlessprism on 2010-05-17
funny/sad thing is i made a HOW-TO 5days ago pertaining to this exact topic, so here it is:

recently both here and on launchpad i have noticed a number of people  experiencing GPG errors. i've looked around an decided to consolidate  some information in hopes of helping people out.
   
_**PPA GPG ERROR FIXES:**_

[LIST]
[*]Dominic Evans script launchpad-update (see attached). save this  script and run it if you find yourself needing GPG keys, this is the  fastest way to update key information. it works for current ppas but  add-apt-reposiroty may soon replace it.
[/LIST]
 
[LIST]
[*]to fix these errors in _lucid_ use "sudo  add-apt-repository ppa:<repository name>" this registers the ppa  with APT and an entry is created in /etc/apt/sources.list  and backs up  to /etc/apt/sources.list.save. ff a key is required and available it is  automatically downloaded and  registered. you must have  "python-software-properties" installed before using this command
[/LIST]
 
[LIST]
[*] you can go to the ppa page click on the green link saying  "technical  details about this PPA", select your version from  the drop  down, click the "Signing Key" link and it should take you to a  keyserver page. Copy and paste gpg public code to your favorite editor,  and  save it.  open "software sources" and select "authentication" click  the "Import Key File", and select the  file you just saved. now reload  your sources
[/LIST]

---

### Post by RedRat on 2010-05-17
Thanks to all who replied here. I should have used "GPG Error" instead of "public key". Thanks for that suggestions.

---

