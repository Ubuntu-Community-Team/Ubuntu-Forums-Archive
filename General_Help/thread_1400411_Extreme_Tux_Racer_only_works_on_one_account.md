---
title: "Extreme Tux Racer only works on one account"
date: 2010-02-06
forum: General Help
---

### Post by Revolutionary101 on 2010-02-06
Hello everyone I have a problem on my computer. My young nephew changed some settings (doesn't know what he did) on his account and now Extreme Tux Racer will not work on his account, but it will work on my account. When he tries to run Extreme Tux Racer the screen goes black and the computer locks up. Could anyone help?

---

### Post by mushwars on 2010-02-06
he needs to be in the games group here is how to do that.

```
gpasswd -a nephew games
```then his account has to be logged out and back in again.

cheers.

edit: he might not be in the video group either, here is how to check 
```
mushwars@mushwars ~ $ groups mushwars
wheel audio video users website vboxusers games mushwars

```

---

### Post by n0dix on 2010-02-06
Try to reinstall the game.

---

### Post by mushwars on 2010-02-06
> **n0dix said:**
> Try to reinstall the game.
That is one way to do it, if for instance your nephews account was made AFTER the installation of the game that might just do it.

```
sudo apt-get purge extremetuxracer
sudo apt-get install extremeturxracer
```

you could also try copying your .tuxracer <--- not sure if that is what it is I dont have it installed
folder in your ~/.tuxracer to his home folder 

```
sudo cp -R ~/.tuxracer /home/nephew/
sudo chown -R nephew /home/nephew/.tuxracer
```

---

### Post by Revolutionary101 on 2010-02-06
I solved it all I had to do was change the configuration of the game back to its default configuration via terminal. I tried to reinstall the game but it didn't do anything, but thanks for the help.

---

