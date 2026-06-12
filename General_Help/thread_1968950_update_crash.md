---
title: "update crash"
date: 2012-04-29
forum: General Help
---

### Post by johnnybevo on 2012-04-29
ok i did something wrong. 
How do I fix it?



E: Type 'b-src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
E: The list of sources could not be read.

---

### Post by matt_symes on 2012-04-29
Hi

Open a terminal and type

 ```
cat /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
```

Copy and paste the results from the terminal (highlight text->right click -> copy) back here.

Kind regards

---

### Post by johnnybevo on 2012-04-29
> **matt_symes said:**
> Hi

Open a terminal and type

 ```
cat /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
```

Copy and paste the results from the terminal (highlight text->right click -> copy) back here.

Kind regards

this is what i get

b-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main

---

### Post by matt_symes on 2012-04-29
Hi

Open a terminal and type (or copy and paste)

```
sudo sed -i 's/b-src/deb/g' /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
```

Enter your password. It will not be echoed to the screen.

Then type 

```
sudo apt-get update
```

Kind regards

---

### Post by johnnybevo on 2012-04-29
> **matt_symes said:**
> Hi

Open a terminal and type (or copy and paste)

```
sudo sed -i 's/b-src/deb/g' /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list
```

Enter your password. It will not be echoed to the screen.

Then type 

```
sudo apt-get update
```

Kind regards


Oh wow that did it. thank you very very much.

I have a lot to learn.
I had set up a wubi about a year ago and just did not use it.
I installed 11.10 about a week or two ago then upgraded to 12.04 and decided to leave windows behind, nothing else on this machine now but linux.
Even with the learning curve I not sure I will ever go back to windows.

---

