---
title: "remove desktop environment completely"
date: 2012-03-10
forum: General Help
---

### Post by Fintican on 2012-03-10
Hi there,

  I have experimented a little with lxde as alternative DE. Finally I have decided to remove it. During installation apt-get had written that about one hundread megabytes are going to be used.

 This is what I use to remove it

```
 sudo apt-get --purge remove lxde 
```During removal about 20 megabytes where removed. Then I have run

```
 sudo apt-get autoremove 
```and another about 10 megabytes where gone. I though that's all but then I have run

```
 sudo dpkg -S lxde 
```and it yielded a list of about 60 packages plainly belonging to lxde. I want to try other environments as well and I do not want to have half packages left on disk after each try. So I want to remove them. I tried to remove orphanded packages as well but

```
 deborphan  
```has found just two packages unrelated to lxde. I don't believe that package manager doesn't remember which packages where installed because I asked to and which where installed to satisfy dependencies. But if it is so than there is no problem to somehow remove all packages which I did'nt ask to isntall and there is nothing which depends on them now...

  but I am not able to find how that can be done.
  please advise
  thnks in advance

---

### Post by raja.genupula on 2012-03-10
what's your original Environment ?

OK see this [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Fintican on 2012-03-10
1. I have unity installed. Currently trying xfce.

2. I went to the link you posted couple of times. But it is useless to me because in remove command for lubuntu there are packages which was already installed before lxde and I want to keep them.

3. I don't want to go through long list of packages and check them. They are computers to do so. I believe package manager has all the information needed as I wrote in first post.

4. Moreover I don't need the list of packages to remove. I could remove the packages with lxde in their name. I hope that there is a systematic way to do it. Removing packages no longer needed is vital part of package management....

---

### Post by raja.genupula on 2012-03-10
hi do this 
```
(apt-cache depends lubuntu-desktop; apt-cache depends ubuntu-desktop; apt-cache depends ubuntu-desktop) | cut -d ‘:’ -f 2 | tr -d [:blank:] | sort | uniq -u | tr [:space:] ‘ ‘ | xargs sudo apt-get -y purge
```

while i am in Ubuntu 11.10 testing i have posted a thread on specific Envi and mc4man & Mise gave me this solution . Thanks guys . 

@Op i am sure that gonna help you .

---

### Post by Fintican on 2012-03-11
Hi, thank you that is definitely way to go. But I am a little surprised. I though that this stuff si more automated. Maybe there is something I am missing why it is not so easy to do.

  I have made a few corrections to your command. Now it looks like this

```
apt-cache depends lxde | cut -d: -f 2 | tr -d [:blank:] | grep -v "^<" | sort | uniq -u | tr [:space:] ' ' | xargs sudo apt-get -y purge
```Delimiter to cut was malformed and I added that grep to remove entries like "<something>"

 thanks for help

---

