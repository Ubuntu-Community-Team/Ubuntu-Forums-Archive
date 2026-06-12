---
title: "ubuntu server + ubuntu-desktop"
date: 2010-11-07
forum: General Help
---

### Post by sim085 on 2010-11-07
Hello, I was wondering, is installing ubuntu server edition and then install ubuntu-desktop (apt-get install ubuntu-desktop) on top of this the same as directly installing ubuntu desktop?

---

### Post by 3Miro on 2010-11-07
No. They are not the same.

Ubuntu desktop refers to the Gnome desktop with the themes, applications, panels, menus etc. This will look exactly like the regular desktop. However, the server edition comes with a different build for the kernel. Servers and desktop computers are used in a different manner so there are different parameters regarding CPU scheduling. That will be different. There may be other programs that are installed by default on the server and not on the desktop (I am not sure what those are, but I think ssh-server will be one of them).

---

### Post by sim085 on 2010-11-07
> **3Miro said:**
> No. They are not the same.

Thanks for your reply. I want to install a linux distro to use for the development of web applications. This means that I need a gui but also applications such as the apache webserver. At the moment what I'm doing is this; install ubuntu server edition and then on top of that install xubuntu. However I am not sure if that is the right way forward which is I went to ask this question.

---

### Post by oregonbob on 2010-11-07
Hi Sim085, your installation desires are probably like most in here. My bet is you want to install ubuntu-desktop and then carefully add the services you want such as apache, mysql etc. Most of my machines are for the same purpose. Lately I discovered that if I have desktop and tell it to install some server packages it REMOVES desktop without asking me - a horrible experience. I still accomplished what I needed but always watch when adding packages for lines that say "To be removed: package_blah_blah"

After you install ubuntu-desktop, use the Synaptic Package Manager on the menu and adding packages is easy.

---

