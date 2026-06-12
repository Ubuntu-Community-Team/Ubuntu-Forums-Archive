---
title: "Log in problem"
date: 2011-10-05
forum: General Help
---

### Post by terence201 on 2011-10-05
I am using the ubuntu 11.04. I have been using it for few weeks.
Today when i click "switch user", and i expect that i will be prompted to the login page. However, nothing come out. it just freeze with the default ubuntu background.
Therefore i power off my laptop and do a reboot. when it launch to the login screen, it is still the same, the login box just doesn't appear. I am not able to login to the account.

i wonder how i can able to login again. Thanks.

---

### Post by Mark Phelps on 2011-10-05
Next time you reboot, hold down one of the SHIFT keys until you see the GRUB menu.

Then, select the top-most Recovery option.

After you go through the recovery steps, you should be able to reboot and get a login after that.

---

### Post by terence201 on 2011-10-05
thanks for reply. i am actually dual boot with windows 7. 
i did try the recovery mode. try a lot of other methods like startX. but the result is the same. the login menu is just not loaded. However, i am still able to login to my account in the terminal from the recovery mode, just that no gui. I need gui in order to continue my work.

---

### Post by dino99 on 2011-10-05
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo apt-get install --reinstall ubuntu-desktop

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

---

