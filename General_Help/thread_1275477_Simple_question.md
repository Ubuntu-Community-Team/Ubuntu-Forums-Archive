---
title: "Simple question"
date: 2009-09-25
forum: General Help
---

### Post by accol on 2009-09-25
Hey everyone!

Quick question:  I tried out Linux Mint but didnt like it.  However, I did like how the terminal had that quote thing whenever it opened up.  Is there a website or package I can download to find more things along those lines to do to the terminal?

---

### Post by clonne4crw on 2009-09-25
I don't use Mint, but what is this thing that you're describing?

Is it the Message Of The Day (MOTD)?

---

### Post by j.bell730 on 2009-09-25
It's fortune.

```
sudo apt-get install fortune
```

---

### Post by accol on 2009-09-25
sorta, mint had like an ascii drawing saying something directly above the command line

---

### Post by j.bell730 on 2009-09-25
> **accol said:**
> sorta, mint had like an ascii drawing saying something directly above the command line

Oh, yeah, you also need cowsay.

Get fortune, then...
```
sudo apt-get install cowsay
fortune | cowsay -n
```

---

### Post by accol on 2009-09-25
thanks, but do you know how to set it so that it automatically happens every time I first open the terminal?

---

### Post by j.bell730 on 2009-09-25
```
gksudo gedit /etc/bash.bashrc
```

Add this to the end of the file and save
```
fortune | cowsay -n
echo
```

---

### Post by ad_267 on 2009-09-25
> **accol said:**
> thanks, but do you know how to set it so that it automatically happens every time I first open the terminal?

```
echo "fortune | cowsay -n" >> .bashrc
```

---

### Post by accol on 2009-09-25
omg thanks!!!

---

