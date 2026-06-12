---
title: "Restricted extras"
date: 2012-09-27
forum: General Help
---

### Post by rickm1945 on 2012-09-27
I installed the Ubuntu Restricted Extras but do not have the True type fonts. I checked Libre office writer and the fonts were the default fault fonts. Any ideas on this problem?

---

### Post by drmrgd on 2012-09-27
Perhaps when you installed, you didn't accept the EULA and the fonts weren't installed?  Try running:

```
sudo apt-get install ttf-mscorefonts-installer
```

If they weren't installed, you'll be able to install them with that.  If they were installed, and it's a bit of a long shot, but you could try updating your font cache:

```
sudo fc-cache -f
```

---

### Post by coffeecat on 2012-09-27
As drmrgd said, you may have missed the EULA. If you get a message saying that ttf-mscorefonts-installer is already installed when you run "sudo apt-get install ttf-mscorefonts-installer", try this instead:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

Did you install ubuntu-restricted-extras from the terminal or from Software Centre? If from the terminal, you need to use the TAB key to move around the EULA and then ENTER to accept it. This is what you will see if you run the above command.

---

### Post by rickm1945 on 2012-09-30
> **coffeecat said:**
> As drmrgd said, you may have missed the EULA. If you get a message saying that ttf-mscorefonts-installer is already installed when you run "sudo apt-get install ttf-mscorefonts-installer", try this instead:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```Did you install ubuntu-restricted-extras from the terminal or from Software Centre? If from the terminal, you need to use the TAB key to move around the EULA and then ENTER to accept it. This is what you will see if you run the above command.
  I tried to reinstall and it brought up the EULA, but there was no way to accept it. There was an <ok> at the bottom but I hit enter and nothing happened, and couldn't click on it. Sorry for not getting back here sooner.

---

### Post by coffeecat on 2012-09-30
> **rickm1945 said:**
> I tried to reinstall and it brought up the EULA, but there was no way to accept it. There was an <ok> at the bottom but I hit enter and nothing happened, and couldn't click on it.

> **coffeecat said:**
> If from the terminal, you need to use the TAB key to move around the EULA and then ENTER to accept it.

If I remember correctly, using the TAB key should highlight the OK, which will then respond when you press enter.

---

### Post by rickm1945 on 2012-09-30
> **coffeecat said:**
> If I remember correctly, using the TAB key should highlight the OK, which will then respond when you press enter.
You are right the tab key does the trick, thank you for the help. All the fonts installed.

---

