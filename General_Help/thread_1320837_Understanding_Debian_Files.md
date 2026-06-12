---
title: "Understanding Debian Files"
date: 2009-11-09
forum: General Help
---

### Post by rfkrocktk on 2009-11-09
I'm looking to create my own debian repository as a convenience to the community and to myself to make it very easy to install applications that I commonly use (think "rfkrocktk-desktop"). 

I had a question about how to create preinst and postinst scripts. All attempts at running commands within these scripts has resulted in problems I've had to manually fix within my OS. As a nice way to start learning the debian file format and how to package programs for debian-based operating systems, I have decided to make packages that install repositories. 

So, how would I do this? I assume the simplest route is to just include a file in my deb files within /etc/apt/sources/list.d/* that will get copied there when installed. However, I usually get warnings when trying to compile deb files like this. Can anyone help me out with this? I have been reading the Debian documentation but it seems to leave out a lot of important information related to this.

---

