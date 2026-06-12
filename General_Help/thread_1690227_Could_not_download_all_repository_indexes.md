---
title: "Could not download all repository indexes"
date: 2011-02-18
forum: General Help
---

### Post by Steve Moss on 2011-02-18
Hi

I am using version 10.4 LTS

When I run check in the update manager I get the error message 

Could not download all repository indexes

With details as follows 

Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

Is this a problem that needs to be fixed?

---

### Post by jerrrys on 2011-02-19
go to system>admin>synaptic package manager 

and click on the reload button

---

### Post by Steve Moss on 2011-02-19
Thanks for the reply :))

Basically thats what I did so I get the same error message

---

### Post by jerrrys on 2011-02-19
there has been other post on update manager acting up and this would work.  with you, no such luck

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Something+wicked+happened&as_qdr=all&sa=Google+Search&lang=en#836]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Something+wicked+happened&as_qdr=all&sa=Google+Search&lang=en#836")

---

### Post by Steve Moss on 2011-02-19
Thanks jerrys the linked provided the answer

I changed the Google DNS settings

---

