---
title: "Root password problem."
date: 2012-07-23
forum: General Help
---

### Post by KaisaUbun2 on 2012-07-23
So I attempted to install my Dell Network printer through the dell drivers Ran it in the command terminal etc. everything fine and I'm enjoying my very minor victory until the Root password screen comes up which you always have to enter during updates and basially everything so i put my password in and it says it's incorrect I try it 3 more times very slowly always wrong i open my terminal and type in Sudo su to get me into the root to see if it accepts my password there and it does I try again in the dell one incorrect password any solutions? without me having to go into Linux Recovery mode and drop to root shell?

---

### Post by raja.genupula on 2012-07-23
anything with a restart ??

---

### Post by KaisaUbun2 on 2012-07-23
> **raja.genupula said:**
> anything with a restart ??

I tried that I can login just fine. Which leads me to believe that if I change my password as root user it wouldn't help much either.

---

### Post by SlugSlug on 2012-07-23
not sure what your talking about but..

your password is not root's password

Is it asking for the root passowrd??

maybe try 

```
sudo passwd PASSWORD
```

and then give the program that password (root's password)?

turn root account off again with

```
sudo passwd -l
```

---

### Post by KaisaUbun2 on 2012-07-23
> **SlugSlug said:**
> not sure what your talking about but..

your password is not root's password

Is it asking for the root passowrd??

maybe try 

```
sudo passwd PASSWORD
```and then give the program that password (root's password)?

turn root account off again with

```
sudo passwd -l
```

Now I'm not sure what you're asking. I figured it would be something like that my password is not the root password I just assumed it was since it was the only password I set, How would I set a root password

However it really just says i need administrative privileges and I am the administrator, on the admin user, using the admin password.

---

### Post by oobuntuck on 2012-07-23
I followed instructions on this page and it gets the job done everytime:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[FONT=Courier New]sudo -i
sudo passwd root
[/FONT]and when done,
[FONT=Courier New]sudo passwd -dl root[/FONT]Just make sure you do disable the root account as above when done. The gurus emphasize on this for safety purposes.

---

### Post by KaisaUbun2 on 2012-07-23
> **oobuntuck said:**
> I followed instructions on this page and it gets the job done everytime:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[FONT=Courier New]sudo -i
sudo passwd root
[/FONT]and when done,
[FONT=Courier New]sudo passwd -dl root[/FONT]Just make sure you do disable the root account as above when done. The gurus emphasize on this for safety purposes.


Thank you soooooo much worked perfectly like a charm, and there was explanations and some learning done thank you!

---

