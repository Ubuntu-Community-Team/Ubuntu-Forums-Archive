---
title: "wget question"
date: 2010-05-16
forum: General Help
---

### Post by rcayea on 2010-05-16
Hey everyone,

I am currently using Virtualbox here on my ubuntu1004 machine to build Linux From Scratch. 


If anyone is familiar with LFS you know that you may download the packages needed using wget. 

My question is, when I go to use the wget command, it doesn't seem to work. I am sure I am doing something wrong or at least I might be. 
I have tried to type in:
wget -i wget-list, wget -i ./wget-list, wget ./wget-list.

Anyway, you see that I have tried many different combos of the command. 

Any tips would be greatly appreciated.

thanks,
Randy

---

### Post by c9-3Rr0r on 2010-05-16
You should be in directory where list file is located located. Or give full path as a argument for example 

```

wget -i /home/usrename/url_list

```

I hope that helps

---

### Post by rcayea on 2010-05-16
thanks for the info. I'll go give it a try.

---

