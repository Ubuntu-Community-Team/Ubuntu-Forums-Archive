---
title: "Program removal"
date: 2010-12-14
forum: General Help
---

### Post by paulcos on 2010-12-14
I recently tried to install USHARE on my computer,but during install i lost power.Now my computer freezes at the log in screen.I have tried pkill and a few others but i am getting nowhere.PLEASE HELP.I can get my system to work in low graffix mode but thats it!

---

### Post by sanderd17 on 2010-12-14
you can get the login screen, so when you press CTRL+ALT+1, you get into a terminal?

Could you login and try some aptitude commands? Start with the

```

sudo aptitude safe-upgrade

```

This will try to update your packages and maybe find the broken one.

---

### Post by paulcos on 2010-12-14
when i do this i get dpkg was interrupted,you must manally run sudo dpkg --configure -a.But when i do this nothing happens!my hardrive goes into overdrive but ive left it for 2 hours and nothing has happened!

---

### Post by garvinrick4 on 2010-12-14
#Boot into recovery with network: Login:
```

[CODE]sudo apt-get purge <packagename>
``````
sudo dpkg --configure -a
``````
sudo apt-get -f install
``````
sudo apt-get update && sudo apt-get upgrade
``````
sudo reboot
```[/code]
##edit on first line apt-get

---

### Post by synicalx on 2010-12-14
> **sanderd17 said:**
> you can get the login screen, so when you press CTRL+ALT+1, you get into a terminal?

Could you login and try some aptitude commands? Start with the

```

sudo aptitude safe-upgrade

```

This will try to update your packages and maybe find the broken one.

Definitely try this.

If that doesn't work, your best bet would be to create a new CD/USB boot device and repair using that

---

### Post by paulcos on 2010-12-14
Tried sudo prge ushare.Get sudo purge command not found

---

### Post by paulcos on 2010-12-14
Is there not anyway to kil ushare in the terminal?

---

### Post by matt_symes on 2010-12-14
Hi

 > sudo prge ushare

A small typo i think. Should be

```

 sudo apt-get purge ushare
```

Kind regards

---

### Post by sanderd17 on 2010-12-14
> **paulcos said:**
> Tried sudo prge ushare.Get sudo purge command not found

it should be 
```

sudo aptitude purge ushare

```

*Edit: Matt_symes, you beat me to it, @OP: aptitude and apt-get are more or less equivalent. aptitude is more debian-ish en apt-get more ubuntu-ish*

---

### Post by paulcos on 2010-12-14
> **sanderd17 said:**
> it should be 
```

sudo aptitude purge ushare

```

*Edit: Matt_symes, you beat me to it, @OP: aptitude and apt-get are more or less equivalent. aptitude is more debian-ish en apt-get more ubuntu-ish*

when i try this i get E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by matt_symes on 2010-12-14
Hi

At the terminal type

```
sudo dpkg --configure -a
```

Kind regards

---

### Post by paulcos on 2010-12-14
> **matt_symes said:**
> Hi

At the terminal type

```
sudo dpkg --configure -a
```

Kind regards

I have tried this but i left it for over an hour,and it just seems to get stuck.Do you have any idea this process should take?

---

### Post by matt_symes on 2010-12-14
Hi

Sorry i missed your post about that. Well, it should not take an hour, and quite why it is i am not sure.

I have never used uShare and i am not sure what it is, so i am not the best person to give advice.

Maybe you could remove the package manually and then reinstall, but lets see if anybody has any better ideas.

Kind regards

---

