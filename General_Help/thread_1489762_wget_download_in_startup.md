---
title: "wget download in startup"
date: 2010-05-21
forum: General Help
---

### Post by 5p1d0r on 2010-05-21
hi all
i try to make wget download automatic in startup in ubuntu
that someone can help me thanks:confused::confused:

---

### Post by wojox on 2010-05-21
What do you want it to automatically get?

---

### Post by Chesamo on 2010-05-21
Let your filename be *foo.file* and your username be *example*.
```
$ echo "wget http://example.com/foo.file -O /home/example/foo.file" > script.sh
$ chmod +x script.sh
$ sudo mv script.sh /etc/init.d/
$ sudo update-rc.d script.sh defaults
```

---

### Post by 5p1d0r on 2010-05-22
> **Chesamo said:**
> Let your filename be *foo.file* and your username be *example*.
```
$ echo "wget http://example.com/foo.file -O /home/example/foo.file" > script.sh
$ chmod +x script.sh
$ sudo mv script.sh /etc/init.d/
$ sudo update-rc.d script.sh defaults
```

it not working on me 
this my code
```
echo "wget -m  ftp://ftp.ifremer.fr/ifremer/cersat/products/gridded/mwf-blended/data/6-hourly/" > data.sh
i already do step by step that you post
but not working 
any idea thanks alot

```

---

### Post by 5p1d0r on 2010-05-22
> **wojox said:**
> What do you want it to automatically get?

yes i want wget automatically download file in start up

---

### Post by Chesamo on 2010-05-24
You can't download an entire directory through wget.

---

### Post by 5p1d0r on 2010-05-25
> **Chesamo said:**
> You can't download an entire directory through wget.
I do not understand, can you review my code thanks

---

### Post by dino99 on 2010-05-25
have you tried with webhttrack instead ? (synaptic repo)

---

### Post by 5p1d0r on 2010-05-25
> **dino99 said:**
> have you tried with webhttrack instead ? (synaptic repo)

its not about download file, its done. my problem is how to start download in start up

---

