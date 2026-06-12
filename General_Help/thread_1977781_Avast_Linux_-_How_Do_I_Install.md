---
title: "Avast Linux - How Do I Install?"
date: 2012-05-10
forum: General Help
---

### Post by sen0140 on 2012-05-10
Hi there, its been a while since I last used Ubuntu and I remember setting up this Avast before but I forgot.  Anyways I downloaded the .deb file but I can't do anything with the file after that, if anyone could help me out I'd really appreciate, thanks.

---

### Post by watgrad on 2012-05-10
I have never encountered virus problems with ubuntu - would adding a virus shield maybe cause more problems that it prevents?

---

### Post by sen0140 on 2012-05-10
Yea I know but I guess I would just like to still know how to install programs like this if I ever needed to.

---

### Post by Penguinnerd on 2012-05-10
You need to install the .deb file using gdebi.

You should be able to do this through right-clicking the file.

If you don't have gdebi, use this to get it:

```

sudo apt-get install gdebi

```

In 12.04, they expect people to use the software centre for this, but it often messes up. (When handling .deb files) I know I can count on gdebi to work.

---

### Post by wilee-nilee on 2012-05-10
> **sen0140 said:**
> Hi there, its been a while since I last used Ubuntu and I remember setting up this Avast before but I forgot.  Anyways I downloaded the .deb file but I can't do anything with the file after that, if anyone could help me out I'd really appreciate, thanks.

Download the debi from here get a key from avast and install.
[http://www.avast.com/linux-home-edition#](http://www.avast.com/linux-home-edition#)

You will need to modify a file as well to run it, it will run the first time but error out without this modification when started again.

Run this command to open it and put the next notation at the bottom and save it.

[COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]sudo gedit /etc/sysctl.conf[/SIZE][/FONT][/COLOR]

                                   [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]kernel.shmmax = 128000000[/SIZE][/FONT][/COLOR]

Then run this command to load it , a restart will do the same.

[COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]sudo sysctl -w kernel.shmmax=128000000[/SIZE][/FONT][/COLOR]

---

### Post by sen0140 on 2012-05-10
> **Penguinnerd said:**
> You need to install the .deb file using gdebi.

You should be able to do this through right-clicking the file.

If you don't have gdebi, use this to get it:

```

sudo apt-get install gdebi

```In 12.04, they expect people to use the software centre for this, but it often messes up. (When handling .deb files) I know I can count on gdebi to work.

I installed gdebi but I get an error message that says Error: Wrong architecture 'i386'

Also when downloaded the file and I went to the terminal and typed sudo dpkg -i filename but that wouldnt work either.

---

### Post by sen0140 on 2012-05-10
> **wilee-nilee said:**
> Download the debi from here get a key from avast and install.
[http://www.avast.com/linux-home-edition#](http://www.avast.com/linux-home-edition#)

You will need to modify a file as well to run it, it will run the first time but error out without this modification when started again.

Run this command to open it and put the next notation at the bottom and save it.

[COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]sudo gedit /etc/sysctl.conf[/SIZE][/FONT][/COLOR]

                                   [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]kernel.shmmax = 128000000[/SIZE][/FONT][/COLOR]

Then run this command to load it , a restart will do the same.

[COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]sudo sysctl -w kernel.shmmax=128000000[/SIZE][/FONT][/COLOR]

Alright I'll try this but I don't recall doing this the first time when I got avast to work, isn't there another way?  Also its the free edition avast if that makes a difference lol.

---

### Post by wilee-nilee on 2012-05-10
> **sen0140 said:**
> Alright I'll try this but I don't recall doing this the first time when I got avast to work, isn't there another way?  Also its the free edition avast if that makes a difference lol.

Not that I know of it may be fixed now so this is not needed, but for a while it was, I just automatically do it myself as I add a few other things like a swappiness change.

I got this from the avast forum originally.

---

### Post by Rytron on 2012-08-13
Can anyone get the latest updates for Avast Linux (they are currently dating back to 2009)? I tried to update but got this message.

---

