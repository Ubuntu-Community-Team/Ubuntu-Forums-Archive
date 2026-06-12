---
title: "How to install view.gtk on Ubuntu?"
date: 2012-07-22
forum: General Help
---

### Post by khankamil19 on 2012-07-22
Hi,
  I found this site very helpful and I appreciate the quick response of community members.
I am not an expert in ubuntu but still I need it strongly. 
There is a software x9.nsls.bnl.gov/software/download/view.gtk.tar.gz available from this link which minimizes the time while I do scientific analysis of my data at synchrotron. but the problem is that I cannt be everytime at synchrotron so I want to install it on ubuntu.
I have some requests here, which I think that only you can good guiadance.
1. Please check software, extract it and read the readme file. and post it whether it can be installed on ubuntu or not?

2. As it requires gtk+-2.0, and libtiff. can you please [COLOR=Red]make a tutorial[/COLOR] on how to install these in ubuntu. I searched this site wholly and came across that many people have problem with the installation of these packages. Also, many people need these packages for various purposes. I think that making a tutorial will be a worth-while. 

Thanks

waiting for your response,

khankamil

---

### Post by CharlesA on 2012-07-22
You can run this:

```
sudo apt-get install gtk+2.0
```

It will pull in a ton of dependencies tho.

---

