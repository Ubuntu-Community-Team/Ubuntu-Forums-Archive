---
title: "how to remove edubuntu from ubuntu"
date: 2006-03-31
forum: General Help
---

### Post by babyboss on 2006-03-31
I was so curious about edubuntu, and I did what the Ubuntu FAQ suggests to do to install edubuntu. Now, I feel like returning back to ubuntu. How can I do that?

---

### Post by babyboss on 2006-04-01
nobody tried it before?

---

### Post by alamba on 2006-04-01
What steps did you take to install it? apt-get/synaptic?

A

---

### Post by babyboss on 2006-04-02
sudo apt-get install edubuntu-destop
simply this step.

I tried:
sudo apt-get remove edubuntu-destop

it says the package does not exist

also, when you turn on your computer, and on the screen of login, after you log in, you have to wait a bit. Usually, there is a quick flash of a Ubuntu banner, and on the banner, it shows the activation of devices, and basic programs... do u know how i can change that banner to something else?

---

### Post by Ramses de Norre on 2006-04-02
edubuntu-desktop is a meta package, it installs a lot of other packages which you'll need to remove manually again..

---

### Post by babyboss on 2006-04-03
how do I remove them manually?

---

### Post by mcmillan on 2006-04-03
You can look up the dependencies of edubuntu-desktop to see what all it installs. Some of it will be things you already had installed and should keep though. So it's not as simple as just removing all of those packages. But any that you don't want to keep you should remove.

---

