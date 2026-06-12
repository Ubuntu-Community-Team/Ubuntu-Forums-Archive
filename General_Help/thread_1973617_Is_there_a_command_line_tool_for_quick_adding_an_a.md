---
title: "Is there a command line tool for quick adding an apt line?"
date: 2012-05-05
forum: General Help
---

### Post by redhatlinux10 on 2012-05-05
We all know we can use apt-add-repository to add an apt line just like 'ppa:shutter/ppa', and we also can use ubuntu software center -> edit software resouces -> other softwares -> add to add an apt line just like 'deb [http://ignorantguru.github.com/debian/](http://ignorantguru.github.com/debian/) unstable main'.
but is there a command line tool for 'deb [http://ignorantguru.github.com/debian/](http://ignorantguru.github.com/debian/) unstable main'?
many thanks.

---

### Post by whiskers751 on 2012-05-05
Sudo add-apt-repository

---

### Post by whiskers751 on 2012-05-05
> **whiskers751 said:**
> Sudo add-apt-repository

oh oops!
Try sudo nano /etc/sources.list

---

### Post by haqking on 2012-05-05
> **redhatlinux10 said:**
> We all know we can use apt-add-repository to add an apt line just like 'ppa:shutter/ppa', and we also can use ubuntu software center -> edit software resouces -> other softwares -> add to add an apt line just like 'deb [http://ignorantguru.github.com/debian/](http://ignorantguru.github.com/debian/) unstable main'.
but is there a command line tool for 'deb [http://ignorantguru.github.com/debian/](http://ignorantguru.github.com/debian/) unstable main'?
many thanks.

```
sudo echo "deb [http://ignorantguru.github.com/debian/](http://ignorantguru.github.com/debian/) unstable main" >> /etc/apt/sources.list 

```

---

### Post by haqking on 2012-05-05
> **whiskers751 said:**
> oh oops!
Try sudo nano /etc/sources.list

to edit it manually it would be

```
sudo nano /etc/apt/sources.list
```

or echo to the file as i posted above

---

### Post by Cheesemill on 2012-05-05
```
sudo add-apt-repository 'deb http://ignorantguru.github.com/debian/ unstable main'
```

---

### Post by dragonfly41 on 2012-05-05
I use **[COLOR=DimGray]cli companion[/COLOR]** as my command line tool

---

### Post by plucky on 2012-05-05
> **whiskers751 said:**
> oh oops!
Try sudo nano /etc/sources.list

That would be **sudo nano /etc/apt/sources.list**

---

### Post by Cheesemill on 2012-05-05
> **haqking said:**
> ```
sudo echo "deb [http://ignorantguru.github.com/debian/](http://ignorantguru.github.com/debian/) unstable main" >> /etc/apt/sources.list 

```

I don't think that this will work as the sudo permissions don't carry across the redirection.
Instead I think you would have to use:
```
echo "deb http://ignorantguru.github.com/debian/ unstable main" | sudo tee -a /etc/apt/sources.list
```

---

### Post by haqking on 2012-05-05
> **Cheesemill said:**
> I don't think that this will work as the sudo permissions don't carry across the redirection.
Instead I think you would have to use:
```
echo "deb http://ignorantguru.github.com/debian/ unstable main" | sudo tee -a /etc/apt/sources.list
```

actually yeah you are right, i dont use sudo i just added it cos it was ubuntu ;)

I do as above when i "su" excluding the sudo

Peace

---

### Post by redhatlinux10 on 2012-05-06
> **Cheesemill said:**
> ```
sudo add-apt-repository 'deb http://ignorantguru.github.com/debian/ unstable main'
```
this is what i want. what a shame for that i didn't dive deeper into this command.

---

