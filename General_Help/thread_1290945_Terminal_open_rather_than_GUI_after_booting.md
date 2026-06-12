---
title: "Terminal open rather than GUI after booting"
date: 2009-10-14
forum: General Help
---

### Post by whathaveugot on 2009-10-14
Hi folks,

I got this problem in my Lenovo S10 which has a dual boot of WinXP n UNR 9.04. 

Whenever i'm trying to boot to ubuntu, the GUI is missing, instead the terminal opens with login prompts. Its showing something like "no image....". Could any1 plz tell me what exactly happened an how do I get out of this mess.

Also, FYI, I installed Apache5/PHP5 4 days back. The problem actually started after that, to be precise. Another thing that I noted was when I tried to reboot from root. Just before rebooting it showed: "no Apache MPM installed". So I reckon that there's a high chance the Apache installed is pretty screwed up.

I tried using xfix in the recovery mode but it didn't helped much.

Somebody plez help!!!!

Cheers.

---

### Post by hal10000 on 2009-10-14
It' unlikely that apache or php is the problem here. Did you install them with your package-manager (e.g. synaptic)? Look in synaptic if the package [COLOR="Red"]apache2-mpm-worker[/COLOR] is installed, if not, then install it (btw. there is no apache5, just apache2).

To come to your problem, what happens if you type [COLOR="Red"]gdm[/COLOR] or [COLOR="Red"]sudo gdm[/COLOR]? Does it start normally? If not, what happens if you type [COLOR="Red"]startx[/COLOR]?

Also, post the output of the command [COLOR="Red"]who -r[/COLOR]

---

### Post by whathaveugot on 2009-10-14
> **hal10000 said:**
> It' unlikely that apache or php is the problem here. Did you install them with your package-manager (e.g. synaptic)? Look in synaptic if the package [COLOR="Red"]apache2-mpm-worker[/COLOR] is installed, if not, then install it (btw. there is no apache5, just apache2).

To come to your problem, what happens if you type [COLOR="Red"]gdm[/COLOR] or [COLOR="Red"]sudo gdm[/COLOR]? Does it start normally? If not, what happens if you type [COLOR="Red"]startx[/COLOR]?

Also, post the output of the command [COLOR="Red"]who -r[/COLOR]

hey,

the package apache2-mpm-worker is installed. And when I fired the startx command the GUI appeared but I think there's still some problem coz when I tried to connect to internet using the USB modem of d service provider, a prompt appeared asking for password for the USB key, which had never happened before coz there's no passwd for it.


And here are the outputs of the other two commands:

[B]$ sudo gdm
sudo: gdm: command not found
[/B]

[B]$ who -r
    run-level 2 2009-10-14 20:40   last=
[/B]

And, just FYI, here is a snippet of the screenshot from my boot up:

[B]....
....
19 + 0 records in
19 + 0 records out

kinit: name_to_dev_t(/dev/disk/by-uuid/.........) = dev(8, 10)

kinit: trying to resume from /dev/disk/by-uuid/.....

kinit: No resume image, doing norma boot....

ubuntu 9.04 tty1

login:[/B]

what do you suggest now?

Cheers.

---

### Post by hal10000 on 2009-10-14
> $ sudo gdm
sudo: gdm: command not found

gdm or kdm or xdm are display managers. you need one of them to get a graphical login screen.

Most people use gdm, so try to install it (if you have none of them):
sudo apt-get install gdm

---

### Post by whathaveugot on 2009-10-14
> **hal10000 said:**
> gdm or kdm or xdm are display managers. you need one of them to get a graphical login screen.

Most people use gdm, so try to install it (if you have none of them):
sudo apt-get install gdm

but I need to get my internet working for sudo-apt to work. I dont know how am I supposed to do that.

---

### Post by hal10000 on 2009-10-14
Did your internet connection ever work?
Does it work if you boot your ubuntu live-cd?
Usually you have to configure your internet connection with your network-manager, filling in the information you have got from your provider.
Which desktop envirenment do you use (xfce, gnome, kde or what else)?

---

### Post by whathaveugot on 2009-10-15
yeah it worked well earlier but now its asking for passwd to connect....I entered as root and it was configured again...this time it asked me to create a default keyring which I skipped and hence it's not working in root too....can you tell me how do I configure the keyring and also where do I remove/edit this connection from....

about the desktop....I reckon its gnome. And one thing more, I checked in the services option where I found that gdm was installed and running....so I was wondering why did the command (sudo gdm) failed earlier.

---

### Post by P4man on 2009-10-15
you've mentioned root a few times.. did you try and make a root account or log in as root, or change root password? If so, you probably messed up badly.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by whathaveugot on 2009-10-18
> **P4man said:**
> you've mentioned root a few times.. did you try and make a root account or log in as root, or change root password? If so, you probably messed up badly.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I did login as root by using the command "sudo -s" but I didn't created one, I just used the default.

---

